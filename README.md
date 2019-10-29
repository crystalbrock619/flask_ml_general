# flask_ml_general

A deployable flask application tailored for production machine learning.  Contains drop-in model loading, logging pre-configured, and other useful features.  This is not meant to be a REST API and includes no data security or auth.  This is meant to be a lightweight deployable API to drop a model in and get connected to a front-end or dashboard quickly with regular, reliable, JSON responses.

## Notes

### Instance Folder

When committed, this repository is set to ignore the instance/ folder.  In that folder should be your config.py file with any sensitive data.  Do not commit config.py with any API keys or database URIs.

### Predefined Routes

The root route path is a landing page for API usage instructions.  Apparently this is a thing and should prbably be built out.

### Logs in the Instance Folder

You really need to manually create the instance folder to get logs in development.  By default, logs are saved to instance/logs/debug.log for safety reasons (don't accidentally want to push sensitive information).  Override the log save path in config.  Note that in heroku, those writes will not persist and you'll need to log to an external service (not currently supported) in production.

## TODO

### Generalize load_file

> Right now, load_file only handled pickled files.  For Keras h5 files, keras.models import load_model needs to be implemented.  For JSON (models can be saved in JSON format as well), the file can be returned as a path (example useage: to keras.models.model_from_json)

### Logging

> Add two-level logging layer for 'debug-full' and 'production' logging.  Add logging at each of the following actions:

* Instantiating all classes

* Loading files

* All checks, transforms, and predictions

### Better Landing Page

> The landing page should have clear instructions as to how the client request should be formed and any subsequent routes they should be aware of.  A nice template would make this update go faster with the renderer already set.


### Add token auth from backend?

> It is likely that backend will be generating user tokens.  As an extension, it might be work considering a kerberos integration for unified authentication to the application server and how that might effect the 'general' architecture.  Though not intended to be implemented here, there may be changes to how things are stored, accessed, that need to be arranged for that level of security in the future. Just a thought.
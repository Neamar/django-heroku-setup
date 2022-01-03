# django-heroku-setup
A minimal Django setup that can be deployed to Heroku directly.

* custom user model (can't be done after the initial migration)
* SCSS support
* static file support with manifest and infinite cache (hashed content)
* config from environment variables (e.g. DATABASE_URL)

## Things to do
Clone this repo, then rename all instances of `app_name` to your project name (including the folder)

You can also change the SECRET_KEY in `app_name/settings.py`.

### Custom user model
User model is in `core/models.py`.

### SCSS
You can use SCSS, see `core/templates/template.html` for the way to load the file, and `core/templates/css/core.scss` for an example.

To reference a static file, use the built-in `static()` function. This way, when running with `DEBUG=False`, a custom forever-cacheable URL will be generated.

### Static files
To run in dev, you simply need to `./manage.py runserver` as usual.

If you're not interested in recompiling the SCSS on every single change, you can set `DEBUG_OFFLINE=True` on your dev environment. Note that you won't be able to change the SCSS, and you'll need to manually run `DESIGN_OFFLINE=True python manage.py compress` on each CSS change.

With `DEBUG=False`, cacheable URLs will be used.

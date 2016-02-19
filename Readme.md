# Heroku Buildpack: Python
![buildpack_python](https://cloud.githubusercontent.com/assets/51578/13116296/5f4058f0-d569-11e5-8129-bffd7be091e6.jpg)

This is the official [Heroku buildpack](http://devcenter.heroku.com/articles/buildpacks) for Python apps, powered by [pip](http://www.pip-installer.org/), and other excellent software.

Recommended web frameworks include Django and Flask. Recommended webserver is Gunicorn. There are no restrictions around what software can be used (as long as it's pip-installable). Web processes must bind to `$PORT`, and only the HTTP protocol is permitted for incoming connections.

Usage
-----

Example usage:

    $ ls
    Procfile  requirements.txt  web.py

    $ heroku create --buildpack git://github.com/heroku/heroku-buildpack-python.git

    $ git push heroku master
    ...
    -----> Python app detected
    -----> Installing python-2.7.11
         $ pip install -r requirements.txt
           Collecting requests (from -r requirements.txt (line 1))
             Downloading requests-2.9.1-py2.py3-none-any.whl (501kB)
           Installing collected packages: requests
           Successfully installed requests-2.9.1
           
    -----> Discovering process types
           Procfile declares types -> (none)

You can also add it to upcoming builds of an existing application:

    $ heroku buildpacks:set heroku/python

A `requirements.txt` file must be found at the root of your application's repository.

Specify a Runtime
-----------------

You can also specify specific versions of the Python runtime with a `runtime.txt` file:

    $ cat runtime.txt
    python-3.5.1

Runtime options include:

- `python-2.7.11`
- `python-3.5.1`
- `pypy-4.0.1` (unsupported, experimental)
- `pypy3-2.4.0` (unsupported, experimental)

Other [unsupported runtimes](https://github.com/heroku/heroku-buildpack-python/tree/master/builds/runtimes) are available as well. Use at your own risk. 

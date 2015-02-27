# MozWall

[![Build Status](https://magnum.travis-ci.com/ariestiyansyah/MozWall.svg?token=hPuxgNQnEXgG9b2mx45v&branch=master)](https://magnum.travis-ci.com/ariestiyansyah/MozWall)

MozWall is a backchannel visualisation solution for the Twitter Search API v1.1 based on Twitter Fontana.

The Twitter API connection backend is written in [Python] & [Flask] and the visualisation frontend is written in [CoffeeScript] and has CSS
animations through Compass & [SASS].

The HTML for the website is generated using [Jade] and styling & layout
is achieved (mostly) through use of Twitter's [Bootstrap 3] framework.
The additional theme's are provided by [Bootswatch].

## Getting started

Alright, so there's some initial preparation and setup to perform to get
the project up and running.

### Software

First of all, your development machine should be equipped with Python 2.6+
and preferably [virtualenv] and [virtualenvwrapper]. This should be no
problem on most Linux distributions, fairly easy on OS X and might be
somewhat challenging on Windows (I have no experience with Python on Windows).

If you want to be able to edit the CoffeeScript, Jade & SASS files
you will also need [nodejs + npm], [Grunt] and [Ruby], [RubyGems] & [Bundler]
to be available.

### Prepare

In order to use the Twitter API v1.1 you will need to create a
"application" at https://dev.twitter.com/.

Also load up a browser tab with http://randomkeygen.com/, we are going to need
a random secret key soon.

### Setup

With that out of the way, you can now "install" the project in a virtualenv:

``` shell
$ mkvirtualenv develop
$ workon develop
$ pip install -r requirements.txt
```

For the frontend requirements also run:

``` shell
$ npm install
$ bundle install
```

Then you'll need to create a config file, let's save it as
`backend/var/conf/mozwall.conf`.

In this file, enter the credentials for the Twitter application you've created
and one of the random "Ft. Knox Passwords":

``` python
TWITTER = {
    'consumer-key': 'xxxwerjewjrelwknelwk320',
    'consumer-secret': 'dbg93geufbfgeoh'
}

SECRET_KEY = '%S#cR3T$(~4re>Awes0me{;?='
```

### Verify

Now everything should be set up and configured. We can confirm this
by trying to sign in with Twitter.

First start the development server:

``` shell
$ python backend/src/app.py backend/var/conf/mozwall.conf
> * Running on http://0.0.0.0:5000/
```

Now go to `http://0.0.0.0:5000/api/twitter/session/new/`.

If everything is working correctly you will be redirected to twitter.com
and asked to "Authorize your application to use your account".

After confirming access you will be redirected back to a page on
the development server with the plain text string "OK".

If you've also installed the frontend requirements you can verify if everything
is in working condition by running grunt. You should see some output like this:

``` shell
$ grunt
> Running "watch" task
> Waiting...
```

## Develop

Cool, you got the initial set up out of the way. Luckily you don't need to
do all of this each time you want to work on MozWall. From now on just
run these commands to get a development server:

``` shell
$ workon develop
$ python backend/src/app.py backend/var/conf/mozwall.conf
> * Running on http://0.0.0.0:5000/
```

And in another terminal window you can keep running Grunt:

``` shell
$ grunt
> Running "watch" task
> Waiting...
```

[Python]: http://www.python.org/
[Flask]: http://flask.pocoo.org/
[virtualenv]: http://www.virtualenv.org/
[virtualenvwrapper]: http://virtualenvwrapper.readthedocs.org/
[CoffeeScript]: http://coffeescript.org/
[Compass]: http://compass-style.org/
[SASS]: http://sass-lang.com/
[Jade]: http://jade-lang.com/
[Bootstrap 3]: http://getboostrap.com/
[Bootswatch]: http://bootswatch.com/
[nodejs + npm]: http://nodejs.org/
[Grunt]: http://gruntjs.com/
[Ruby]: https://www.ruby-lang.org/
[RubyGems]: http://rubygems.org/
[Bundler]: http://bundler.io/
[Twitter Fontana]: http://www.eight.nl/

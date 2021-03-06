# django-base

A project template for Django 1.7.

To use this project follow these steps:

1. Create your working environment
2. Install Django
3. Create the new project using the mysite template
4. Install additional dependencies
5. Use the Django admin to create the project

*note: these instructions show creation of a project called "mysite".  You
should replace this name with the actual name of your project.*

## Working Environment

You have several options in setting up your working environment.  We recommend
using virtualenv to separate the dependencies of your project from your system's
python environment.  If on Linux or Mac OS X, you can also use virtualenvwrapper to help manage multiple virtualenvs across different projects.

### Virtualenv Only

First, make sure you are using virtualenv (http://www.virtualenv.org). Once
that's installed, create your virtualenv::

    $ virtualenv --distribute mysite

You will also need to ensure that the virtualenv has the project directory
added to the path. Adding the project directory will allow `django-admin.py` to
be able to change settings using the `--settings` flag.

### Virtualenv with virtualenvwrapper

In Linux and Mac OSX, you can install virtualenvwrapper (http://virtualenvwrapper.readthedocs.org/en/latest/),
which will take care of managing your virtual environments and adding the
project path to the `site-directory` for you::

    $ mkdir mysite
    $ mkvirtualenv -a mysite mysite-dev
    $ cd mysite && add2virtualenv `pwd`

### Windows

In Windows, or if you're not comfortable using the command line, you will need
to add a `.pth` file to the `site-packages` of your virtualenv. If you have
been following the book's example for the virtualenv directory (pg. 12), then
you will need to add a python pathfile named `_virtualenv_path_extensions.pth`
to the `site-packages`. If you have been following the book, then your
virtualenv folder will be something like::

`~/.virtualenvs/mysite/lib/python2.7/site-directory/`

In the pathfile, you will want to include the following code (from
virtualenvwrapper):

    import sys; sys.__plen = len(sys.path)
    /home/<youruser>/mysite/mysite/
    import sys; new=sys.path[sys.__plen:]; del sys.path[sys.__plen:]; p=getattr(sys,'__egginsert',0); sys.path[p:p]=new; sys.__egginsert = p+len(new)

## Installing Django

To install Django in the new virtual environment, run the following command::

    $ pip install django

## Creating your project

To create a new Django project called '**mysite**' using
django-base, run the following command::

    $ django-admin.py startproject --template=https://github.com/g3rd/django-base/archive/master.zip --extension=py,rst,html mysite_project

## Installation of Dependencies

Depending on where you are installing dependencies:

In development::

    $ pip install -r requirements/local.txt

For production::

    $ pip install -r requirements.txt

*note: We install production requirements this way because many Platforms as a
Services expect a requirements.txt file in the root of projects.*

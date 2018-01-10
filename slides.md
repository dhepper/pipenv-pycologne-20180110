# Dependency Management with pipenv

Daniel Hepper

PyCologne, January 2018

---

# What is Dependency Management?

---

# Package vs. Package

- Package: a collection of Python modules
- Distribution: a bundle of software to be installed
- Library: a package intended to be used by another piece of software
- Project: a bundle of software to be run

#Presenter Notes
    - Package: a directory with a __init__.py file and a bunch of submodules
    - Distribution: intended to be shared, has a setup.py, downloaded from PyPI
    - Library: not useful on its own
    - Project: might be distributed

---
# Dependencies

- Most Python code relies on external dependencies
- Dependencies should be installed automatically
- you want to keep track of the installed versions

---

# Goals of Dependency Management

- compatibility
- reproducability
- maintainability

---

# Different priorities

## Libraries:

  compatibility > maintainability > reprocability

## Projects:

  reproducability > maintainability> compatiblity

.notes: Libraries must define their dependencies in setup.py, setup.py is not sufficient for Projects

---
# Libraries

# setup.py

    !python
    setup(
      ...
      install_requires=[
          'chardet>=3.0.2,<3.1.0',
          'idna>=2.5,<2.7',
          'urllib3>=1.21.1,<1.23',
          'certifi>=2017.4.17'
      ],
    )
---
# Projects

# Virtualenv + requirements.txt

    !bash
    $ virtualenv myproject
    $ source myproject/bin/activate
    (myproject) $ pip install requests
    (myproject) $ pip freeze > requirements.txt
    (myproject) $ cat requirements.txt
    certifi==2017.11.5
    chardet==3.0.4
    idna==2.6
    requests==2.18.4
    urllib3==1.22

---
# Enter pipenv
Aims to bring the best from other language's package handling to Python

- automatically creates virtualenvs
- automatically records installed packages
- distinguishes between normal and dev dependencies
- "Windows is a first-class citizen"
- created by Kenneth Reitz

#Presenter Notes
- hidden complexity (?)
- fast-moving
- less flexible (e.g. only prod & dev)

---

# DEMO

---
# Alternative: pip-tools

- create a requirements.in file(s)
- compile to requirements.txt file(s) with pip-compile
- install with pip-sync

See talk by Chris Arndt:
<https://github.com/SpotlightKid/talk-requirements-revisited>

---
# Thanks

# $ pip install pipenv

<https://pypi.python.org/pypi/pipenv>


# Daniel Hepper

[@danielhepper](https://twitter.com/danielhepper)

<github.com/dhepper>

<consideratecode.com>

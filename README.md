# Thumby Documentation Website

This website holds all of the documentation on the MicroPython API, and the Arduino C/C++ implementation for Thumby along with some helpful examples. 

---

# Building the site locally

Pre-requisites: You will need [Python](https://www.python.org/downloads/) and [pip](https://pip.pypa.io/en/stable/installation/), the Python package manager, installed on your machine.

[Install MkDocs](https://www.mkdocs.org/getting-started/), the wonderful static site generator, along with [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/getting-started/), the nice theme that helps bring dark mode and other fun styles to the website.

Once installed, fork this repository to create your local copy. To run the website locally, navigate a command prompt or terminal to the directory of the project that has the mkdocs.yml file and execute:

```
mkdocs serve
```

If everything is correctly installed, your terminal should print a message like:

```
INFO     -  [13:32:01] Serving on http://127.0.0.1:8000/
```

Open a web browser, like Google Chrome, to the web address [http://127.0.0.1:8000/](http://127.0.0.1:8000/) to see your local changes as you save your edited files. 

To exit the serve mode, select the terminal and press the keys Ctrl+C on Windows or Command+C on Mac to exit the local build.

Once everything looks good on your local build, move on to the next step to contribute your documentation to this repository to help others work on Thumby projects! :sparkling_heart:

---

# Contributing to this project
We love your input! We want to make contributing to this project as easy and transparent as possible, whether it's:

- Reporting a bug, typo, incorrect, or unclear information
- Discussing the current state of the documentation
- Submitting a fix
- Proposing new features
- Becoming a maintainer

## We Develop with GitHub
We use github to host code, to track issues and feature requests, as well as accept pull requests.

## We Use [GitHub Flow](https://docs.github.com/en/get-started/quickstart/github-flow), So All Code Changes Happen Through Pull Requests
Pull requests are the best way to propose changes to the codebase. We actively welcome your pull requests:

1. Fork the repo and create your branch from `main`.
2. If you've added code that should be tested, test it or ask for help!
3. If you've changed API examples, update the documentation.
4. Make sure your code works and that you use spellcheck with any doc changes.
5. Issue that pull request!

## Any contributions you make will be under the Version 3 GNU GENERAL PUBLIC LICENSE 
In short, when you submit changes, your submissions are understood to be under the same [GNU GENERAL PUBLIC LICENSE](https://www.gnu.org/licenses/gpl-3.0.en.html) that covers the project. Feel free to contact the maintainers if that's a concern.

## Report bugs using GitHub's issues
We use GitHub issues to track public bugs. Report a bug by **opening a new issue**; it's that easy!

## Write bug reports with detail, background, and sample code
[This is an example](http://stackoverflow.com/q/12488905/180626) of a bug report. Here's [another example from Craig Hockenberry](http://www.openradar.me/11905408).

**Great Bug Reports** tend to have:

- A quick summary and/or background
- Steps to reproduce
  - Be specific!
  - Give sample code if you can. 
- What you expected would happen
- What actually happens
- Notes (possibly including why you think this might be happening, or stuff you tried that didn't work)

We *love* thorough bug reports!!

# Handbook

This repository contains FLINT Handbook

## Installation

To edit the documentation you need a [GitHub](github.com) account. Once you have created one and logged in, you can edit any page by navigating to the corresponding file and clicking the edit (pen) icon.

This will create a "fork" and further you can create a "pull request", which will be approved by one of the existing members of the Docs team. If you have any development experience, you can setup the docs on your local machine to build the documentation locally.

Here are the steps you can follow while setting up the documentation locally.

1. Fork the repository

If you choose to setup the documentation website locally, you need to have Python and the Python package manager `pip` on your local machine. Follow the official [Python installation](https://www.python.org/downloads/) to setup Python on your local machine.

First make a fork, and then clone the repo:

2. Clone the repository. Replace the `<GITHUB_USERNAME>` with your GitHub username. You can find your username by clicking on your profile picture in the top right corner of the GitHub website.

```sh
git clone https://github.com/<GITHUB_USERNAME>/Handbook
```

Assuming that you have python & pip already installed. Let us set the documentation up:

#### For **Linux** Users:

```sh
virtualenv env
source env/bin/activate
pip install -r requirements.txt
make html
```

#### For **Windows** Users:

```sh
virtualenv env
env\Scripts\activate
pip install -r requirements.txt
make html
```

You can now open the Handbook website on `_build/html/index.html` in your browser. Make corresponding changes on the documentation site and then run `make clean && make html` to update the documentation. You can now create a pull request to get your changes merged into the upstream develop branch.
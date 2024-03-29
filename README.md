# Handbook
## Introduction 
[FLINT Handbook](https://moja-global.github.io/Handbook/) is intended to provide an introduction to FLINT so that its readers, regardless of their knowledge level can understand what FLINT aims to accomplish. The FLINT handbook will go over climate science, the problems it poses to our environment, and the steps we can take to mitigate it's effects.

The Handbook covers:

- Understanding Climate Science and Organizations championing the cause.
- Use of carbon models like the Generic Carbon Budget Model (GCBM).
- Introduction to Full Lands and Integration tools.
- Role of Data Version Control (DVC) in Land Sector Dataset Repos.
- Running a GCBM Silmulation.
- Discussion on Climate Science and Projections.

## Installation

To edit the documentation you need a [GitHub](github.com) account. Once you have created one and logged in, you can edit any page by navigating to the corresponding file and clicking the edit (pen) icon.

This will create a "fork" and further you can create a "pull request", which will be approved by one of the existing members of the Docs team. If you have any development experience, you can setup the docs on your local machine to build the documentation locally.

Here are the steps you can follow while setting up the documentation locally.

1. Fork the repository

If you choose to setup the documentation website locally, you need to have Python and the Python package manager `pip` on your local machine. Follow the official [Python installation](https://www.python.org/downloads/) to setup Python on your local machine.

First make a fork, and then clone the repo

2. Clone the repository 

Replace the `<GITHUB_USERNAME>` with your GitHub username. You can find your username by clicking on your profile picture in the top right corner of the GitHub website.

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

## Project Structure

Please make use of the Project Structure when contributing to this Handbook to save time -

1. To understand the Handbook's blueprint, take a look at the Project Structure.

2. After that, you can browse the [website](https://moja-global.github.io/Handbook/) to see which sections need improvement.

3. Rather than searching linearly through folders, use this Project Structure again to locate the file you want to improve.

4. Submit a pull request after navigating directly to the file you wish to edit.

``` text
  ├── Chapter 1                     # Understanding Climate Science and Carbon Models
       ├── index.rst                # Landing page of Chapter 1
       ├── section_one.rst          # The Organisations behind the Climate Mitigation Steps
       └── section_two.rst          # How does FLINT help solve issues arising from Climate Change
  ├── Chapter 2                     # Chapter 2: Introduction to the Full Lands Integration Tool
       ├── index.rst                # Landing page of Chapter 2
       ├── section_one.rst          # Modules
       ├── section_two.rst          # Inputs 
       └── section_three.rst        # Output
  ├── Chapter 3                     # Introduction to Generic Carbon Budget Model
       ├── index.rst                # Landing page of Chapter 3
       ├── section_one.rst          # End-to-end workflow for the GCBM Analysis
       ├── section_two.rst          # Post-processing
       └── section_three.rst        # What is the effect of running the model without disturbance?
  ├── Chapter 4                     # The Work DVC Plays in the Land Sector Repo
       ├── index.rst                # Landing page of Chapter 4
       └── section_one.rst          # How to create a reproducible pipeline with Moja Global Dataset.
  ├── Chapter 5                     # Running a GCBM Simulation
       ├── index.rst                # Landing page of Chapter 5
       ├── section_one.rst          # Project structure and directory hierarchy overview
       ├── section_two.rst          # Setting up our GCBM environment
           ├── index.rst            # Landing page of Section 2
           ├── section_twoa.rst     # Installing Python
           ├── section_twob.rst     # Installing Microsoft Access Database Driver
           ├── section_twoc.rst     # Installing Visual C++ Redistributable Packages
           └── section_twod.rst     # Update GCBM Run Script
       ├── section_three.rst        # Spatial data preparation(jupyter notebook)
       └── section_four.rst         # Tiler Configuration
  ├── Chapter 6                     # Climate Projections
       ├── index.rst                # Landing page of Chapter 6
       ├── section_one.rst          # How do we expect our world to change?
       ├── section_two.rst          # What does the increase in CO2 mean for forests?
       └── section_three.rst        # Changing Patterns
  ├── Appendices.rst                # Vision: The reproducible science stack
  ├── Conclusion.rst                # Conclusion of the Handbook
  └── index.rst                     # Home page of the Handbook 
```

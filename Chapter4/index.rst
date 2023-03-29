Chapter 4: The Work DVC Plays in the Land Sector Repo 
===========================================================

FLINT requires data to run simulations properly, and this data is available in the `Land Sector Dataset repository <https://github.com/moja-global/Land_Sector_Datasets>`__.

According to :footcite:t:`2023:DVC`, `Data Version Control (DVC) <https://dvc.org/>`__ is a data and Machine
Learning management tool that leverages tools like Git and CI/CD to
track and save data and simulation results models. DVC allows us to
create and switch between different versions of data/models and adopt
engineering tools and best practices for data science projects.

In the past decade, Git has become one of the most used open source
software by developers worldwide. Git tracks changes in the set of files
and coordinates work among programmers. Services like Github use Git for
hosting software development, task management, etc. However, these
services only work best with small files, which is incompatible with
most data science and simulation tasks, as they typically require and
generate large files. DVC allows us to store the location of these large
files in Git so that we can assess them quickly later. DVC is a
beneficial extension to Git as a lightweight tool to help us manage and
version these larger models.

The Land Sector Dataset repository is built using DVC to verify that the
data inputs and the resulting outputs to a simulation are the same -
which is essential when talking about scientific models. DVC can cache
preprocessed data on publicly available remote storage, making sharing
datasets ready for FLINT analysis easier. Learn more here :footcite:t:`2020:DVCorg`. 

.. rubric:: References

.. footbibliography::

.. toctree::
   :hidden:

   section_one
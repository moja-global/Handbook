Installing Python
=================

To set up and run a GCBM simulation, we must install Python 3.7. If we
have Python 3.7 installed already, skip to the `Existing-Python-Installation`_ section.

**New Python Installation** To install Python 3.7, we must
first verify that we have no existing Python 3.7 installation with this
terminal command.

.. code:: bash

       py -V

Next, we change our current directory to the ``python_3_installer``
directory, which is located in this path
``GCBM software and training components\1_Standalone_Template\tools\python_3_installer``.

After changing the current directory, we run the ``install_python``
command to install python.

.. code:: bash

       cd <path to the python_3_installer directory>
       install_python

Running the ``install_pyton`` command will install Python in a default
path of ``C:\Python37``.

**Existing Python Installation** 

.. _existing-python-installation:

If we already have Python 3.7 installed
on our machine, we need to locate the existing Python path.

Next, we change the current directory to the ``python_3_installer``
directory, which is located in this path
``GCBM software and training components\1_Standalone_Template\tools\python_3_installer``.

.. code:: bash


       cd <path to the python_3_installer directory>

In the ``python_3_installer`` directory, we run this terminal command.

.. code:: bash

       install_modules_only <path to the existing Python>
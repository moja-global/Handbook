Project structure and directory hierarchy overview
==================================================

To run a GCBM simulation, we have to complete the following processes:

-  Configure and run the Tiler to convert spatial data into GCBM format
-  Run the Recliner2GCBM tool to create the GCBM input database
-  Run the GCBM configuration script
-  Run GCBM
-  Use post-processing tools to generate the final output

   -  Familiar ecosystem indicators (NPP, etc.) in database format
   -  Convert raw spatial output to final layers

This document discusses these steps in detail to help us run a GCBM
simulation successfully.

**Project Structure** Here is how the Standalone Project directory looks

::

   1_Standalone_Template
   ├── documentation
   ├── gcbm_project
   ├── input_datatbase
   ├── layers
   ├── logs
   ├── processed_output
   ├── tools
   ├── EULA.txt
   ├── readme.txt
   └── run_all.bat

The folders and files in the Standalone Project contain the following
information:

-  **documentation** folder: This folder holds documentation on
   different GCBM tools and processes
-  **gcbm_project:** This folder contains the simulation working
   directory
-  **input_databse:** This folder contains aspatial input data required
   to run the GCBM simulation
-  **layers:** This folder contains spatial layers or data needed to run
   the GCBM simulation
-  **logs:** This folder includes pre and post-processing tools and
   simulation log files
-  **processed_output:** This folder contains the fully-processed
   outputs. \***\*
-  **tools:** This folder includes the pre and post-processing tools,
   the GCBM and the supporting \****software to run the GCBM simulation
-  ``EULA.txt``: This file contains the agreement for using the GCBM
   simulation
-  ``readme.txt``: This file contains the GCBM setup information
-  ``run_all.bat``: This file runs the project from start to finish ##
   Prerequisites

To follow through with this documentation, we must have the following:

-  A command line interface, for Windows users, it is important we use
   the command prompt to run the terminal commands
-  Code editors like `Notepad
   ++ <https://notepad-plus-plus.org/downloads/>`__ and `Visual Studio
   Code <https://code.visualstudio.com/download>`__ ## GCBM Installation
   Guide

This section will discuss setting up an environment to run a GCBM
simulation.
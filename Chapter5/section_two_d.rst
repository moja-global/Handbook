Update GCBM Run Script
----------------------

After installing the required packages, we update our ``run_all.bat``
file to point to these packages. We open up the ``run_all.bat`` file in
any code editor of our choice.

Next, we edit the ``GCBM_PYTHON`` variable to point to the Python path
we used in our Python Installation step. After updating the
``GCBM_PYTHON`` variable, we update the ``PLATFORM`` variable to reflect
the version of the Microsoft Access Database Driver we have installed.

.. code:: bat

       REM Set Python path - change this to your Python installation directory.
       set GCBM_PYTHON=C:\Python37
       
       REM Is your version of MS Access 32 (x86) or 64 (x64) bit?
       set PLATFORM=x64
       REM **************************************************************************

To verify that we have successfully installed all the packages, we run
the run_all.bat file by clicking it.
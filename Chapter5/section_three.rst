Spatial data preparation(jupyter notebook)
------------------------------------------

As discussed earlier in this documentation, the GCBM simulation requires
spatial and aspatial or tabular data to run. This section will discuss
creating a sample GCBM project and adding these required data.

We create a sample GCBM project by making a copy of the
``1_Standalone_Template`` folder and renaming the copy to
``Sample_Data_Exercise``.

|image1| |image2|

Next, we delete all the folders in the
``Sample_Data_Exercise\layers\raw`` directory.

|image3| |image4|

We then add spatial data to our project by copying the contents in the
``Sample_Data\Spatial`` directory into the
``Sample_Data_Exercise\layers\raw`` directory.

|image5| |image6|

Next, we add aspatial data to our project by copying the
``Sample_Data\Aspatial\yield_curves.csv`` file into the
``Sample_Data_Exercise\input_database`` directory.

|image7| |image8|

Then, we delete the old ``yield.csv`` file in the
``Sample_Data_Exercise\input_database`` directory. We have added the
sample data required to run a GCBM simulation to our project. We can
explore the data in the ``yield_curves.csv`` and ``inv_sample.shp``
files. The yield curve data have one classifier, which is LdSpp. We link
spatial inventory to yield curves with classifiers.

.. image:: https://paper-attachments.dropboxusercontent.com/s_C62E98ACCB4207E09399EF70CCC5A9D6995D66B82064646EB958DB6F9AC550B3_1665224279129_Screenshot+698.png

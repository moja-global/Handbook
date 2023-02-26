Tiler Configuration
-------------------

The spatial layers need to be converted to a data format that the GCBM
can use to run a simulation, and this conversion is done by the tiler.
The tiler scripts use a mojadata python package to convert spatial data
to the FLINT format.

In our project, the tiler script can be located in this path
``GCBM software and training components\Sample_Data_Exercise\tools\Tiler\tiler.py``.

To configure the tiler, we open the tiler script in any code editor of
our choice.

.. image:: https://paper-attachments.dropboxusercontent.com/s_C62E98ACCB4207E09399EF70CCC5A9D6995D66B82064646EB958DB6F9AC550B3_1665224317518_Screenshot+643.png

**Update the bounding box** Next, we update the bounding box. The
bounding box defines the study area of the plant simulation, and other
spatial layers are cropped and reprojected to the area specified in the
bounding box.

.. image:: https://paper-attachments.dropboxusercontent.com/s_C62E98ACCB4207E09399EF70CCC5A9D6995D66B82064646EB958DB6F9AC550B3_1665224544784_Screenshot+643.png

The bounding box in the code block above receives three parameters:

-  A path that points to the inventory shape layer, in this case,
   ``inventory.shp``
-  An Attribute parameter, in this case, ``PolyID``. This attribute is a
   chosen file that defines a simulation area that represents all of the
   polygons in the landscape
-  The ``pixel_size`` parameter defines the resolution at which the
   simulation should run

Replace the bounding box with the code block below.

.. code:: python

       bbox = BoundingBox(
           VectorLayer(
               "bbox",
               os.path.join(layer_root, "inventory", "inv_sample.shp"),
               Attribute("Age")),
           pixel_size=0.01)
       
       tiler = GdalTiler2D(bbox, use_bounding_box_resolution=True)

**Configure the Classifier layers** After updating the bounding box, we
configure the classifier layers. The classifier layers link spatial data
to the yield table.

The classifier layers are shown in the image below.

.. image:: https://paper-attachments.dropboxusercontent.com/s_C62E98ACCB4207E09399EF70CCC5A9D6995D66B82064646EB958DB6F9AC550B3_1665225428527_Screenshot+647.png

Replace the classifier layers with this code block below.

.. code:: python

       classifier_layers = [
                   VectorLayer("LdSpp", os.path.join(layer_root, "inventory", "inv_sample.shp"), Attribute("LdSpp"), tags=[classifier_tag]),
               ]

.. image:: https://paper-attachments.dropboxusercontent.com/s_C62E98ACCB4207E09399EF70CCC5A9D6995D66B82064646EB958DB6F9AC550B3_1665225608392_Screenshot+648.png

In the images above, we do the following:

-  Delete one classifier layer
-  Change the name of the first classifier layer from ``Classifier1`` to
   ``LdSpp``. We must keep this classifier name consistent, as we will
   use it to generate an input database later in this tutorial
-  Change the path to the inventory shape layer

**Configure the age layer** Next, we update the age layer. We can see
the age layer in the image below.

.. image:: https://paper-attachments.dropboxusercontent.com/s_C62E98ACCB4207E09399EF70CCC5A9D6995D66B82064646EB958DB6F9AC550B3_1665225774781_Screenshot+649.png

We replace the age layer with this piece of code.

.. code:: python

       # Age - layer name must be "initial_age" so that the script can update the GCBM configuration file.
               VectorLayer("initial_age", os.path.join(layer_root, "inventory", "inv_sample.shp"), Attribute("Age"),
                           data_type=gdal.GDT_Int16, raw=True), 

.. image:: https://paper-attachments.dropboxusercontent.com/s_C62E98ACCB4207E09399EF70CCC5A9D6995D66B82064646EB958DB6F9AC550B3_1665225881112_Screenshot+650.png

**Configure the mean annual temperature** Next, we configure the mean
annual temperature vector layer.

.. image:: https://paper-attachments.dropboxusercontent.com/s_C62E98ACCB4207E09399EF70CCC5A9D6995D66B82064646EB958DB6F9AC550B3_1665226000048_Screenshot+650-1.png

The vector layer is replaced by this raster layer.

.. code:: python

       RasterLayer(os.path.join(layer_root, "environment", "NAmerica_MAT_1971_2000.tif"), 
             name= "mean_annual_temperature"),

.. image:: https://paper-attachments.dropboxusercontent.com/s_C62E98ACCB4207E09399EF70CCC5A9D6995D66B82064646EB958DB6F9AC550B3_1665226446760_Screenshot+699.png

We use the ``NAmerica_MAT_1971_2000.tif``\ raster mean annual
temperature layer in the code block above. The
``NAmerica_MAT_1971_2000.tif`` layer is in the
``layers\raw\Environment\NAmerica_MAT_1971_2000.tif`` directory.

**Disturbance events** Disturbances significantly change the forest
dynamic; however, the initial test run will be without any disturbances.
To simulate without disturbances, delete the disturbance layer.

.. image:: https://paper-attachments.dropboxusercontent.com/s_C62E98ACCB4207E09399EF70CCC5A9D6995D66B82064646EB958DB6F9AC550B3_1665226082096_Screenshot+651.png

After we are done with this section, here is how our ``tiler.py`` file
looks

**Clean up Tiler script whitespace** After configuring our tiler
scripts, we clean up tabs and spaces using the Notepad++ editor. We
clean up these spaces because Python is sensitive to whitespace and can
throw an error.

.. image:: https://paper-attachments.dropboxusercontent.com/s_C62E98ACCB4207E09399EF70CCC5A9D6995D66B82064646EB958DB6F9AC550B3_1665226169556_Screenshot+656.png

**Run the Tiler** After cleaning up the tiler script, we run the
``process_spatial_layers.bat`` file. This ``process_spatial_layers.bat``
is in the ``Sample_Data_Exercise\layers`` directory.

|image9| |image10|

When the tiler script is done, the ``Sample_Data_Exercise\layers\tiled``
directory should contain these files.

-  A ``.tiff`` file of the final cropped and reprojected version of each
   layer
-  A JSON file for each ``.tiff`` file containing metadata and attribute
   table, if applicable
-  A ``study_area.json`` file containing metadata about the tiled layers

.. image:: https://paper-attachments.dropboxusercontent.com/s_C62E98ACCB4207E09399EF70CCC5A9D6995D66B82064646EB958DB6F9AC550B3_1665226551658_Screenshot+659.png

Tabular data preparation(jupyter notebook)
------------------------------------------

Things to add:

-  info about the Chapman-Richards growth function
-  how **curve_fit** function from **scipy** works
-  note on trying different initial guesses for parameters(can explain
   during the next call)
-  mention the importance of data visualization, European Beech is an
   example
-  note about species: Have to check if related species are in
   \**documentation:raw-latex:`\species`\_names.csv**. ## Input database
   generation(Recliner2GCBM)

Next, we need to generate the project input database. To create the
input database, we need the following:

-  A CBM3 ArchiveIndex Database (AIDB). The ArchiveIndex Database is a
   database that contains non-spatial and spatially referenced
   parameters. These parameters include but are not limited to decay
   rates, disturbance matrices, root biomass coefficients etc.
-  A yield table in ``.csv`` or ``.xls``/``.xlsx`` format

**Configure Project** To start building the input database, we run the
``input_database\run_recliner2gcbm_gui.bat`` file. Running the
``run_recliner2gcbm_gui.bat`` file opens a **Configure Project** window.

.. image:: https://paper-attachments.dropboxusercontent.com/s_C62E98ACCB4207E09399EF70CCC5A9D6995D66B82064646EB958DB6F9AC550B3_1665226592289_Screenshot+662.png

To configure a project, we do the following:

-  Populate the **AIDB Path** input field with a link to the
   ``ArchiveIndex_Beta_Install.mdb`` file. The
   ``ArchiveIndex_Beta_Install.mdb`` file is located in the
   ``input_database`` directory
-  Add a link to the ``gcbm_input.db`` file in the **Path** input field.
   The ``gcbm_input.db`` file is located in the ``input_database``
   directory. The ``gcbm_input.db`` is the database that will be
   generated at the end of the process.
-  Click **yes**, when the prompt asks you to replace the existing
   version of the file |image11|

**Add Classifier** After configuring our project, we add our classifiers
layers.

.. image:: https://paper-attachments.dropboxusercontent.com/s_C62E98ACCB4207E09399EF70CCC5A9D6995D66B82064646EB958DB6F9AC550B3_1665226691110_Screenshot+667.png

Clicking on the **Add** button opens up a window.

.. image:: https://paper-attachments.dropboxusercontent.com/s_C62E98ACCB4207E09399EF70CCC5A9D6995D66B82064646EB958DB6F9AC550B3_1665226739716_Screenshot+668.png

The window prompts us to do the following:

-  Input the ``LdSpp`` classifier name. The classifier name must be the
   same in our ``tiler.py`` file
-  Link to the ``yield_curves.csv`` path in the **Path** input field.
   The ``yield_curves.csv`` file is in the ``input_database`` directory
-  Click the Column select button and click the **A** column. Clicking
   the **A column** specifies which column has the ``LdSpp`` classifier
   values |image12|

Click the **Ok** button.

.. image:: https://paper-attachments.dropboxusercontent.com/s_C62E98ACCB4207E09399EF70CCC5A9D6995D66B82064646EB958DB6F9AC550B3_1665226937771_Screenshot+675.png

After adding our classifier layers, we click the **Next** button.

**Configure Growth Curves** After configuring the classifiers, the next
step is configuring the yield curves. In this step, we add a set of age
and volume data to describe the tree growth.

To configure the growth curves, we do the following:

-  Add the path to the ``yield_curves.csv`` file in the **File** input
   field. This ``yield_curves.csv`` file contains the yield curve data
   for the classifier we just setup
-  Click on the ``LdSpp`` Classifier Column **Select** button and click
   a row in column **A.** Clicking a row in column **A** specifies what
   column the ``LdSpp`` classifier maps to
-  Change the **Growth curve interval** to 10, and click the **Age10**
   data header. The **Growth curve interval** is the number of years
   between volume increments for all the curves in the
   ``yield_curves.csv`` file
-  Identify which columns represent the species, forest type or the
   archive index tree species column. Click the **Species** select
   button and click column **B.** Clicking column **B c**\ hanges the
   **Species** input field to 1
-  Identify what columns represent the start and the end of the volume
   increments. To specify the start column, we click on the first
   **Increments “…”** button and click anywhere in the **C** column. To
   specify the end column, we click the second **Increments** “**…**”
   button and click anywhere in the last increment column to the right.
   Mapping these columns will give the **Increments** input field a
   value of 2 and 32, respectively
-  Click the **Next** button to continue

.. image:: https://paper-attachments.dropboxusercontent.com/s_C62E98ACCB4207E09399EF70CCC5A9D6995D66B82064646EB958DB6F9AC550B3_1665227021699_Screenshot+679.png

**Optional data** After configuring the growth curves, we see the
**transition rules screen.** Transition rules \****describe what happens
after specific stand types are disturbed by specific disturbance events.
This documentation will not cover transition rules as they are optional.
Click on the **Next** button to continue.

After the T\ **ransition Rules screen,** the \****following screen
\****is the **Configure Disturbance Categories screen.** The **Configure
Disturbance Categories screen** is an optional advanced GCBM module
component that will not be covered in this documentation\ **.** Click on
the **Next** button to continue\ **.**

|image13| |image14|

**Save Recliner2GCBM configuration** After configuring the data to
create an input database, we need to save it. In this section, we do the
following:

-  Check the previous steps for errors

-  Save the data in the ``input_database`` directory using the **Save
   configuration** button. By default, the data is saved in a
   ``recliner2gcbm_config.json`` file |image15| |image16|

-  Click the **Load** button to generate the input database, wait for a
   few minutes and then click **Done** |image17| |image18|

**Configure start/end date** Next, we configure the simulation start and
end date in the ``run_all.bat`` file. We open the ``run_all.bat`` file
in a text editor of our choice. Next, we change the
``SIMULATION_START_YEAR`` variable to 1990 and the
``SIMULATION_END_YEAR`` variable to 2000.

.. code:: bat

       set SIMULATION_START_YEAR= 1990
       set SIMULATION_END_YEAR= 2000

.. image:: https://paper-attachments.dropboxusercontent.com/s_C62E98ACCB4207E09399EF70CCC5A9D6995D66B82064646EB958DB6F9AC550B3_1665228309396_Screenshot+687.png

GCBM run and result visualization
---------------------------------

After configuring the GCBM, we run the simulation by clicking on the
``run_all.bat`` file. We see the processed output in the
``processed_output`` folder.

.. image:: https://paper-attachments.dropboxusercontent.com/s_C62E98ACCB4207E09399EF70CCC5A9D6995D66B82064646EB958DB6F9AC550B3_1665331076441_Screenshot+702.png

.. |image1| image:: https://paper-attachments.dropboxusercontent.com/s_C62E98ACCB4207E09399EF70CCC5A9D6995D66B82064646EB958DB6F9AC550B3_1665224097997_Screenshot+696.png
.. |image2| image:: https://paper-attachments.dropboxusercontent.com/s_C62E98ACCB4207E09399EF70CCC5A9D6995D66B82064646EB958DB6F9AC550B3_1665224098027_Screenshot+697.png
.. |image3| image:: https://paper-attachments.dropboxusercontent.com/s_C62E98ACCB4207E09399EF70CCC5A9D6995D66B82064646EB958DB6F9AC550B3_1665224137466_Screenshot+633.png
.. |image4| image:: https://paper-attachments.dropboxusercontent.com/s_C62E98ACCB4207E09399EF70CCC5A9D6995D66B82064646EB958DB6F9AC550B3_1665224137494_Screenshot+634.png
.. |image5| image:: https://paper-attachments.dropboxusercontent.com/s_C62E98ACCB4207E09399EF70CCC5A9D6995D66B82064646EB958DB6F9AC550B3_1665224181546_Screenshot+636.png
.. |image6| image:: https://paper-attachments.dropboxusercontent.com/s_C62E98ACCB4207E09399EF70CCC5A9D6995D66B82064646EB958DB6F9AC550B3_1665224181571_Screenshot+637.png
.. |image7| image:: https://paper-attachments.dropboxusercontent.com/s_C62E98ACCB4207E09399EF70CCC5A9D6995D66B82064646EB958DB6F9AC550B3_1665224221812_Screenshot+639.png
.. |image8| image:: https://paper-attachments.dropboxusercontent.com/s_C62E98ACCB4207E09399EF70CCC5A9D6995D66B82064646EB958DB6F9AC550B3_1665224221845_Screenshot+640.png
.. |image9| image:: https://paper-attachments.dropboxusercontent.com/s_C62E98ACCB4207E09399EF70CCC5A9D6995D66B82064646EB958DB6F9AC550B3_1665226514578_Screenshot+657.png
.. |image10| image:: https://paper-attachments.dropboxusercontent.com/s_C62E98ACCB4207E09399EF70CCC5A9D6995D66B82064646EB958DB6F9AC550B3_1665226514597_Screenshot+658.png
.. |image11| image:: https://paper-attachments.dropboxusercontent.com/s_C62E98ACCB4207E09399EF70CCC5A9D6995D66B82064646EB958DB6F9AC550B3_1665226645335_Screenshot+666.png
.. |image12| image:: https://paper-attachments.dropboxusercontent.com/s_C62E98ACCB4207E09399EF70CCC5A9D6995D66B82064646EB958DB6F9AC550B3_1665226767050_Screenshot+669.png
.. |image13| image:: https://paper-attachments.dropboxusercontent.com/s_C62E98ACCB4207E09399EF70CCC5A9D6995D66B82064646EB958DB6F9AC550B3_1665227053085_Screenshot+680.png
.. |image14| image:: https://paper-attachments.dropboxusercontent.com/s_C62E98ACCB4207E09399EF70CCC5A9D6995D66B82064646EB958DB6F9AC550B3_1665227053051_Screenshot+681.png
.. |image15| image:: https://paper-attachments.dropboxusercontent.com/s_C62E98ACCB4207E09399EF70CCC5A9D6995D66B82064646EB958DB6F9AC550B3_1665227099306_Screenshot+682.png
.. |image16| image:: https://paper-attachments.dropboxusercontent.com/s_C62E98ACCB4207E09399EF70CCC5A9D6995D66B82064646EB958DB6F9AC550B3_1665227099331_Screenshot+683.png
.. |image17| image:: https://paper-attachments.dropboxusercontent.com/s_C62E98ACCB4207E09399EF70CCC5A9D6995D66B82064646EB958DB6F9AC550B3_1665227252988_Screenshot+685.png
.. |image18| image:: https://paper-attachments.dropboxusercontent.com/s_C62E98ACCB4207E09399EF70CCC5A9D6995D66B82064646EB958DB6F9AC550B3_1665227252937_Screenshot+686.png

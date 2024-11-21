How to create a reproducible pipeline with Moja Global Dataset.
===============================================================

To add datasets to the Land sector
`repository <https://github.com/moja-global/Land_Sector_Datasets>`__, we
start by cloning this repository. Check out `this
article <https://docs.github.com/en/repositories/creating-and-managing-repositories/cloning-a-repository>`__
to understand how to clone a repository on GitHub. Learn more :footcite:t:`2020:VCS`.

Next, we go through the library and find the raw dataset that we want to
process, in this case, the ``HarmonizedWorldSoilDatabase`` dataset. It
is important to note that the ``HarmonizedWorldSoilDatabase`` is a test
dataset. Each dataset will have specific transformation steps to prepare
analysis, but each step can be run using our DVC pipelines. Each
pipeline will follow the broad steps of download, extract and transform,
then save the results on the remote storage.

In the ``Land_Sector_Datasets`` repository we just cloned, navigate to
the ``bilToTif.py`` file, which is nested in the ``Data/Soil``
directory.

This ``Data/Soil/bilToTif.py`` file contains a ``BILtoTIF`` function
that takes the raw ``HarmonizedWorldSoilDatabase`` dataset as a
parameter and then converts the dataset from a ``.bil`` file to a
``.tif`` file. The ``BILtoTIF`` function then saves the ``.tif`` file.

.. code:: py

      def BILtoTIF(inBilPath,outTifPath):
          inBil = gdal.Open(inBilPath)
          driver = gdal.GetDriverByName('GTiff')
          outTif = driver.CreateCopy(outTifPath, inBil, 0)
    
          inBil = None
          outTif = None

Next, in the ``Data/Soil/bilToTif.py`` file, we have a
``restructureTIF`` function that restructures the ``.tif`` dataset using
the options specified in the ``restructureTIF``.

.. code:: py

      def restructureTIF(in_tif, out_tif):
            options = gdal.WarpOptions(
                creationOptions=["COMPRESS=DEFLATE","PREDICTOR=2","ZLEVEL=9"],
                dstSRS="EPSG:4326",
                format="GTiff",
                multithread=True,
                xRes=0.005, yRes=0.005,
                resampleAlg="near",
             )
         gdal.Warp(destNameOrDestDS=out_tif, srcDSOrSrcDSTab=in_tif, options=options)
   if __name__ == "__main__":
      in_src = os.path.join("HWSD_RASTER","hwsd.bil")
      out_src = os.path.join("HWSD_VECTOR","HarmonizedWorldSoilDatabase_RAW.tif")
      BILtoTIF(in_src,out_src)
      if os.path.isfile(out_src):
          restructuredTifPath = os.path.join("HWSD_VECTOR","HarmonizedWorldSoilDatabase_RESTRUCTURED.tif")
          restructureTIF(in_tif=out_src, out_tif=restructuredTifPath)

We can see the different options specified in the code block above.

The project’s root directory has a ``dvc.yaml`` file. This ``dvc.yaml``
file contains an established DVC pipeline.

.. code:: py


    vars:
       - python: C:\Develop\anaconda\envs\gdal\python.exe
       stages:
           HarmonizedWorldSoilDatabase:
               cmd: python bilToTif.py
               wdir: Data/Soil
               deps:
               - HWSD_RASTER\hwsd.bil
               - bilToTif.py
               outs:
               - HWSD_VECTOR\HarmonizedWorldSoilDatabase_RAW.tif
               - HWSD_VECTOR\HarmonizedWorldSoilDatabase_RESTRUCTURED.tif


The DVC pipeline does the following: 
* Runs the ``bilToTif`` script 
* Pushes the processed data to a remote storage

In the root directory, there is a ``.github`` folder that contains a
``workflows`` folder. This ``.github/workflows`` directory contains a
``health-check.yaml`` file.

The ``github/workflows/health-check.yaml`` file holds the GitHub Actions
responsible for recreating this DVC pipeline.

.. code:: py


   name: dvc-report
   on: [push]
   jobs:
     run:
       runs-on: [ubuntu-latest]
       steps:
         - uses: actions/checkout@v2
         - uses: actions/setup-python@v2
           with:
             python-version: '3.x'
         - uses: iterative/setup-dvc@v1
         - uses: iterative/setup-cml@v1
         - name: add dvc
           env:
             repo_token: ${{ secrets.GITHUB_TOKEN }}
           run: |
             echo "# DVC REPORT" > report.md
             echo "## Files and Directories currently tracked" >> report.md
             dvc list -R --dvc-only . >> report.md
             cml-send-comment report.md 



It is important to note that GitHub Actions only runs when there is a
change in the python script, producing a different data output.

.. rubric:: References

.. footbibliography::
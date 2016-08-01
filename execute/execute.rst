.. index::
	single: Running the tool

****************
Running the tool
****************

As discussed in the :doc:`Setting up the tool <../setup/setup>` section, the Data Extractor tool is operated from a MapInfo Workspace file within which the data required to run the tool is already loaded. It also relies on an SQL database containing the boundaries of the relevant partners, and a configuration document for setting up the tool. Therefore, before running the tool, ensure the following conditions are met:

- A MapInfo document has been created which contains both the partner boundary layer and any MapInfo data layers that may be included in the extraction. 
- An SQL database exists that contains the relevant partner boundaries, any data tables required, and auxiliary tables and stored procedures as set out in the setup section, in the correct tables and formats. 
- The file dsn for the SQL database has been created.
- The XML configuration document has been set up correctly, both for general settings and for each individual layer that will be queried. It is named correctly.
- The Data Extractor tool has been installed and set up, and is loaded into the workspace using the MapInfo Tool Manager.

Please refer to the :doc:`setup <../setup/setup>` section for further information about any of these requirements.

.. index::
	single: Opening the form

Opening the form
----------------

To open the Data Searches tool, open the tool in the Tools menu (**Tools... -> Data Extractor**), as shown in :numref:`figRunExtractor`. 


.. _figRunExtractor:

.. figure:: figures/RunExtractor.png
	:align: center

	Launching the Data Extractor tool (ArcGIS).


If there are any structural issues with the XML document, the tool will display a message that it has encountered an error, and not load any further. If any of the map layers that are listed in the configuration document are not present, a warning will be shown (:numref:`figLaunchWarning`). The layers that are missing will not be loaded into the form and so cannot be included in the analysis. Provided that the XML document is otherwise correct, the form will display (:numref:`figDisplayForm`).


.. _figLaunchWarning:

.. figure:: figures/LaunchWarning.png
	:align: center

	A warning is displayed for any data layers not loaded in the GIS project.

.. _figDisplayform:

.. figure:: figures/DisplayForm.png
	:align: center

	The form is displayed with the active partners and available data layers shown.

Select the partners for which you wish to run the extraction, and the tables that you would like to include, what type of extraction you would like to carry out (spatial, survey tags, or both), make sure all other options are correct then press **OK**. The tool can run for a considerable amount of time dependent on the number of records that are being selected. Progress is shown in a progress window (:numref:`figProgress`).

.. _figSelectOptions:

.. figure:: figures/SelectOptions.png
	:align: center

	Select the required options on the form.


.. _figProgress:

.. figure:: figures/ExtractorProcessing.png
	:align:center

	Progress is shown in the progress window.

When the tool finishes, it asks the user whether to close the form or keep it open for subsequent use (:numref:`figFinished`). Once the user makes a choice the log file is sown (:numref:`figLogFile`)

.. _figFinished:

.. figure:: figures/ProcessComplete.png
	:align: center

	Once the process finishes a message box is shown.

.. _figLogFile:

.. figure:: figures/LogFile.png
	:align: center

	The log file is shown for review.

.. index::
	single: Extraction results


Extraction Results
------------------

All results are held in the `DefaultPath <../setup/setup.html#defaultpath>`__ folder as specified in the XML configuration document. As shown in :numref:`figResults` each partner has its own subfolder where the partner results are stored in the formats requested. A log file folder contains the process logs.

.. figure:: figures/OutputFolderAnnotated.png
	:align: center

	Output is organised in partner specific folders.

Now you can repeat the analysis as required. 



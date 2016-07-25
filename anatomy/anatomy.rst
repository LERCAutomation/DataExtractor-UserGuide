**************************
Anatomy of data extraction
**************************

.. index::
	single: Detailed process description

This section describes how a typical data extraction might be carried out manually, and how the Data Extraction Tool automates this process. Please note that the examples used in this illustration are purely fictional and do not represent a real-world scenario. 

Detailed process description
============================

The process of a typical data extraction can be broken down into a number of distinct steps that are described here. In the next section the way that the Data Extraction Tool carries out these steps is explained.

**Defining a search boundary**

Before any extraction can be carried out, the polygon describing the area for which data will be extracted has to be entered into the GIS system. Typically this would be held in a single data layer, with some associated attributes such as the name of the organisation represented by the boundary. Once this area has been entered into the data layer, it can be used time and again.

**Selecting the relevant data layers**

Using the boundary defined and/or selected in the previous step, each of the data layers describing the presence of protected sites and/or species is selected one by one.

**Exporting the results**

The selected features are exported in the format required by the user, including only the relevant columns from the dataset. Symbology may be defined by hand before the data is ready to be sent out. 

**Repeating the process**

Where there is more than one partner for which data needs to be extracted, the process will be repeated for each partner boundary.

.. index::
	single: Tool overview

The Data Extractor Tool
======================

There are four parts to the Data Extractor Tool that work together to automate the process described above:

1. A GIS layer that describes the boundaries of all relevant partners and stakeholders. 
#. Spatial data held in an SQL database, and / or in spatial data layers within the GIS system.
#. An XML file that specifies how the extractions are set up and what data should be exported for each data layer
#. The Data Extractor Tool interface.

The Data Extractor Tool is used within a GIS environment and requires all the required data layers to be preloaded in the GIS (see :numref:`figMapInfoUI`). 

.. _figMapInfoUI:

.. figure:: figures/InterfacMapInfoAnnotated.png
	:align: center

	The MapInfo user interface configured for using the Data Extractor Tool

Tool workflow
-------------

The Data Extractor Tool requires minimum user input in order to carry out its processes once it is configured. The simple workflow is as follows (see :numref:`figUIAnn`):

1. The user selects for which partner(s) the extraction should be carried out.
#. The user specifies which data layers to search. Only layers that are loaded in the GIS or are available in the SQL database are made available at this point. 
#. The users selects whether the extracted files should be added to a zip file, whether confidential data should be included, and whetherthe log file should be cleared before the process starts.
#. Finally, the user selects whether the selection of data should be based on spatial location only, survey tags (names) only, or both. This allows for the inclusion of data relevant to a stakeholder that is outside of a stakeholder's boundary.
#. Once the user clicks 'OK' the process starts.


.. _figUIAnn:

.. figure:: figures/MenuExampleAnnotated.png
	:align: center

	The Data Extractor Tool menu workflow


In essence, the process that the tool follows is identical to the manual extraction described above. 

1. The boundary of each partner is processed in sequence. 
#. The selected SQL and GIS data layer are selected using the boundary (and/or the survey tags for this partner).
#. The resulting selections are exported to the output folder as specified in the configuration file, using the columns and symbology specified in this configuration file.
#. GIS data is added to the map as detailed by the user. Layers are symbolised as specified in the configuration file, and labels are added if requested. [Haven't run the tool yet so don't know if it does this - assume not]
#. During the process the tool reports its progress to a log file and when the process finishes this log file is displayed, allowing the user to assess the success of the data extraction. The log file is kept with the other output in the output directory.


.. index::
	single: Tool Outputs

Tool Outputs
============

Below is a selection of outputs generated from the example data search given in figures :numref:`figArcGISUI` and :numref:`figUIAnn`. These examples were generated using the ArcGIS tool, and the GIS output from the MapInfo tool has a slightly different format. The tabular data, however, is the same for both implementations of the tool [Andy you might want to include the visuals from the MapInfo implementation].

When the process finishes, the GIS output is presented within the GIS interface (:numref:`figArcOutputAnn`). Note the output layers are presented in a logical format and their names refer back to the search reference number. The symbology of the layers is customised, as is the labelling applied to each output layer. The buffer that was used for the analysis is also included in the output. Only layers for which a feature was found within the search radius will be included in the output.

.. _figArcOutputAnn:

.. figure:: figures/ExampleOutputArcGISAnnotated.png
	:align: center

	GIS output from the Data Searches Tool (ArcGIS implementation)

The GIS output is stored, together with all other outputs from the tool, in a user defined folder (:numref:`figOutputFolder`). These outputs may include a combination of GIS layers, the buffer layer that was used, tabular layers in different formats, a combined sites table, and the log file.  

.. _figOutputFolder:

.. figure:: figures/OutputFolderAnnotated.png
	:align: center

	Data Searches Tool output folder

Tabular output is produced in a text based format and can include the distance of each feature to the search feature (:numref:`figTabularOutput`). It is possible to create summary statistics for any column during the process, which will be included in the tabular output.


.. _figTabularOutput:

.. figure:: figures/ExampleTabularOutput.png
	:align: center

	Example of tabular output from the Data Searches Tool

The combined sites table (see :numref:`figCombinedSites`) contains a summary of the sites that are found. Again, this output is highly customisable and it is easy to exclude or include layers in this table as required. Any summary statistics can be included.

.. _figCombinedSites:

.. figure:: figures/CombinedSitesTableExample.png
	:align: center

	Example of a combined sites table

Finally, the log file details each step that was taken during the process, and gives some feedback about the outcomes of the steps. This includes reporting on the input for the search, the number of features that were selected in each data layer, and which data layers did not return any features (see :numref:`figLogFileExample`).

.. _figLogFileExample:

.. figure:: figures/LogFileExample.png
	:align: center

	Example of a Data Searches Tool log file


The following chapters, :doc:`setting up the tool <../setup/setup>` and :doc:`running the tool <../execute/execute>`, will guide you through setting up and operating the tool in such a way that these tool outputs meet the exact requirements of data searches within your organisation.
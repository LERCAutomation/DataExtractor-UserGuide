************
Introduction
************

.. index::
	single: Background

Background
==========

Carrying out data extractions (i.e. extracting records for partners on, for example, species or local nature reserves) is a routine task for many Local Environmental Record Centres (LERCs). The process is a repetitive one, with the same kind of extraction being carried out for what can be a considerable number of partners. Mostly, the only difference between partners is the geographical area they focus on, while the data they require can be represented by a few standard tables. Therefore this is a process that is ideally suited to being automated.

The Data Extractor tool was originally developed for Greenspace Information for Greater London (GiGL) and implemented in MapInfo. Currently the tool is used by a variety of LERCs and a version for ArcGIS is under consideration.

.. raw:: latex

   \newpage

.. index::
	single: Tool overview

Tool overview
=============

The Data Extractor tool is configurable in a flexible way according to the requirements of the LERC or individual user through a configuration document. It is integrated into the user interface of the GIS system and presented there as menu item. The tool itself has a simple interface (:numref:`figUI`), requiring a minimum of input (the user is requested to select which partners an extract will be created for, and from which tables). There are some additional options to tailor the extracts to include confidential records, and some simple output options. Once set up, the tool communicates with both the GIS system and an associated SQL database to extract the required data.

.. _figUI:

.. figure:: figures/UserInterface.png
	:align: center

	The Data Extractor tool interface

Data layers for the tool can be contained in an SQL Server database or as GIS layers loaded in the GIS application. When running an extraction the tool uses a GIS layer, which is also present in the associated SQL database, to find the boundary for each partner and extract the records which fall within this boundary. The attributes for each partner in this GIS layer define which of the available data layers will be extracted and in which format. Extracts are saved in a predefined location, and a log file is kept that records the steps of each extraction. The process is discussed in this document in more detail in the section on :doc:`running the tool <../execute/execute>`.

.. raw:: latex

   \newpage

Defining the way that extractions should be carried out, the output that they generate and the layers that can potentially be included is done via a configuration document written in XML. Using this document the user can configure all the parts of the extraction, for example:

* The name of the geographic layer containing the partner boundaries, and its key columns.
* The location of the SQL Server file DNS (defining the connection details for the database).
* The location of the output folder.
* For each data layer, a detailed definition of what information should be returned from it.
* Details on the display and labelling of output from individual data layers where relevant.

Using this configuration file, each individual LERC can tailor the Data Extractor tool to its individual requirements. Examples of the XML file are included in the :doc:`../appendix/appendix`, and the process of setting up this file is discussed in the section on :doc:`setting up the tool <../setup/setup>`. 

Additionally to the XML file the SQL server database is set up via a number of auxiliary tables and stored procedures. Again, the process of configuring this is discussed in the section on :doc:`setting up the tool <../setup/setup>`. 

.. index::
	single: Benefits

Benefits
========

There are a number of clear benefits to using the Data Extractor tool for carrying out routine data extractions for partners. 

1. The tool, by encapsulating and automating the process, saves considerable time over carrying out these extractions manually.
#. Both the process and the outputs of the extraction are standardised, therefore minimising the risk of user error that is present in a manual extraction.
#. By specifying the outputs of the tool centrally through the configuration file, the output for each extraction is consistent with all other extractions, regardless of the individual carrying out the extraction. This leads to comparability of results and a predictable experience for the users of a data extraction service.
#. The extractions are repeatable and, through the inclusion of the log file, automatically documented.
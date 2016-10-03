.. index::
	single: FAQ
	see: Frequently asked questions; FAQ

**************************
Frequently Asked Questions
**************************

This is a list of Frequently Asked Questions about the Data Extractor tool. Feel free to suggest new entries!

General questions
=================

**How do I get a copy of the tool?**

	The latest version of the tool can be downloaded from `GitHub <https://github.com/LERCAutomation/DataExtractor-MapInfo/releases>`_. Please ensure that you use the correct configuration file, an example copy of which is also included with the release.

**Can several people use the tool at the same time?**

	Any number of users can use the tool simultaneously if they have a copy of it loaded in their own copy of MapInfo. The tool uses the data layers that are loaded in GIS in a read-only fashion, so there is no limit to the number of users of the tool. The stored procedures that are run store their temporary results in tables that carry the login name of the user, so as long as each user has a unique login ID no conflicts should arise. However, where results are written to a central (network) location, and the extraction is run for the same partner, conflicts may occur.

**Does the tool work with QGIS or ArcGIS?**

	Currently only a MapInfo implementation of the tool exists. However, if funding was available the tool could be adapted to also support ArcGIS and/or QGIS.

Operating the tool
==================

**One of the data tables I want to use isn't showing in the form. How do I get it to show up?**

	This issue can arise in several ways:

	- The table is a MapInfo GIS layer and isn't loaded in the active workspace. In this case, a :ref:`message will pop up <figlaunchwarning>` before the form is shown telling you the layer isn't loaded. Add the layer to the workspace and the problem should be resolved.
	- The table, either an SQL table or MapInfo GIS layer, isn't listed in the XML configuration document (or its name is not being obtained within the :ref:`TableListSQL node <tablelistsql>`). Please refer to the :doc:`setup <../setup/setup>` section and add it as a map layer or amend the SQL statement as appropriate.
	- The table is a MapInfo GIS layer, and it is listed in the configuration document, but the :ref:`TableName <maptables>` is spelled incorrectly. Note that the name must follow the exact format of the name of the layer in the active workspace.

**The partner I want to extract data for is not shown in the form. How do I get the name to show up?**

	This issue can arise in two ways:

	- The partner boundary polygon does not exist in the partner boundary SQL table. Add it to the table.
	- The partner's status in not **Active**. Change the value of the partner's status in the :ref:`ActiveColumn <activecolumn>` to ``Y``.

**The tool is not extracting the right data for the partner**
	
	This issue will arise if the names of files in the :ref:`FilesColumn <filescolumn>` are not correct. Check that the names match the table names in the XML configuration file. Alternatively, check the :ref:`FormatColumn <formatcolumn>` and the :ref:`ExportColumn <exportcolumn>` to ensure the correct format of data is requested.


Tool issues
===========

**How do I report a new bug or propose a change in the tool?**

	Please check the existing known issues and change requests on the LERCAutomation pages on `GitHub <https://github.com/LERCAutomation/DataExtractor-MapInfo>`_ before reporting/proposing new issues or changes. If you have a new issue or request you can submit it there and it will be picked up by the developers. Alternatively, you can email suggestions to `Hester <mailto:Hester@HesterLyonsConsulting.co.uk>`_ or `Andy <mailto:Andy@AndyFoyConsulting.co.uk>`_. 

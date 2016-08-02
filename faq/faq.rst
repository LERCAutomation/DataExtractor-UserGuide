.. index::
	single: FAQ
	see: Frequently asked questions; FAQ

**************************
Frequently Asked Questions
**************************

This is a list of Frequently Asked Questions about the HLU Tool. Feel free to
suggest new entries!

General questions
=================

**How do I get a copy of the tool?**

	The source code as well as the installer setups can be downloaded from `GitHub <https://github.com/LERCAutomation/DataExtractor-MapInfo/releases>`_. Please ensure that you use the correct configuration file, a copy of which is included in the :doc:`Appendix <../appendix/appendix>`. An example file is also included with the release, in the MapBasic folder.

**Can several people use the tool at the same time?**

	Any number of users can use the tool if they have a copy of it installed on their PC. The tool uses the data layers in a read-only fashion, and so there is no limit to the number of users of the tool. The stored procedures that are run store their temporary results in tables that carry the login name of the user, so as long as each user has a unique login ID no conflicts should arrive. Where results are written to a central (network) location and the extraction is run for the same partner conflicts may occur.

**Does the tool work with QGIS or ArcGIS?**

	Currently only a MapInfo implementation of the tool exists. However, if funding was available the tool could be adapted to also support ArcGIS and/or QGIS.

Operating the tool
==================

**One of the data layers I want to use isn't showing in the form. How do I get it to show up?**

	This issue can arise in several ways:

	- The layer is a MapInfo table and isn't loaded in your GIS document. In this case, a `message will pop up <../execute/execute.html#figlaunchwarning>`__ before the form is shown telling you the layer isn't loaded. Add the layer to the GIS interface and the problem should be resolved.
	- The layer is either an SQL table or MapInfo table and isn't listed in the XML configuration document (or it is not being obtained within the `TableListSQL node <../setup/setup.html#tablelistsql>`__. Please refer to the :doc:`setup <../setup/setup>` section and add it as a map layer or amend the SQL statement as appropriate.
	- The layer is a MapInfo table, and it is listed in the configuration document, but the `TableName <../setup/setup.html#tablename>`_ is spelled incorrectly. Note that the name is case sensitive and must follow the exact format of the name of the layer in the GIS document.

**The partner I want to extract data for is not shown in the form. How do I get it to show up?**

	This issue can arise in two ways:

	- The partner boundary polygon does not exist in the partner boundary SQL table. Add it to the table.
	- The partner's status in not Active. Change the value of the partner's status in the `ActiveColumn <../setup/setup.html#activecolumn>`__

**The tool is not extracting the right data for the partner**
	
	This issue will arise if the names of files in the `FilesColumn <../setup/setup.html#filescolumn>`__ are not correct. Check that the names match the table names in the XML configuration file. Alternatively, check the `FormatColumn <../setup/setup.html#formatcolumn>`__ and the `ExportColumn <../setup/setup.html#exportcolumn>`__ to ensure the correct format of data is requested.


Tool issues
===========

**How do I report a new bug or propose a change in the tool?**

	Please check the existing known issues and change requests on the LERCAutomation pages on `GitHub <https://github.com/LERCAutomation/DataExtractor-MapInfo>`_ before reporting/proposing new issues or changes. If you have a new issue or request you can submit it there and it will be picked up by the developers. Alternatively, you can email suggestions to `Hester <mailto:Hester@HesterLyonsConsulting.co.uk>`_ or `Andy <mailto:Andy@AndyFoyConsulting.co.uk>`_. 



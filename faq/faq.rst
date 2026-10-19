.. index::
	single: FAQ
	see: Frequently asked questions; FAQ

**************************
Frequently Asked Questions
**************************

This is a list of Frequently Asked Questions about the DataExtractor tool. Feel free to suggest new entries!

General questions
=================

**How do I get a copy of the tool?**

	Obtain the compiled tool and matching profiles from your administrator. The `MapInfo repository <https://github.com/LERCAutomation/DataExtractor-MapInfo>`_ contains the source and supporting files. Use an MBX built for your MapInfo version and architecture; editing source files alone does not update the executable. Current profile examples and the :ref:`change_log` are in the appendix.

**Can several people use the tool at the same time?**

	Any number of users can use the tool simultaneously if they have a copy of it loaded in their own copy of MapInfo. The tool uses the data layers that are loaded in GIS in a read-only fashion, so there is no limit to the number of users of the tool. The stored procedures that are run store their temporary results in tables that carry the login name of the user, so as long as each user has a unique login ID no conflicts should arise. However, where results are written to a central (network) location, and the extraction is run for the same partner, conflicts may occur.

**Does the tool work with QGIS?**

	The MapInfo tool is a MapBasic application and cannot run in QGIS. A QGIS implementation would require separate development.

**Is there an ArcGIS Pro version?**

	Yes. A separate ArcGIS Pro version is available with its own `DataExtractor user guide <https://github.com/LERCAutomation/DataExtractor-ArcPro-UserGuide>`_. This guide covers the MapInfo version.

Operating the tool
==================

**One of the data tables I want to use isn't showing in the form. How do I get it to show up?**

	This issue can arise in several ways:

	- The table is a MapInfo GIS layer and isn't loaded in the active workspace. In this case, the tool warns before showing the form that the layer is not loaded. Add the layer to the workspace and the problem should be resolved.
	- The output definition is not listed under SQLTables or MapTables in the selected profile. For SQL outputs, also check that each partner's SQLTableColumn names an available source returned by :ref:`TableListSQL <tablelistsql>`. Please refer to the :doc:`setup <../setup/setup>` section and add it as a map layer or amend the SQL statement as appropriate.
	- The table is a MapInfo GIS layer, and it is listed in the configuration document, but the :ref:`TableName <maptables>` is spelled incorrectly. Note that the name must follow the exact format of the name of the layer in the active workspace.

**The partner I want to extract data for is not shown in the form. How do I get the name to show up?**

	Check the following:

	- The partner boundary row must exist in the MapInfo PartnerTable, and that table must be open. The form reads partners from MapInfo, rather than from the SQL Server copy.
	- The partner must match :ref:`PartnerClause <partnerclause>` in the profile, typically ``Active = "Y"``. Check the row's active flag and any other conditions in that clause.

**The tool is not extracting the right data for the partner**
	
	Check the output names in :ref:`SQLFilesColumn <sqlfilescolumn>` and :ref:`MapFilesColumn <mapfilescolumn>` against the child node names in the selected profile. Check the form selection, partner source table, WhereClause, exclusion option, survey tags and selection type. If the boundary has changed, also update its SQL Server copy. Alternatively, check the :ref:`FormatColumn <formatcolumn>` and the :ref:`ExportColumn <exportcolumn>` to ensure the correct format of data is requested.


**Where are my outputs after a cancelled run or a transfer failure?**

    When WorkingDir is enabled, completed partners are already delivered to
    DefaultPath and unfinished files remain locally. A failed transfer may
    leave files in both places. Check the paths recorded in the log before
    rerunning or recovering files; see :ref:`working_outputs`.

**Why is the main log not changing while the tool is running?**

    The main log is published at the end of the run. During processing, use
    the temporary journal in the working run folder, or in LogFilePath when
    staging is disabled. See :ref:`run_logs`.

**Why has a ZIP-enabled run stopped, or left original files beside a ZIP?**

    Check that Windows tar.exe and fc.exe are available and allowed. Allow
    enough free space for archive verification. Failed verification preserves
    originals and the previous ZIP; failed cleanup may leave a verified ZIP
    and originals together. Follow the recovery paths in the log and see
    :ref:`zip_outputs`.

Tool issues
===========

**How do I report a new bug or propose a change in the tool?**

	Please check the existing known issues and change requests on the LERCAutomation pages on `GitHub <https://github.com/LERCAutomation/DataExtractor-MapInfo>`_ before reporting/proposing new issues or changes. If you have a new issue or request you can submit it there and it will be picked up by the developers. Alternatively, you can email suggestions to `Hester <mailto:Hester@HesterLyonsConsulting.co.uk>`_ or `Andy <mailto:Andy@AndyFoyConsulting.co.uk>`_. 

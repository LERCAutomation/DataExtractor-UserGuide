.. index::
	single: FAQ
	see: Frequently asked questions; FAQ
    single: Troubleshooting

**************************
Frequently Asked Questions
**************************

This is a list of Frequently Asked Questions about the DataExtractor tool. Feel free to suggest new entries!

General questions
=================

.. index::
    single: Downloads
    single: MBX files; obtaining

**How do I get a copy of the tool?**

	Obtain the compiled tool and matching profiles from your administrator. The `MapInfo repository <https://github.com/LERCAutomation/DataExtractor-MapInfo>`_ contains the source and supporting files. Use an MBX built for your MapInfo version and architecture; editing source files alone does not update the executable. Current profile examples and the :ref:`change_log` are in the appendix.

.. index::
    pair: Concurrent use; output conflicts
    single: User IDs; concurrent use

**Can several people use the tool at the same time?**

Each user can run the tool in their own MapInfo session, but coordinate access
to shared resources. Use separate user IDs for SQL intermediate tables and
user-specific logs, and avoid overlapping runs under the same ID. Do not run
extractions that write the same final partner folders or filenames at the
same time. Fresh working folders do not prevent final-output conflicts.

Coordinate partner-boundary uploads and other changes to shared SQL data with
the database administrator. Separate sessions and user IDs alone do not make
all shared operations safe. See :ref:`output_overwriting`.

.. index::
    single: QGIS

**Does the tool work with QGIS?**

	The MapInfo tool is a MapBasic application and cannot run in QGIS. A QGIS implementation would require separate development.

.. index::
    single: ArcGIS Pro version

**Is there an ArcGIS Pro version?**

	Yes. A separate ArcGIS Pro version is available with its own `DataExtractor user guide <https://github.com/LERCAutomation/DataExtractor-ArcPro-UserGuide>`_. This guide covers the MapInfo version.

Operating the tool
==================

.. index::
    pair: Troubleshooting; missing tables

**One of the data tables I want to use isn't showing in the form. How do I get it to show up?**

	This issue can arise in several ways:

	- The table is a MapInfo GIS layer and isn't loaded in the active workspace. In this case, the tool warns before showing the form that the layer is not loaded. Add the layer to the workspace and the problem should be resolved.
	- The output definition is not listed under SQLTables or MapTables in the selected profile. For SQL outputs, also check that each partner's SQLTableColumn names an available source returned by :ref:`TableListSQL <tablelistsql>`. Please refer to the :doc:`setup <../setup/setup>` section and add it as a map layer or amend the SQL statement as appropriate.
	- The table is a MapInfo GIS layer, and it is listed in the configuration document, but the :ref:`TableName <maptables>` is spelled incorrectly. Note that the name must follow the exact format of the name of the layer in the active workspace.

.. index::
    pair: Troubleshooting; hidden controls
    single: Form options; hidden controls

**Why are some options missing from the form?**

The selected profile can hide optional controls:

* Blank ``DefaultZip`` hides **Zip extract files?**.
* Blank ``DefaultExclusion`` or ``ExclusionClause`` hides **Apply exclusion clause?**.
* Blank ``DefaultUseCentroids`` hides **Select polygons by centroids?**.
* Blank ``EasyLoaderCommand`` hides **Upload partner table to server?**.

Hidden checkboxes are initially unchecked. Ask the administrator to check the
chosen profile in :doc:`../setup/setup`, then reopen the form after any change.
**Clear log file?** remains visible even when ``DefaultClearLogFile`` is blank;
in that case it starts unchecked. Selection Type applies to SQL outputs only.

.. index::
    pair: Troubleshooting; missing partners

**The partner I want to extract data for is not shown in the form. How do I get the name to show up?**

	Check the following:

	- The partner boundary row must exist in the MapInfo PartnerTable, and that table must be open. The form reads partners from MapInfo, rather than from the SQL Server copy.
	- The partner must match :ref:`PartnerClause <partnerclause>` in the profile, typically ``Active = "Y"``. Check the row's active flag and any other conditions in that clause.

.. index::
    pair: Troubleshooting; incorrect extracts
    single: Partner boundaries; troubleshooting geometry

**The tool is not extracting the right data for the partner**
	
	Check the output names in :ref:`SQLFilesColumn <sqlfilescolumn>` and :ref:`MapFilesColumn <mapfilescolumn>` against the child node names in the selected profile. Check the form selection, partner source table, WhereClause, exclusion option, survey tags and selection type. If the boundary has changed, also update its SQL Server copy. Alternatively, check the :ref:`FormatColumn <formatcolumn>` and the :ref:`ExportColumn <exportcolumn>` to ensure the correct format of data is requested.

    For MapInfo outputs, check the selected partner's boundary. If that partner
    has no geometry, only the output's attribute condition filters the source
    rows; other partners do not change the selection. See :ref:`mapinfo_selection`.
    Ordinary spatial MapInfo selection retains whole features, so geometry
    extending beyond the partner boundary does not by itself indicate an error.


.. index::
    pair: Troubleshooting; shortened output names
    single: Output names; troubleshooting collisions

**Why is an output filename shortened, or why has the run stopped with an output-name conflict?**

After expanding naming variables, the tool keeps only the first 31 characters
of SQL and MapInfo output base names. The log records any truncation. Before
extraction or partner upload, it checks whether requested outputs would use
the same destination file. A conflict stops the run and the log identifies
both definitions and partners. Use shorter distinct names or separate output
folders, then rerun; see :ref:`output_name_limits`.

.. index::
    pair: Troubleshooting; missing outputs
    single: Recovery; cancelled or failed transfers

**Where are my outputs after a cancelled run or a transfer failure?**

    When WorkingDir is enabled, completed partners are already delivered to
    DefaultPath and unfinished files remain locally. A failed transfer may
    leave files in both places. Check the paths recorded in the log before
    rerunning or recovering files; see :ref:`working_outputs`.

.. index::
    pair: Troubleshooting; log updates

**Why is the main log not changing while the tool is running?**

    The main log is published at the end of the run. During processing, use
    the temporary journal in the working run folder, or in LogFilePath when
    staging is disabled. See :ref:`run_logs`.

.. index::
    pair: Troubleshooting; ZIP failures

**Why has a ZIP-enabled run stopped, or left original files beside a ZIP?**

    Check that Windows tar.exe and fc.exe are available and allowed. Allow
    enough free space for archive verification. Failed verification preserves
    originals and the previous ZIP; failed cleanup may leave a verified ZIP
    and originals together. Follow the recovery paths in the log and see
    :ref:`zip_outputs`.

Tool issues
===========

.. index::
    single: Bug reports
    single: Change requests

**How do I report a new bug or propose a change in the tool?**

Check the existing `MapInfo issues
<https://github.com/LERCAutomation/DataExtractor-MapInfo/issues>`_ first. For a
new issue, include:

* The DataExtractor and MapInfo versions, including the MapInfo architecture.
* The profile settings involved and the relevant partner output requests.
* The steps to reproduce the issue, the result expected and what happened.
* Relevant messages from the current log and any retained diagnostics.

Remove confidential data and credentials from logs, profiles and sample data
before sharing them. Feature requests should explain the workflow and desired
result. You can also email `Hester <mailto:Hester@HesterLyonsConsulting.co.uk>`_
or `Andy <mailto:Andy@AndyFoyConsulting.co.uk>`_.

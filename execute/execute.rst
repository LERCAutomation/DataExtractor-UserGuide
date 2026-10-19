.. index::
	single: Running the tool

****************
Running the tool
****************

As discussed in the :doc:`Setting up the tool <../setup/setup>` section, the DataExtractor tool is operated from a MapInfo workspace within which the GIS layers required to run the tool are already loaded. It also relies on an SQL database containing the boundaries of the relevant partners, the SQL tables containing any data that may be extracted, and a configuration document for setting up the tool. Therefore, before running the tool, ensure the following conditions are met:

- A MapInfo document has been created which contains both the partner boundary GIS layer and any MapInfo GIS layers that may be included in the extraction. 
- The SQL Server connection is available. For SQL extractions, the database contains the required data, auxiliary tables and stored procedures, and an up-to-date partner boundary table (or the upload option is configured).
- The file DSN for the SQL database has been created.
- The XML configuration document has been set up correctly, both for general settings and for each individual layer that will be queried. It is also named correctly and in the same directory as the tool MapBasic application (.MBX).
- The DataExtractor tool has been installed and is loaded in MapInfo using the MapInfo Tool Manager.

.. seealso::
	Please refer to the :doc:`setup <../setup/setup>` section for further information about any of these requirements.

.. index::
	single: Opening the form

Opening the form
================

Launch DataExtractor using the ribbon button or classic Tools menu described
in :ref:`figExtractorLaunch`.


If several profile XML files are present beside the MBX, first choose the required profile. If only one is present, it is loaded automatically. The main configuration file selects the default profile.

If there are any structural issues with the XML document, the tool will display a message that it has encountered an error, and not load any further. If any of the map layers that are listed in the configuration document are not present in the active workspace a warning will be shown. The layers that are missing will not be loaded into the form and so cannot be included in the extracts.


Provided that the XML document is otherwise correct, the form will display (:numref:`figExtractorForm`).

.. index::
	single: Using the form

Using the form
==============

The form can process multiple partners and output definitions during a single execution. Select the partners for which you wish to run the extraction, and the SQL and / or MapInfo tables that you would like to include, what type of SQL extraction you would like to carry out (spatial, survey tags, or both), make sure all other options are correct then press **OK**.

.. _figExtractorForm:

.. figure:: figures/DisplayForm.png
    :align: center

    Selecting partners, output definitions and extraction options

The :guilabel:`SQL Tables` list contains output definitions from SQLTables;
the source SQL table is specified separately for each partner in SQLTableColumn.
The :guilabel:`MapInfo Tables` list contains configured layers that are open in
MapInfo. Selecting an output in the form does not override the partner's
SQLFilesColumn or MapFilesColumn: it must be requested in both places.
Double-click a partner to display its notes.

Check the available options before starting:

* :guilabel:`Zip extract files?` packages each partner's outputs separately.
* :guilabel:`Apply exclusion clause?` adds the configured exclusion condition
  to SQL outputs only.
* :guilabel:`Clear log file?` archives the existing main log before starting
  a new one. Leave it unchecked to append this run to the existing log.
* :guilabel:`Select polygons by centroids?` passes the centroid option to
  SQL Server selection. MapInfo layers continue to use intersection.
* :guilabel:`Upload partner table to server?` uploads the open partner table
  using EasyLoader when SQL outputs have been selected. Otherwise ensure
  the SQL Server copy is already up to date.

Some options may be hidden by the profile. Selection Type applies to SQL
outputs: the combined option includes spatial matches and survey-tag matches.
Spatial MapInfo layers use the partner boundary; non-spatial MapInfo tables
use their configured attribute condition without a boundary intersection.

.. caution::
	The tool can run for a considerable amount of time dependent on the number of records that are being selected.

A progress window shows the extraction progress. Use **Cancel** to interrupt
processing; see :ref:`working_outputs` for handling unfinished local outputs.

When the extract process finishes it asks the user whether to close the form or keep it open for subsequent use.

Once the user makes a choice the log file is shown. This should be checked thoroughly to ensure that all expected extracts have been generated, the format of the extract files is correct, and that the number of records included in each extract file is as expected.

The following illustrative excerpt shows the kind of messages to check.
Timestamps and intervening messages are omitted, and the name and count are
examples rather than the results of a recorded test run:

.. code-block:: text

    Process started!
    Processing partner 'Example Partner (P1)' ...
    25 records selected.
    Exporting as a CSV file ...
    Export complete.
    Processing for partner complete.
    Process completed!

For ZIP output, also check for successful archive verification. With
WorkingDir enabled, check the partner transfer and final diagnostics messages.
Review the complete log for errors and skipped outputs, even when the final
message says processing completed.

You can now repeat the extract process for different partners and/or files as required.


.. index::
	single: Extraction results

Extract results
===============

Completed outputs are delivered to the :ref:`DefaultPath <defaultpath>` folder specified in the profile. If WorkingDir is configured, they are created locally first and transferred after each partner is completed. Each partner has its own sub-folder where the extract files for that partner are stored in the formats specified in the partner GIS layer.

The main log is saved in :ref:`LogFilePath <logfilepath>` as ``DataExtractor_<userid>.log``. Check it even after a completion message: individual outputs can be skipped because no records match, the partner does not request them, or the record count exceeds RecMax.


.. _working_outputs:

Local working folder and recovery
=================================

With WorkingDir configured, each run creates a fresh subfolder there. Partner
and format subfolders use the same names as at the final destination. Exports,
CSV/TXT post-processing and optional ZIP creation finish before the tool closes
the partner's output tables and transfers its folder to DefaultPath. Completed
partners are transferred during the run, rather than waiting for every partner.

Transfers use Windows Robocopy with three retries and a two-second delay.
Existing files with matching names are replaced; unrelated destination files
are retained. A transfer failure stops further processing and leaves remaining
local files at the location recorded in the log. Transfers can partially
succeed, so check both locations before recovering an output.

Cancellation retains unfinished local outputs. A later run uses a fresh working
folder and does not automatically resume or include retained files. Check the
log and decide whether to recover those files or rerun the affected partner.
Empty working folders are removed after processing.

When WorkingDir is missing or blank, outputs are created directly in DefaultPath.
Choose distinct partner folders and avoid simultaneous runs writing to the same
destination.

.. _zip_outputs:

ZIP output
==========

ZIP creation uses the Windows native ``tar.exe`` and ``fc.exe`` tools with normal
user permissions. Their availability is checked before a ZIP-enabled run starts.
They must be installed and permitted by your organisation. There is no additional
ZIP script to deploy with v1.7.05; the legacy ``zip.vbs`` is not called by this
version. Configured export macros still use Windows Script Host.

The tool creates a candidate archive in a separate temporary folder, checks it,
extracts it and compares the restored files byte for byte with the originals.
Only a verified archive replaces an existing ZIP. Source files are then removed.
Allow disk space for the original outputs, candidate ZIP and extracted copy.
Links and junctions within a partner output folder are not supported.

If verification or archive replacement fails, the previous ZIP and original
outputs are retained. A source-cleanup failure can leave a verified new ZIP
alongside remaining originals. Check the recovery locations in the log and
confirm the archive's contents before deleting retained files. With staging
enabled, the completed ZIP is transferred with the partner's folder.

.. _run_logs:

Run logs and diagnostics
========================

During processing, messages are buffered in memory and written to a temporary
run journal. With staging enabled, the journal, Universal Translator files,
EasyLoader log and export-macro log use the working run folder. Without staging,
the journal uses LogFilePath. The journal is named
``DataExtractor_<userid>_tmp_<run-token>.log``. The working folder location is
recorded at the start of a staged run.

At completion, cancellation or a handled processing error, the tool moves
supporting log and translator files from the top level of the working folder
to LogFilePath and appends the buffered messages to the main log. The main log is then
opened for review. It is updated at the end of the run, so use the temporary
journal to inspect progress while processing.

If the main log cannot be written, the messages remain in memory and the
temporary journal is retained. Restore access to LogFilePath and retry before
starting another run; pending messages must be published first. Preserve the
journal if you need to close MapInfo, as the memory buffer will not survive
closing the application. A failed diagnostics transfer leaves files in the
working folder for recovery. The log records the relevant paths.

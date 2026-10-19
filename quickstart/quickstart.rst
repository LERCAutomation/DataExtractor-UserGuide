***********
Quick start
***********

Use these steps once an administrator has installed the tool and prepared the
workspace, database connection and profile. You do not need to edit XML for
routine use. For a new installation or upgrade, start with
:ref:`administrator_setup`.

.. index::
    single: Quick start
    pair: Routine use; extraction

.. _quick_start:

Run a routine extraction
========================

1. **Open the prepared MapInfo workspace.** Check that the partner boundary
   table and the MapInfo source layers you need are open. Check that the
   selected partners have the intended boundaries or attribute-only conditions;
   see :ref:`mapinfo_selection`.
#. **Launch DataExtractor and choose the profile.** Use the ribbon button or
   classic Tools menu. If a profile chooser appears, select the profile for
   the extraction you intend to run.
#. **Select the partners and outputs.** Select the required partners, SQL output
   definitions and MapInfo layers. Each output must also be requested by the
   partner's configured output list; see :ref:`partner_example`.
#. **Check the options.** Choose the SQL selection type and review exclusion,
   centroids, partner upload, ZIP and clear-log options where shown. Follow
   your organisation's profile instructions. See :ref:`output_formats` for
   output-format choices. Reusing output names can replace earlier files;
   preserve results you need to keep or use a separate destination. See
   :ref:`output_overwriting`.
#. **Click Ok and allow processing to finish.** The progress window shows the
   extraction progress. If you cancel or processing stops, follow
   :ref:`working_outputs` before recovering files or rerunning partners.
#. **Review the complete log.** Check errors, skipped outputs and record counts,
   even if the tool reports completion. Confirm any ZIP verification and
   working-folder transfers succeeded. Skipped outputs may leave files from
   earlier runs in the final folder, so use this run's log to identify its outputs.
#. **Check the final destination.** Confirm that the expected partner folders
   and requested file formats are present in DefaultPath. Review the log in
   LogFilePath and retain complete TAB or SHP file sets when sharing outputs.

:numref:`figExtractorForm` identifies the form controls. See
:doc:`../execute/execute` for the detailed requirements and options.

.. index::
    single: Worked example
    pair: Extraction; worked example
    single: Outputs; example filenames

.. _worked_example:

Worked example: one partner and two outputs
===========================================

This illustrative extraction uses the :ref:`appendix profile <example_xml>`
and the :ref:`worked partner row <partner_example>` in Setting up the tool.
An administrator must adapt the paths, prepare the database and partner
boundary, and open the ``Ancient_Woodland`` source table first. Include matching
records in both sources. The example data and workspace are not supplied with
this guide.

Choose ``DefaultProfile.xml`` if prompted, then use these selections:

.. list-table::
    :header-rows: 1
    :widths: 40 60

    * - Control
      - Choice
    * - Partner list
      - Example Partner (abbreviation ``P1``)
    * - SQL output list
      - AllSpecies
    * - MapInfo output list
      - AncientWoodland
    * - Selection Type
      - Spatial Only, because this example supplies no survey tags
    * - Zip extract files?
      - Unchecked, so the individual outputs can be inspected
    * - Other optional checkboxes, where shown
      - Unchecked for this example; the SQL partner boundary is already current

Use a fresh example output folder and click **Ok**. The partner row requests
**Both** GIS formats and a **CSV** export. With the blank ``OutputType`` settings
in the appendix profile, a successful run with matching records produces:

.. list-table::
    :header-rows: 1
    :widths: 50 50

    * - Base filename
      - Contents and formats
    * - ``Species_P1_2026`` (for a run in 2026)
      - AllSpecies results from ``LERC_Spp_Point``, as TAB, SHP and CSV
    * - ``AncientWoodland_P1``
      - AncientWoodland results from ``Ancient_Woodland``, as TAB, SHP and CSV

The species filename uses the year the run starts. The partner folder uses
``P1`` and the run's financial quarter and year, as described under
:ref:`naming_variables`. Find the completed files beneath ``DefaultPath``, in
the configured format subfolders. The appendix profile leaves ``WorkingDir``
blank, so this example writes directly to that destination.

Review the log in ``LogFilePath`` for both outputs and their record counts.
Empty results or other conditions may cause an output to be skipped; selecting
a definition in the form does not override the partner's requested output list.
Keep TAB and SHP companion files together when sharing the results. See
:ref:`output_formats` for format overrides and :ref:`run_logs` for log review.

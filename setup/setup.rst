*******************
Setting up the tool
*******************

Before the DataExtractor tool will function, it needs to be installed and configured. It is essential that the configuration is carried out first.

.. index::
	single: Configuring the tool

Configuring the tool
====================

The DataExtractor tool requires a minimum of two XML configuration files:

1. An XML file called 'DataExtractor.xml'. This simply defines:

	* The title of the tool as it appears in the tool menu
	* The default XML profile to be pre-selected (where more than one XML profile is present)

	.. caution::
		The name of this configuration file must be 'DataExtractor.xml'. The tool will not load if this file is not found.


2. One or more user-maintained XML profiles (with the suffix '.xml') containing a detailed configuration for the tool.

	.. tip::
		An example of an XML profile can be found in the :doc:`Appendix <../appendix/appendix>`.


Attributes and settings in the XML profiles are presented as nodes (beginning with a start node, e.g. ``<example>``, and finishing with an end node, e.g. ``</example>``), with the value for that node held between the ``<value>`` and ``</value>`` tags.

The XML file can be edited in a text editor such as Notepad or Wordpad, or using an XML editor. The configuration file is split into three sections:

General attributes
	General and default attributes for the tool.

SQL Tables
	Deals with how extracts from each SQL Server table should be handled.

Map Tables
	Deals with how extracts from each GIS layer should be handled.

.. caution::
	It is important that the structure of the file is maintained as it is presented in the :doc:`Appendix <../appendix/appendix>`. Any changes to the structure may result in the DataExtractor tool not loading, or not working as expected.

Once editing has been completed and the edits have been saved, it is recommended that the configuration file is opened using an XML editor or web browser which will help highlight any editing errors – only if the structure of the file is valid will the whole file be displayed in the Internet browser.

.. note::
	It is recommended that the configuration file is kept in a central (network) location, so that all users use the same configuration. Additionally, it is essential that the configuration file is kept in the same folder as the compiled version of the tool.


.. index::
	single: Special characters in XML

.. raw:: latex

   \newpage

Special characters in XML
-------------------------

The characters ``&``, ``<`` and ``>`` are not valid within values and, so in order to be used, must be **escaped** with XML entities as follows:

<
	This must be escaped with ``&lt;`` entity, since it is assumed to be the beginning of a tag. For example, ``RecYear &lt; 2010``

>
	This should be escaped with ``&gt;`` entity. It is not mandatory -- it depends on the context -- but it is strongly advised to escape it. For example, ``RecYear &gt; 1980``

&
	This must be escaped with ``&amp;`` entity, since it is assumed to be the beginning of a entity reference. For example, ``TaxonGroup = 'Invertebrates - Dragonflies &amp; Damselflies'``


.. index::
	single: Setup for MapInfo

Setup for MapInfo
-----------------

.. index::
	single: General attributes; MapInfo

General attributes
******************

The MapInfo settings below describe DataExtractor v1.7.05. The main file
``DataExtractor.xml`` and all profile XML files must be beside the compiled
``.MBX`` application. Select the appropriate executable for your MapInfo version
and 32-bit or 64-bit installation. The screenshots show an earlier interface;
the current options are described in :doc:`../execute/execute`.

Main configuration file
***********************

``DataExtractor.xml`` contains the following settings under ``DataExtractor``:

_`ToolTitle`
    The title used in the MapInfo Tools menu.

_`DefaultProfile`
    The profile name without the ``.xml`` extension to preselect when several
    profiles are present. Leave blank to use ``DefaultProfile``. If only one
    profile exists, it is loaded automatically. Otherwise the user chooses a
    profile before the extraction form opens.

Profile settings
****************

The following nodes belong under ``DataExtractor`` in each profile. The
:ref:`example_xml` shows their structure. Old MapInfo nodes ``FilesColumn``,
``ConfidentialClause`` and ``DefaultConfidential`` have been replaced by the
separate file-list and exclusion settings below.

_`Debug`
    Set to ``Yes`` to include additional diagnostic messages in the log;
    otherwise use ``No``.

_`LogFilePath`
    The folder for the main user-specific log, ``DataExtractor_<userid>.log``,
    and supporting diagnostic files. Missing folders are created if permissions
    allow. The run journal is written locally when WorkingDir is used and the
    accumulated messages are appended to the main log when the run finishes.

_`FileDSN`
    The full path to the file DSN defining the SQL Server connection. Configure
    the ODBC driver and access permissions for the MapInfo installation in use.

_`DefaultPath`
    The final output folder below which partner folders are created. It may
    contain the date variables described under :ref:`naming_variables`.

_`WorkingDir`
    An optional local folder used to create outputs before moving them to
    DefaultPath. A fresh subfolder is created for each run. Exports, export
    macros and ZIP creation finish locally before each partner is transferred.
    Leave this node missing or blank to write directly to DefaultPath. See
    :ref:`working_outputs` for completion, cancellation and recovery behaviour.

_`PartnerFolder`
    The partner subfolder name, for example
    ``%partner%_DataExchange_%qq%_%ffff%``. If blank, the partner abbreviation
    from ShortColumn is used. Choose a distinct folder for each partner and
    keep it within the output folder.

_`MapInfoFolder`, _`ArcGISFolder`, _`CSVFolder`, _`TXTFolder`
    Subfolders within each partner folder for TAB, SHP, CSV and TXT files,
    respectively. Leave a value blank to put that format directly in the
    partner folder. The XML setting named ArcGISFolder controls the shapefile
    output folder; it is part of the MapInfo profile.

_`DatabaseSchema`
    The schema used in SQL Server, typically ``dbo``.

_`TableListSQL`
    A SQL Server query returning the available source table names in its first
    column. Each partner's SQLTableColumn identifies which source to use.
    The form's SQL list shows the configured output definitions, rather than
    asking the user to choose one source table for all partners.

_`PartnerTable`
    The partner boundary table, which must be open in MapInfo. SQL extractions
    also require the corresponding table in SQL Server. It can be uploaded
    at the start of a run using the EasyLoader option below, or maintained
    separately. Keep the MapInfo and SQL Server copies consistent.

_`PartnerColumn`
    The column containing the partner name used to select its boundary.

_`ShortColumn`
    The column containing the partner abbreviation used for output naming.

_`NotesColumn`
    The column containing partner notes. Double-click a partner in the form
    to display its notes.

_`ActiveColumn`
    The name of the column holding the partner's active flag, normally ``Y``
    or ``N``. The current form filters partners using PartnerClause; setting
    this column alone does not define that filter.

_`PartnerClause`
    A MapInfo SQL condition defining which partners appear, for example
    ``Active = "Y"``. Supply the condition without ``WHERE``.

_`FormatColumn`
    The column specifying each partner's GIS output format: ``Tab``, ``Shp``
    or ``Both``. Leave the partner's value blank for no GIS output, unless
    an output definition supplies its own OutputType.

_`ExportColumn`
    The column specifying an additional text export: ``CSV`` or ``TXT``.
    Leave the partner's value blank for no text export. These are format
    names, rather than the old ``Y``/``N`` values. CSV includes column headings;
    TXT has no headings. Both use comma delimiters and Windows Latin-1 text.

_`SQLTableColumn`
    The column containing the SQL Server source table name for each partner.

.. _filescolumn:

_`SQLFilesColumn`
    The column listing the SQL output definition names required for each
    partner. Use the child node names under SQLTables, separated by commas,
    or ``ALL`` for all definitions. A blank value requests none. Only outputs
    also selected in the form are processed. Use distinct names that are not
    substrings of one another, as the current matching uses text searches.

_`MapFilesColumn`
    The equivalent column listing the child node names under MapTables.
    It also accepts ``ALL`` or a blank value, and is combined with the user's
    selection in the form.

_`TagsColumn`
    The column containing the comma-separated survey tags used for SQL Server
    selection. Survey-tag selection requires the appropriate database tables
    and stored procedures.

_`SpatialColumn`
    The name of the partner geometry column in SQL Server, for example
    ``SP_GEOMETRY``. This may differ from the MapInfo ``obj`` column.

_`SelectTypeOptions`
    Keep the options in this order: ``Spatial Only;Survey Tags Only;Spatial and
    Survey Tags``. The third option combines spatial matches with records
    matching the partner's survey tags. These options apply to SQL extractions.

_`DefaultSelectType`
    The initial option number: ``1`` for spatial, ``2`` for survey tags or
    ``3`` for both.

_`RecMax`
    The maximum selected record count for an individual output (before any
    SQL grouping). An output exceeding the limit is skipped and reported in the log; it is not truncated and
    this is not a combined limit for all of a partner's outputs.

_`DefaultZip`
    Set ``Yes`` or ``No`` for the initial :guilabel:`Zip extract files?`
    selection. Leave blank to hide the option. ZIP output requires Windows
    ``tar.exe`` and ``fc.exe``; see :ref:`zip_outputs`.

_`ExclusionClause`
    A SQL Server condition applied when :guilabel:`Apply exclusion clause?`
    is selected. Supply the condition without ``WHERE``. It is combined with
    each SQL output's WhereClause and does not filter MapInfo layers.

_`DefaultExclusion`
    Set ``Yes`` or ``No`` for the initial exclusion option. The option is
    hidden if this value or ExclusionClause is blank.

_`DefaultClearLogFile`
    Set ``Yes`` or ``No`` for :guilabel:`Clear log file?`. When selected,
    the existing main log is archived using its modification date and time
    before a new main log is started. Otherwise new run messages are appended.
    The checkbox remains visible when the setting is blank.

_`DefaultUseCentroids`
    Set ``Yes`` or ``No`` for :guilabel:`Select polygons by centroids?`.
    Leave blank to hide it. This option is passed to SQL Server selection;
    it does not change MapInfo layer intersection queries.

_`UTPath`
    The folder containing the Universal Translator supplied with the installed
    MapInfo version. Use the actual installation path.

_`UTCommand`
    The translator executable, commonly ``Imut.exe`` in older installations
    or ``Fme.exe`` in later ones. The translator is used for SHP output.

_`EasyLoaderCommand`
    The full path to ``EasyLoader.exe`` for the installed MapInfo version.
    If blank, the upload checkbox is hidden. Uploading is only attempted when
    SQL outputs have been selected.

_`EasyLoaderQuotes`
    Use ``Y`` to quote the file arguments passed to EasyLoader, including
    paths containing spaces. Use ``N`` for unquoted arguments. This setting specifically expects
    ``Y``, rather than ``Yes``. Check it against your installed EasyLoader version.

_`EasyLoaderSwitches`
    The command-line switches for EasyLoader. Configure these for the intended
    database upload and the installed EasyLoader version.

_`DefaultEasyLoader`
    Set ``Yes`` or ``No`` for the initial
    :guilabel:`Upload partner table to server?` option.

.. _naming_variables:

Output naming variables
***********************

DefaultPath supports the date variables below. PartnerFolder and OutputName
also support ``%partner%``, which is replaced with the partner abbreviation
from ShortColumn. Values are based on the date the run starts.

.. list-table:: Naming variables
    :header-rows: 1
    :widths: 25 75

    * - Variable
      - Meaning
    * - ``%partner%``
      - Partner abbreviation; for example ``ABC``
    * - ``%dd%``
      - Two-digit day; for example ``19``
    * - ``%mm%``
      - Two-digit month; for example ``10``
    * - ``%mmm%``
      - Short month name; for example ``Oct``
    * - ``%yy%`` / ``%yyyy%``
      - Two-digit / four-digit year; for example ``26`` / ``2026``
    * - ``%qq%``
      - Financial quarter: April-June is Q1, July-September Q2,
        October-December Q3 and January-March Q4
    * - ``%ffff%``
      - April-March financial year; for example ``26-27``

SQL table attributes
********************

.. _SQLTables:

Each child node under ``SQLTables`` defines an output subset. Its node name
identifies it in SQLFilesColumn and in the form. All selected SQL definitions
use the source table named in that partner's SQLTableColumn. See the
:ref:`example_xml` for a current XML example.

OutputName
    The output filename without an extension. This replaces the old SQL
    TableName setting. Naming variables are supported.

OutputType
    Leave blank to use the partner's GIS format, or specify ``TAB``, ``SHP``
    or ``Both`` to override it. A non-empty unrecognised GIS type, such as
    ``None``, suppresses GIS output. For SQL outputs, request CSV or TXT using
    ExportColumn; do not rely on OutputType to request a text export.

Columns
    The comma-separated SQL Server column list, or ``*``. Include the geometry
    column when spatial output is required.

WhereClause
    The SQL Server condition selecting this subset, without ``WHERE``.
    A blank condition includes the whole partner-selected subset, rather
    than the entire source table. The exclusion condition is added if enabled.

OrderClause
    An optional complete SQL clause, including its keywords, for example
    ``ORDER BY TAXONOMIC_GROUP, SPP_NAME``. Grouping must also be valid for
    the selected columns. Leave blank if no ordering or grouping is needed.

Macro / MacroParm
    Optional script path and additional parameter for post-processing CSV
    or TXT exports. The tool runs the script using ``wscript.exe`` and waits
    for it to finish before continuing. Arguments are passed in this order:
    MacroParm, export folder, export filename (including extension), and macro
    log path. The script must accept these arguments and write any diagnostic
    messages to that log. Macros run before ZIP creation and transfer, so the
    folder argument points to the working folder when staging is enabled.

_`Symbology`
    Optional styling for SQL-derived TAB outputs. Each child ``Symbol`` rule
    contains ``Clause`` (a MapInfo condition, or blank for all matching objects)
    and ``Object`` (``Point`` or ``Region``). Point rules contain a nested
    ``Symbol`` value; region rules contain ``Pen`` and ``Brush`` values.
    These replace the obsolete Type and Style nodes. Obtain style definitions
    from MapInfo, for example using ``Print CurrentSymbol()`` in the MapBasic
    window after choosing a symbol. See the appendix for the XML structure.

Map table attributes
********************

.. _MapTables:

Each child node under ``MapTables`` identifies an output in MapFilesColumn
and in the form. The source table must be open in MapInfo.

TableName
    The source table name as it appears in the active MapInfo workspace.

OutputName
    The output filename without an extension. If blank, TableName is used.
    Naming variables are supported.

OutputType
    Leave blank to use the partner's formats. ``TAB``, ``SHP`` or ``Both``
    overrides the GIS output. ``CSV`` or ``TXT`` requests that text format
    and suppresses GIS output for this map definition. ``None`` suppresses
    GIS output while retaining any text format requested by the partner.

Columns
    The comma-separated MapInfo column list, or ``*``. Include ``obj`` when
    spatial output is required.

WhereClause
    An optional MapInfo SQL condition without ``WHERE``. Spatial source
    layers are intersected with the partner boundary and filtered by this
    condition. Non-spatial tables are filtered by the condition alone.

OrderClause
    An optional complete MapInfo clause, for example ``ORDER BY SiteName``.

Macro / MacroParm
    The same CSV/TXT post-processing settings and argument order as for SQL
    outputs. Source MapInfo symbology is retained in map-layer outputs.

.. raw:: latex

   \newpage

.. index::
	single: Setting up the SQL database

Setting up the SQL Server database
==================================

For MapInfo v1.7.05, the tool calls ``AFSelectSppRecords`` and
``AFClearSppSubset`` in the configured DatabaseSchema. Install compatible
versions of these stored procedures and their database dependencies. Their
names are fixed in the MapBasic application, rather than configured in XML.
The connected account needs permission to run them and to create and clear
the user-specific intermediate tables. If automatic partner upload is used,
it also needs the appropriate EasyLoader database permissions.

In addition to any SQL tables containing records to be extracted using the DataExtractor tool, two auxiliary tables must also be present in the SQL Server database in order for the tool to be able to extract data from tables held in SQL Server. These are as follows:

_`Survey` table
	The Survey table is a standard table in the Recorder6 database. It is used to identify any records tagged with any survey tags listed in the `TagsColumn`_ column in the partner GIS layer.

_`Spatial_Tables` table
	This table contains information about any SQL data tables that may be used by the tool. The table has the following columns:

	.. tabularcolumns:: |L|L|

	.. table:: Format of the Spatial_Tables table

		+-----------------+-----------------------------------------------------------------------------------------------+
		|      Column     |                                          Description                                          |
		+=================+===============================================================================================+
		| TableName       | The name of the data table                                                                    |
		+-----------------+-----------------------------------------------------------------------------------------------+
		| OwnerName       | The database owner, usually ``dbo``                                                           |
		+-----------------+-----------------------------------------------------------------------------------------------+
		| XColumn         | The name of the column holding the X coordinates of the record                                |
		+-----------------+-----------------------------------------------------------------------------------------------+
		| YColumn         | The name of the column holding the Y coordinates of the record                                |
		+-----------------+-----------------------------------------------------------------------------------------------+
		| SizeColumn      | The name of the column holding the grid size of the record (in metres)                        |
		+-----------------+-----------------------------------------------------------------------------------------------+
		| IsSpatial       | Bitwise column (1 = Yes, 0 = No) defining whether the table is spatially enabled              |
		+-----------------+-----------------------------------------------------------------------------------------------+
		| SpatialColumn   | If the table is spatially enabled, the name of the geometry column (e.g. ``SP_GEOMETRY``)     |
		+-----------------+-----------------------------------------------------------------------------------------------+
		| SRID            | The name of the spatial reference system used to plot the records                             |
		+-----------------+-----------------------------------------------------------------------------------------------+
		| CoordSystem     | The coordinate system of the spatial data in the table                                        |
		+-----------------+-----------------------------------------------------------------------------------------------+
		| SurveyKeyColumn | The column containing the survey key for each record                                          |
		+-----------------+-----------------------------------------------------------------------------------------------+

	.. note::
		The British National Grid MapInfo `CoordSystem` definition is
		``Earth Projection 8, 79, "m", -2, 49, 0.9996012717, 400000, -100000 Bounds
		(-7845061.1011, -15524202.1641) (8645061.1011, 4470074.53373)``

	.. caution::
		This table must be filled out correctly for each table that is included in the DataExtractor tool.

	.. note::
		A number of stored procedures that are used by the tool for extracting the required records must also be present in the SQL Server database. To obtain copies of these procedures please contact `Hester <mailto:Hester@HesterLyonsConsulting.co.uk>`_ or `Andy <mailto:Andy@AndyFoyConsulting.co.uk>`_.


.. raw:: latex

   \newpage

.. index::
	single: Installing the tool

Installing the tool
===================

For v1.7.05, use a compiled application containing the v1.7.05 source changes;
editing the source does not update an existing MBX. Select the application
appropriate for your MapInfo version and 32-bit or 64-bit installation.

1. Keep the MBX, its supporting icon files, ``DataExtractor.xml`` and profile
   XML files together in the tool folder. Configure the profiles as described
   above before running the tool.
#. Open MapInfo's tool-management window. In the classic interface this is
   :kbd:`Tools --> Tool Manager...`; the equivalent controls in the ribbon
   interface depend on the MapInfo version installed.
#. Add the DataExtractor MBX using the add/browse controls, give it a title
   and description if requested, and load it (:numref:`figExtractorLoad`).
#. Enable automatic loading at startup if required. In the classic Tool
   Manager these settings are labelled **Loaded** and **AutoLoad**.

.. _figExtractorLoad:

.. figure:: figures/AddToolDialog.png
    :align: center

    Adding and loading the DataExtractor application in MapInfo

ZIP processing is built into v1.7.05 and does not require a separate ZIP
script. Export macros still require Windows Script Host if they are configured.
Local staging uses Windows Robocopy.

Launching the tool
------------------

In the 64-bit ribbon interface, the loaded tool adds a button to the
**Home** tab's **Tools** group (:numref:`figExtractorLaunch`). Click that
button to open DataExtractor. Its caption comes from ToolTitle in
``DataExtractor.xml`` and may differ between installations.

In the classic interface, open the tool's submenu under **Tools** and choose
**Run**. The submenu title also comes from ToolTitle, rather than the title
entered when registering the MBX in Tool Manager.

.. _figExtractorLaunch:

.. figure:: figures/DataExtractorToolMenu.png
    :align: center

    Launching DataExtractor from the Home tab's Tools group

.. tip::

    Save a MapInfo workspace containing the partner boundary table and the
    source MapInfo layers required by the profile. Opening that workspace
    prepares the layers for subsequent extractions.

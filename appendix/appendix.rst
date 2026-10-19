********
Appendix
********

.. index::
    single: Appendix; Change Log
    single: Change Log

.. _change_log:

Change Log
==========

This change log covers the MapInfo tool. Dates and version numbers follow the
comments in ``DataExtractor.mb`` where available; commit dates are used for
changes without dated version comments. The v1.7.05 release date is
19 October 2026. The early version numbering is retained as recorded.

The history was reconstructed from the `source comments
<https://github.com/LERCAutomation/DataExtractor-MapInfo/blob/master/MapBasic/DataExtractor.mb>`_,
`GitHub commits <https://github.com/LERCAutomation/DataExtractor-MapInfo/commits/master/>`_
and `tags <https://github.com/LERCAutomation/DataExtractor-MapInfo/tags>`_.
Not every version has a separate commit or tag. The only tag found when this
history was checked was ``v1.5.1``, dated 26 January 2015.

**1.7.05**
(19Oct2026)

    * :guilabel:`Improved` - Add optional WorkingDir staging, with a fresh folder for each run and transfer after each partner
    * :guilabel:`Improved` - Buffer run messages, keep a temporary journal and publish the main log and supporting diagnostics at completion
    * :guilabel:`Changed` - Create ZIP files using Windows native tools and verify their contents before replacing an existing archive
    * :guilabel:`Changed` - Consolidate output folder creation and retain unfinished outputs for recovery after cancellation or transfer failure
    * :guilabel:`Fixed` - Package the correct partner folder, including the final partner and skipped final outputs
    * :guilabel:`Fixed` - Close output tables, including non-spatial SQL TAB outputs, before packaging and transfer

**1.7.04 - subsequent source update**
(31Jul2025; commit date)

    * :guilabel:`Improved` - Increase SQL output, source-table and map-table array capacities from 99 to 199 entries

**1.7.04b**
(11Feb2022; commit date)

    * :guilabel:`Changed` - Mark SQL extracts skipped for exceeding RecMax as errors in the log

**1.7.04**
(01Oct2021)

    * :guilabel:`Fixed` - Fix bug saving all outputs to first partner folder
    * :guilabel:`Fixed` - Fix bug when exporting SQL file with no where clause

**1.7.03**
(01Oct2021)

    * :guilabel:`Changed` - Enable separate output folders for shp, tab, csv and txt files

**1.7.02**
(19Feb2021)

    * :guilabel:`Fixed` - Fix bug calculating record length

**1.7.01**
(28Dec2020)

    * :guilabel:`Changed` - Add debug option for log file
    * :guilabel:`Changed` - Standardise the log file format
    * :guilabel:`Changed` - Add option to set where clause for which partners to display
    * :guilabel:`Changed` - Output macro errors to log file
    * :guilabel:`Changed` - Wait for macros to complete before continuing
    * :guilabel:`Changed` - Only upload partner table to SQL Server if SQL outputs have been selected

**1.6.09**
(04Dec2020)

    * :guilabel:`Changed` - Wrap Where clause in brackets when exclusion clause is applied
    * :guilabel:`Changed` - Specify input SQL table in log

**1.6.08**
(13Aug2020)

    * :guilabel:`Fixed` - Fix bug not cleaning up SQL temporary tables
    * :guilabel:`Changed` - Use partner name not short name when selecting map files

**1.6.07**
(13Aug2020)

    * :guilabel:`Changed` - Enable EasyLoader to work in both 32bit and 64bit versions of MapInfo

**1.6.06**
(21May2020)

    * :guilabel:`Fixed` - Fix bug not cleaning up SQL temporary tables

**1.6.05**
(30Apr2020)

    * :guilabel:`Changed` - Skip file access errors and report in log at end

**1.6.04**
(23Apr2020)

    * :guilabel:`Fixed` - Fix bug loading profile with more SQL files than last profile

**1.6.03**
(18Apr2020)

    * :guilabel:`Changed` - Enable default output path to contain date variables

**1.6.02**
(06Apr2020)

    * :guilabel:`Fixed` - Fix bug to enable use centroids option

**1.6.01**
(16Mar2020)

    * :guilabel:`Changed` - Enable SQL Table to be defined in partner table
    * :guilabel:`Changed` - Update user interface to allow individual SQL files to be selected
    * :guilabel:`Changed` - Archive existing log file instead of deleting it
    * :guilabel:`Changed` - Enable partner output folders to be named in XML file
    * :guilabel:`Changed` - Enable SQL Files list to be 'ALL'

**1.5.42**
(23Jan2020)

    * :guilabel:`Fixed` - Avoid SQL Server timeouts by re-connecting for each output
    * :guilabel:`Fixed` - Reverse out change to EasyLoader to not use quotes in file paths

**1.5.41**
(31Oct2019)

    * :guilabel:`Fixed` - Fix bug executing EasyLoader with spaces in file paths

**1.5.40**
(08Aug2019)

    * :guilabel:`Changed` - Change confidential survey option to exclusion clause option

**1.5.39**
(30Jul2019)

    * :guilabel:`Changed` - Enable loading XML profiles when running in 64bit

**1.5.38**
(26Jul2019)

    * :guilabel:`Fixed` - Fix bug when partner table is empty

**1.5.37**
(19Jul2019)

    * :guilabel:`Changed` - Create output and log file paths if missing

**1.5.36**
(19Jul2019)

    * :guilabel:`Changed` - Add "DefaultEasyLoader" option to XML
    * :guilabel:`Changed` - Add details of funding organisations to About box

**1.5.35**
(11Jul2019)

    * :guilabel:`Changed` - Display Where and Order By clauses in log for map tables
    * :guilabel:`Fixed` - Fix bugs setting symbology for TAB files

**1.5.34**
(03Jul2019)

    * :guilabel:`Changed` - Add option to upload partner table to SQL Server

**1.5.33**
(05Jun2019)

    * :guilabel:`Changed` - Add "DefaultClearLogFile" option to XML

**1.5.32**
(23May2019)

    * :guilabel:`Changed` - Allow user to select XML profile to use

**1.5.31**
(28May2019)

    * :guilabel:`Changed` - Extract all records if spatial geometry is null

**1.5.30**
(28Apr2019)

    * :guilabel:`Changed` - Add separate clause for ORDER BY and GROUP BY

**1.5.29**
(16Apr2019)

    * :guilabel:`Fixed` - Fix bug with map table being deleted before use

**1.5.28**
(10Apr2019)

    * :guilabel:`Changed` - Add optional parameter to macro/script
    * :guilabel:`Changed` - Switch from cscript to wscript

**1.5.27**
(19Mar2019)

    * :guilabel:`Changed` - Add option to trigger macro/script to post-process each output file
    * :guilabel:`Changed` - Add option to override partner specified output type
    * :guilabel:`Changed` - Enable clauses to contain 'Group By' or 'Order By'

**1.5.26**
(19Mar2019)

    * :guilabel:`Changed` - Enable SQL output file names to contain spaces

**1.5.25**
(16Jan2019)

    * :guilabel:`Changed` - Add partner abbreviation as XML variable
    * :guilabel:`Changed` - Add date components as XML variables
    * :guilabel:`Changed` - Add new OutputName XML node to SQL and Map nodes

**1.5.24**
(17Dec2018)

    * :guilabel:`Fixed` - Always disconnect SQL connection

**1.5.23**
(13Dec2018)

    * :guilabel:`Fixed` - Fix parameter bug calling AFSelectSppRecords
    * :guilabel:`Changed` - Use schema when calling stored procedures

**1.5.22**
(29Oct2018)

    * :guilabel:`Changed` - Get partner layer spatial column name and pass to SQL stored procedure
    * :guilabel:`Changed` - Add option to use centroids for polygons

**1.5.21**
(22Oct2018)

    * :guilabel:`Changed` - Include new tool buttons for MI Pro 64bit

**1.5.20**
(03May2018)

    * :guilabel:`Fixed` - Try to avoid file locking issues in Windows 10
    * :guilabel:`Fixed` - Avoid loop after error processing a partner

**1.5.19**
(27Apr2018)

    * :guilabel:`Fixed` - Reset list value positions before processing to avoid entries being missed

**1.5.18**
(28Mar2018)

    * :guilabel:`Improved` - Reduce maximum process array size to avoid crash

**1.5.17**
(01Dec2017)

    * :guilabel:`Improved` - Increase max partners to 999 and max processes to 32,767 (the array limit)
    * :guilabel:`Changed` - Truncate temporary table names to 31 chars

**1.5.16**
(30Nov2017)

    * :guilabel:`Changed` - Truncate user ID if it means the temporary SQL will be too long for the MapCatalog (> 32 chars)

**1.5.15**
(16Nov2017)

    * :guilabel:`Improved` - Improve debug logging
    * :guilabel:`Changed` - Remove carriage returns, line feeds and tabs from where clauses

**1.5.14**
(09Aug2017)

    * :guilabel:`Changed` - Force universal translator to generate 2D instead of 3D shapefiles

**1.5.13**
(01May2017)

    * :guilabel:`Changed` - Split files into separate columns
    * :guilabel:`Fixed` - Fix bug with map tables not being closed when empty
    * :guilabel:`Changed` - Display file node and table name in map tables list

**1.5.12**
(25Jan2017)

    * :guilabel:`Changed` - Remove hard-coded check for 'GRPrecision' column, enable symbology clauses to be blank

**1.5.11**
(13Jul2016)

    * :guilabel:`Changed` - Get path and command for universal translator from config file and pass to sub-routine

**1.5.10**
(11Jul2016)

    * :guilabel:`Changed` - Enable separate instances for tool to run under different names in Tool menu

**1.5.9**
(30May2016)

    * :guilabel:`Changed` - Change version number to 3 parts

**1.58**
(05Apr2016)

    * :guilabel:`Fixed` - Fix premature disconnection error when dialog remains open
    * :guilabel:`Changed` - Revert to original SQL stored procedure
    * :guilabel:`Changed` - Save TXT files as comma-separated files
    * :guilabel:`Changed` - Add where clause option to Map tables

**1.57**
(09Mar2016)

    * :guilabel:`Changed` - Ask user if they want to keep the dialog open
    * :guilabel:`Changed` - Open log file using Notepad.exe

**1.56**
(22Feb2016)

    * :guilabel:`Changed` - Enable export of tables in either CSV or TXT format
    * :guilabel:`Changed` - Hide dialog checkbox options if default values are blank

**1.55**
(17Jan2016)

    * :guilabel:`Changed` - Load active partner details from MapInfo .tab file instead of SQL Server table
    * :guilabel:`Changed` - Count list of tables not already open in MapInfo
    * :guilabel:`Changed` - Perform user input checks before closing dialog
    * :guilabel:`Fixed` - Fix incorrect call to TranslateToShapefile function for Map tables

**1.54**
(08Dec2015)

    * :guilabel:`Changed` - Pass tags column to SQL stored procedure to also select records based on their survey tags

**1.53**
(11Sep2015)

    * :guilabel:`Changed` - Call new SQL stored procedures to create and clear selected subset tables
    * :guilabel:`Changed` - Check if result contains spatial data
    * :guilabel:`Improved` - Improved performance for setting symbology
    * :guilabel:`Changed` - Display numbers with thousand separators in log
    * :guilabel:`Changed` - Make log file user-specific to avoid concurrent use problems/over-writes

**1.52**
(08Jun2015)

    * :guilabel:`Changed` - Added userid to temporary SQL table name to enable concurrent use of tool

**v1.5.1 - first GitHub tag**
(26Jan2015; tag date)

    * :guilabel:`Changed` - Publish the first tagged MapInfo source version on GitHub

**1.51**
(01Jan2012)

    * Initial development of the MapInfo DataExtractor tool

.. raw:: latex

   \newpage

.. index::
    single: Example XML files

.. _example_xml:

Example XML files
=================

These MapInfo v1.7.05 examples illustrate the current node names. Adapt paths,
table and column names, filters, styles and EasyLoader options to your own
installation and data. The example source tables and columns must exist;
the examples are not a ready-to-run database configuration.

Main configuration file
-----------------------

Save this as ``DataExtractor.xml`` beside the MBX. ToolTitle and DefaultProfile
belong here, rather than in the profile. A blank DefaultProfile selects
``DefaultProfile`` when there is a choice of profiles.

.. code-block:: xml

    <?xml version="1.0" encoding="utf-8"?>

    <!--
    WARNING: This file should be changed carefully and a backup should be
    taken before any changes so that they can be backed out.  Changed lines
    can also be commented out as below.
    -->

    <!--
    This config file contains all the variables used by the DataExtractor
    MapBasic tool.

    The 'configuration' node is the 'root' node and signifies the start of the
    contents of the configuration file.

    The 'DataExtractor' node contains all of the entries relating to the
    MapBasic tool variables.

    Each entry relates to a file, folder, table name, column name or SQL statement
    used by the MapBasic tool to select and export data for partners.
    -->

    <configuration>
    <DataExtractor>

        <!-- The title to use for the program in the Tool menu -->
        <ToolTitle>
            <value>Data Extractor - Partners</value>
        </ToolTitle>

        <!-- The default XML file. If blank, the system looks for DefaultProfile.xml -->
        <DefaultProfile>
            <value></value>
        </DefaultProfile>

    </DataExtractor>
    </configuration>

Profile configuration file
--------------------------

Save the following as ``DefaultProfile.xml`` beside the MBX. WorkingDir is
blank for direct output; enter a local path such as ``C:\DataExtractor\Working``
to stage outputs. Partner rows should name ``AllSpecies`` in SQLFiles and
``AncientWoodland`` in MapFiles, or use ``ALL``. Set each partner's SQLTable
to a source table returned by TableListSQL, GISformat to ``Tab``, ``Shp`` or
``Both``, and Exportformat to ``CSV``, ``TXT`` or blank.

.. code-block:: xml

    <?xml version="1.0" encoding="utf-8"?>

    <!--
    WARNING: This file should be changed carefully and a backup should be
    taken before any changes so that they can be backed out.  Changed lines
    can also be commented out as below.
    -->

    <!--
    This config file contains all the variables used by the DataExtractor
    MapBasic tool.

    The 'configuration' node is the 'root' node and signifies the start of the
    contents of the configuration file.

    The 'DataExtractor' node contains all of the entries relating to the
    MapBasic tool variables.

    Each entry relates to a file, folder, table name, column name or SQL statement
    used by the MapBasic tool to select and export data for partners.
    -->

    <configuration>
    <DataExtractor>

      <!-- Whether to include debug messages in the logfile -->
      <Debug>
        <value>No</value>
      </Debug>

      <!-- Final log folder; created if permissions allow -->
      <LogFilePath>
        <value>C:\DataExtractor\Logs</value>
      </LogFilePath>

      <!-- The location of the File DSN that specifies which SQL Server database to connect to -->
      <FileDSN>
        <value>C:\DataExtractor\Database.dsn</value>
      </FileDSN>

      <!-- Final output folder below which partner folders are created -->
      <DefaultPath>
        <value>C:\DataExtractor\Extracts</value>
      </DefaultPath>

      <!-- Optional local staging folder, for example C:\DataExtractor\Working.
           Missing or blank preserves direct output to DefaultPath.
           Each run uses a fresh sub-folder; each partner is moved after processing. -->
      <WorkingDir>
        <value></value>
      </WorkingDir>

      <!-- The output sub-folder in which each partner's file will be created -->
      <PartnerFolder>
        <value>%partner%_DataExchange_%qq%_%ffff%</value>
      </PartnerFolder>

      <!-- The output sub-folder into which MapInfo files will be saved -->
      <MapInfoFolder>
        <value>MapInfo</value>
      </MapInfoFolder>

      <!-- The output sub-folder for shapefiles created by MapInfo -->
      <ArcGISFolder>
        <value>Shapefiles</value>
      </ArcGISFolder>

      <!-- The output sub-folder into which CSV files will be saved -->
      <CSVFolder>
        <value>CSV</value>
      </CSVFolder>

      <!-- The output sub-folder into which TXT files will be saved -->
      <TXTFolder>
        <value></value>
      </TXTFolder>

      <!-- The schema used in the SQL Server database -->
      <DatabaseSchema>
        <value>dbo</value>
      </DatabaseSchema>

      <!-- The SQL statement used to list all the tables in SQL Server that can be selected
           by the user to extract for each partner -->
      <TableListSQL>
        <value>Select table_name From information_schema.tables Where table_name Like 'LERC[_]Spp[_]%' And table_name Not Like 'LERC[_]Spp[_]%[_]%' Order By table_name</value>
      </TableListSQL>

      <!-- The name of the partner GIS layer in SQL Server used to select the records -->
      <PartnerTable>
        <value>ExtractPolygons</value>
      </PartnerTable>

      <!-- The name of the column in the partner GIS layer containing the partner name passed to SQL
           Server by the tool to use as the partner's boundary for selecting the records -->
      <PartnerColumn>
        <value>PartnerName</value>
      </PartnerColumn>

      <!-- The name of the column in the partner GIS layer containing the abbreviated name passed to
           SQL Server by the tool to use as the sub-folder name for the destination of extracted
           records -->
      <ShortColumn>
        <value>ShortName</value>
      </ShortColumn>

      <!-- The name of the column in the partner GIS layer containing any notes text relating
           to the partner. -->
      <NotesColumn>
        <value>Notes</value>
      </NotesColumn>

      <!-- The name of the column in the partner GIS layer containing the Y/N flag to indicate
           if the partner is currently active.  Only active partners will available for proccessing. -->
      <ActiveColumn>
        <value>Active</value>
      </ActiveColumn>

      <!-- The name of the column in the partner GIS layer containing the GIS format required for
           the output records -->
      <FormatColumn>
        <value>GISformat</value>
      </FormatColumn>

      <!-- The name of the column in the partner GIS layer indicating whether an export should also
           be created as a CSV or TXT file -->
      <ExportColumn>
        <value>Exportformat</value>
      </ExportColumn>

      <!-- The name of the column in the partner GIS layer indicating which SQL table should be
           used for that partner -->
      <SQLTableColumn>
        <value>SQLTable</value>
      </SQLTableColumn>

      <!-- The name of the column in the partner GIS layer indicating which SQL files should be
           created for each partner -->
      <SQLFilesColumn>
        <value>SQLFiles</value>
      </SQLFilesColumn>

      <!-- The name of the column in the partner GIS layer indicating which Map files should be
           created for each partner -->
      <MapFilesColumn>
        <value>MapFiles</value>
      </MapFilesColumn>

      <!-- The name of the column in the partner GIS layer indicating which survey tags, if any
           should be included in the export -->
      <TagsColumn>
        <value>PartnerTags</value>
      </TagsColumn>

      <!-- The name of the column in the partner GIS layer containing the spatial geometry -->
      <SpatialColumn>
        <value>SP_GEOMETRY</value>
      </SpatialColumn>

      <!-- The where clause to determine which partners to display -->
      <PartnerClause>
        <value>Active = "Y"</value>
      </PartnerClause>

      <!-- The options for the selection types -->
      <SelectTypeOptions>
        <value>Spatial Only;Survey Tags Only;Spatial and Survey Tags</value>
      </SelectTypeOptions>

      <!-- The default selection type (1 = spatial, 2 = tags, 3 = both) -->
      <DefaultSelectType>
        <value>3</value>
      </DefaultSelectType>

      <!-- Maximum records in each output; larger outputs are skipped, not truncated -->
      <RecMax>
        <value>10000000</value>
      </RecMax>

      <!-- The default value for zipping the extract files. Leave blank to hide option in dialog. -->
      <DefaultZip>
        <value>No</value>
      </DefaultZip>

      <!-- The SQL criteria for excluding any records (so that these don't appear in the outputs)-->
      <ExclusionClause>
        <value>(CONFIDENTIAL &lt;&gt; 'Y' OR CONFIDENTIAL IS NULL)</value>
      </ExclusionClause>

      <!-- The default value for excluding any records. Leave blank to hide option in dialog. -->
      <DefaultExclusion>
        <value></value>
      </DefaultExclusion>

      <!-- Archive the existing main log before starting a new one? -->
      <DefaultClearLogFile>
            <value>Yes</value>
      </DefaultClearLogFile>

      <!-- By default, should centroids be used for selecting records? Leave blank to hide option in dialog. -->
      <DefaultUseCentroids>
        <value>No</value>
      </DefaultUseCentroids>

      <!-- The path to the Universal Translator program -->
      <UTPath>
        <value>C:\Program Files (x86)\MapInfo\Professional\UT</value>
      </UTPath>

      <!-- The command to run the Universal Translator program -->
      <UTCommand>
        <value>Fme.exe</value>
      </UTCommand>

      <!-- The command to run the EasyLoader program -->
      <EasyLoaderCommand>
        <value>C:\Program Files (x86)\MapInfo\Professional\Tools\EasyLoader.exe</value>
      </EasyLoaderCommand>

      <EasyLoaderQuotes>
        <value>Y</value>
      </EasyLoaderQuotes>

      <!-- The switches to run the EasyLoader program -->
      <EasyLoaderSwitches>
        <value>/E /F /K /P R /Q /Y /NoUI</value>
      </EasyLoaderSwitches>

      <!-- By default, should the EasyLoader program be run? -->
      <DefaultEasyLoader>
            <value>Yes</value>
      </DefaultEasyLoader>

      <SQLTables>
        <AllSpecies>
          <OutputName><value>Species_%partner%_%yyyy%</value></OutputName>
          <OutputType><value></value></OutputType>
          <Columns><value>*</value></Columns>
          <WhereClause><value>RECORDYEAR &gt;= 1985</value></WhereClause>
          <OrderClause><value>ORDER BY SPP_NAME</value></OrderClause>
          <Macro><value></value></Macro>
          <MacroParm><value></value></MacroParm>
          <Symbology>
            <Symbol>
              <Clause><value></value></Clause>
              <Object><value>Point</value></Object>
              <Symbol><value>2,65,16711680,12,"MapInfo Dispersed Groups",0,0</value></Symbol>
            </Symbol>
          </Symbology>
        </AllSpecies>
      </SQLTables>

      <MapTables>
        <AncientWoodland>
          <TableName><value>Ancient_Woodland</value></TableName>
          <OutputName><value>AncientWoodland_%partner%</value></OutputName>
          <OutputType><value></value></OutputType>
          <Columns><value>*</value></Columns>
          <WhereClause><value></value></WhereClause>
          <OrderClause><value></value></OrderClause>
          <Macro><value></value></Macro>
          <MacroParm><value></value></MacroParm>
        </AncientWoodland>
      </MapTables>

    </DataExtractor>
    </configuration>

.. raw:: latex

   \newpage

GNU Free Documentation License
==============================

::

                    GNU Free Documentation License
                     Version 1.3, 3 November 2008
    
    
     Copyright (C) 2000, 2001, 2002, 2007, 2008 Free Software Foundation, Inc.
         <http://fsf.org/>
     Everyone is permitted to copy and distribute verbatim copies
     of this license document, but changing it is not allowed.
    
    0. PREAMBLE
    
    The purpose of this License is to make a manual, textbook, or other
    functional and useful document "free" in the sense of freedom: to
    assure everyone the effective freedom to copy and redistribute it,
    with or without modifying it, either commercially or noncommercially.
    Secondarily, this License preserves for the author and publisher a way
    to get credit for their work, while not being considered responsible
    for modifications made by others.
    
    This License is a kind of "copyleft", which means that derivative
    works of the document must themselves be free in the same sense.  It
    complements the GNU General Public License, which is a copyleft
    license designed for free software.
    
    We have designed this License in order to use it for manuals for free
    software, because free software needs free documentation: a free
    program should come with manuals providing the same freedoms that the
    software does.  But this License is not limited to software manuals;
    it can be used for any textual work, regardless of subject matter or
    whether it is published as a printed book.  We recommend this License
    principally for works whose purpose is instruction or reference.
    
    
    1. APPLICABILITY AND DEFINITIONS
    
    This License applies to any manual or other work, in any medium, that
    contains a notice placed by the copyright holder saying it can be
    distributed under the terms of this License.  Such a notice grants a
    world-wide, royalty-free license, unlimited in duration, to use that
    work under the conditions stated herein.  The "Document", below,
    refers to any such manual or work.  Any member of the public is a
    licensee, and is addressed as "you".  You accept the license if you
    copy, modify or distribute the work in a way requiring permission
    under copyright law.
    
    A "Modified Version" of the Document means any work containing the
    Document or a portion of it, either copied verbatim, or with
    modifications and/or translated into another language.
    
    A "Secondary Section" is a named appendix or a front-matter section of
    the Document that deals exclusively with the relationship of the
    publishers or authors of the Document to the Document's overall
    subject (or to related matters) and contains nothing that could fall
    directly within that overall subject.  (Thus, if the Document is in
    part a textbook of mathematics, a Secondary Section may not explain
    any mathematics.)  The relationship could be a matter of historical
    connection with the subject or with related matters, or of legal,
    commercial, philosophical, ethical or political position regarding
    them.
    
    The "Invariant Sections" are certain Secondary Sections whose titles
    are designated, as being those of Invariant Sections, in the notice
    that says that the Document is released under this License.  If a
    section does not fit the above definition of Secondary then it is not
    allowed to be designated as Invariant.  The Document may contain zero
    Invariant Sections.  If the Document does not identify any Invariant
    Sections then there are none.
    
    The "Cover Texts" are certain short passages of text that are listed,
    as Front-Cover Texts or Back-Cover Texts, in the notice that says that
    the Document is released under this License.  A Front-Cover Text may
    be at most 5 words, and a Back-Cover Text may be at most 25 words.
    
    A "Transparent" copy of the Document means a machine-readable copy,
    represented in a format whose specification is available to the
    general public, that is suitable for revising the document
    straightforwardly with generic text editors or (for images composed of
    pixels) generic paint programs or (for drawings) some widely available
    drawing editor, and that is suitable for input to text formatters or
    for automatic translation to a variety of formats suitable for input
    to text formatters.  A copy made in an otherwise Transparent file
    format whose markup, or absence of markup, has been arranged to thwart
    or discourage subsequent modification by readers is not Transparent.
    An image format is not Transparent if used for any substantial amount
    of text.  A copy that is not "Transparent" is called "Opaque".
    
    Examples of suitable formats for Transparent copies include plain
    ASCII without markup, Texinfo input format, LaTeX input format, SGML
    or XML using a publicly available DTD, and standard-conforming simple
    HTML, PostScript or PDF designed for human modification.  Examples of
    transparent image formats include PNG, XCF and JPG.  Opaque formats
    include proprietary formats that can be read and edited only by
    proprietary word processors, SGML or XML for which the DTD and/or
    processing tools are not generally available, and the
    machine-generated HTML, PostScript or PDF produced by some word
    processors for output purposes only.
    
    The "Title Page" means, for a printed book, the title page itself,
    plus such following pages as are needed to hold, legibly, the material
    this License requires to appear in the title page.  For works in
    formats which do not have any title page as such, "Title Page" means
    the text near the most prominent appearance of the work's title,
    preceding the beginning of the body of the text.
    
    The "publisher" means any person or entity that distributes copies of
    the Document to the public.
    
    A section "Entitled XYZ" means a named subunit of the Document whose
    title either is precisely XYZ or contains XYZ in parentheses following
    text that translates XYZ in another language.  (Here XYZ stands for a
    specific section name mentioned below, such as "Acknowledgements",
    "Dedications", "Endorsements", or "History".)  To "Preserve the Title"
    of such a section when you modify the Document means that it remains a
    section "Entitled XYZ" according to this definition.
    
    The Document may include Warranty Disclaimers next to the notice which
    states that this License applies to the Document.  These Warranty
    Disclaimers are considered to be included by reference in this
    License, but only as regards disclaiming warranties: any other
    implication that these Warranty Disclaimers may have is void and has
    no effect on the meaning of this License.
    
    2. VERBATIM COPYING
    
    You may copy and distribute the Document in any medium, either
    commercially or noncommercially, provided that this License, the
    copyright notices, and the license notice saying this License applies
    to the Document are reproduced in all copies, and that you add no
    other conditions whatsoever to those of this License.  You may not use
    technical measures to obstruct or control the reading or further
    copying of the copies you make or distribute.  However, you may accept
    compensation in exchange for copies.  If you distribute a large enough
    number of copies you must also follow the conditions in section 3.
    
    You may also lend copies, under the same conditions stated above, and
    you may publicly display copies.
    
    
    3. COPYING IN QUANTITY
    
    If you publish printed copies (or copies in media that commonly have
    printed covers) of the Document, numbering more than 100, and the
    Document's license notice requires Cover Texts, you must enclose the
    copies in covers that carry, clearly and legibly, all these Cover
    Texts: Front-Cover Texts on the front cover, and Back-Cover Texts on
    the back cover.  Both covers must also clearly and legibly identify
    you as the publisher of these copies.  The front cover must present
    the full title with all words of the title equally prominent and
    visible.  You may add other material on the covers in addition.
    Copying with changes limited to the covers, as long as they preserve
    the title of the Document and satisfy these conditions, can be treated
    as verbatim copying in other respects.
    
    If the required texts for either cover are too voluminous to fit
    legibly, you should put the first ones listed (as many as fit
    reasonably) on the actual cover, and continue the rest onto adjacent
    pages.
    
    If you publish or distribute Opaque copies of the Document numbering
    more than 100, you must either include a machine-readable Transparent
    copy along with each Opaque copy, or state in or with each Opaque copy
    a computer-network location from which the general network-using
    public has access to download using public-standard network protocols
    a complete Transparent copy of the Document, free of added material.
    If you use the latter option, you must take reasonably prudent steps,
    when you begin distribution of Opaque copies in quantity, to ensure
    that this Transparent copy will remain thus accessible at the stated
    location until at least one year after the last time you distribute an
    Opaque copy (directly or through your agents or retailers) of that
    edition to the public.
    
    It is requested, but not required, that you contact the authors of the
    Document well before redistributing any large number of copies, to
    give them a chance to provide you with an updated version of the
    Document.
    
    
    4. MODIFICATIONS
    
    You may copy and distribute a Modified Version of the Document under
    the conditions of sections 2 and 3 above, provided that you release
    the Modified Version under precisely this License, with the Modified
    Version filling the role of the Document, thus licensing distribution
    and modification of the Modified Version to whoever possesses a copy
    of it.  In addition, you must do these things in the Modified Version:
    
    A. Use in the Title Page (and on the covers, if any) a title distinct
       from that of the Document, and from those of previous versions
       (which should, if there were any, be listed in the History section
       of the Document).  You may use the same title as a previous version
       if the original publisher of that version gives permission.
    B. List on the Title Page, as authors, one or more persons or entities
       responsible for authorship of the modifications in the Modified
       Version, together with at least five of the principal authors of the
       Document (all of its principal authors, if it has fewer than five),
       unless they release you from this requirement.
    C. State on the Title page the name of the publisher of the
       Modified Version, as the publisher.
    D. Preserve all the copyright notices of the Document.
    E. Add an appropriate copyright notice for your modifications
       adjacent to the other copyright notices.
    F. Include, immediately after the copyright notices, a license notice
       giving the public permission to use the Modified Version under the
       terms of this License, in the form shown in the Addendum below.
    G. Preserve in that license notice the full lists of Invariant Sections
       and required Cover Texts given in the Document's license notice.
    H. Include an unaltered copy of this License.
    I. Preserve the section Entitled "History", Preserve its Title, and add
       to it an item stating at least the title, year, new authors, and
       publisher of the Modified Version as given on the Title Page.  If
       there is no section Entitled "History" in the Document, create one
       stating the title, year, authors, and publisher of the Document as
       given on its Title Page, then add an item describing the Modified
       Version as stated in the previous sentence.
    J. Preserve the network location, if any, given in the Document for
       public access to a Transparent copy of the Document, and likewise
       the network locations given in the Document for previous versions
       it was based on.  These may be placed in the "History" section.
       You may omit a network location for a work that was published at
       least four years before the Document itself, or if the original
       publisher of the version it refers to gives permission.
    K. For any section Entitled "Acknowledgements" or "Dedications",
       Preserve the Title of the section, and preserve in the section all
       the substance and tone of each of the contributor acknowledgements
       and/or dedications given therein.
    L. Preserve all the Invariant Sections of the Document,
       unaltered in their text and in their titles.  Section numbers
       or the equivalent are not considered part of the section titles.
    M. Delete any section Entitled "Endorsements".  Such a section
       may not be included in the Modified Version.
    N. Do not retitle any existing section to be Entitled "Endorsements"
       or to conflict in title with any Invariant Section.
    O. Preserve any Warranty Disclaimers.
    
    If the Modified Version includes new front-matter sections or
    appendices that qualify as Secondary Sections and contain no material
    copied from the Document, you may at your option designate some or all
    of these sections as invariant.  To do this, add their titles to the
    list of Invariant Sections in the Modified Version's license notice.
    These titles must be distinct from any other section titles.
    
    You may add a section Entitled "Endorsements", provided it contains
    nothing but endorsements of your Modified Version by various
    parties--for example, statements of peer review or that the text has
    been approved by an organization as the authoritative definition of a
    standard.
    
    You may add a passage of up to five words as a Front-Cover Text, and a
    passage of up to 25 words as a Back-Cover Text, to the end of the list
    of Cover Texts in the Modified Version.  Only one passage of
    Front-Cover Text and one of Back-Cover Text may be added by (or
    through arrangements made by) any one entity.  If the Document already
    includes a cover text for the same cover, previously added by you or
    by arrangement made by the same entity you are acting on behalf of,
    you may not add another; but you may replace the old one, on explicit
    permission from the previous publisher that added the old one.
    
    The author(s) and publisher(s) of the Document do not by this License
    give permission to use their names for publicity for or to assert or
    imply endorsement of any Modified Version.
    
    
    5. COMBINING DOCUMENTS
    
    You may combine the Document with other documents released under this
    License, under the terms defined in section 4 above for modified
    versions, provided that you include in the combination all of the
    Invariant Sections of all of the original documents, unmodified, and
    list them all as Invariant Sections of your combined work in its
    license notice, and that you preserve all their Warranty Disclaimers.
    
    The combined work need only contain one copy of this License, and
    multiple identical Invariant Sections may be replaced with a single
    copy.  If there are multiple Invariant Sections with the same name but
    different contents, make the title of each such section unique by
    adding at the end of it, in parentheses, the name of the original
    author or publisher of that section if known, or else a unique number.
    Make the same adjustment to the section titles in the list of
    Invariant Sections in the license notice of the combined work.
    
    In the combination, you must combine any sections Entitled "History"
    in the various original documents, forming one section Entitled
    "History"; likewise combine any sections Entitled "Acknowledgements",
    and any sections Entitled "Dedications".  You must delete all sections
    Entitled "Endorsements".
    
    
    6. COLLECTIONS OF DOCUMENTS
    
    You may make a collection consisting of the Document and other
    documents released under this License, and replace the individual
    copies of this License in the various documents with a single copy
    that is included in the collection, provided that you follow the rules
    of this License for verbatim copying of each of the documents in all
    other respects.
    
    You may extract a single document from such a collection, and
    distribute it individually under this License, provided you insert a
    copy of this License into the extracted document, and follow this
    License in all other respects regarding verbatim copying of that
    document.
    
    
    7. AGGREGATION WITH INDEPENDENT WORKS
    
    A compilation of the Document or its derivatives with other separate
    and independent documents or works, in or on a volume of a storage or
    distribution medium, is called an "aggregate" if the copyright
    resulting from the compilation is not used to limit the legal rights
    of the compilation's users beyond what the individual works permit.
    When the Document is included in an aggregate, this License does not
    apply to the other works in the aggregate which are not themselves
    derivative works of the Document.
    
    If the Cover Text requirement of section 3 is applicable to these
    copies of the Document, then if the Document is less than one half of
    the entire aggregate, the Document's Cover Texts may be placed on
    covers that bracket the Document within the aggregate, or the
    electronic equivalent of covers if the Document is in electronic form.
    Otherwise they must appear on printed covers that bracket the whole
    aggregate.
    
    
    8. TRANSLATION
    
    Translation is considered a kind of modification, so you may
    distribute translations of the Document under the terms of section 4.
    Replacing Invariant Sections with translations requires special
    permission from their copyright holders, but you may include
    translations of some or all Invariant Sections in addition to the
    original versions of these Invariant Sections.  You may include a
    translation of this License, and all the license notices in the
    Document, and any Warranty Disclaimers, provided that you also include
    the original English version of this License and the original versions
    of those notices and disclaimers.  In case of a disagreement between
    the translation and the original version of this License or a notice
    or disclaimer, the original version will prevail.
    
    If a section in the Document is Entitled "Acknowledgements",
    "Dedications", or "History", the requirement (section 4) to Preserve
    its Title (section 1) will typically require changing the actual
    title.
    
    
    9. TERMINATION
    
    You may not copy, modify, sublicense, or distribute the Document
    except as expressly provided under this License.  Any attempt
    otherwise to copy, modify, sublicense, or distribute it is void, and
    will automatically terminate your rights under this License.
    
    However, if you cease all violation of this License, then your license
    from a particular copyright holder is reinstated (a) provisionally,
    unless and until the copyright holder explicitly and finally
    terminates your license, and (b) permanently, if the copyright holder
    fails to notify you of the violation by some reasonable means prior to
    60 days after the cessation.
    
    Moreover, your license from a particular copyright holder is
    reinstated permanently if the copyright holder notifies you of the
    violation by some reasonable means, this is the first time you have
    received notice of violation of this License (for any work) from that
    copyright holder, and you cure the violation prior to 30 days after
    your receipt of the notice.
    
    Termination of your rights under this section does not terminate the
    licenses of parties who have received copies or rights from you under
    this License.  If your rights have been terminated and not permanently
    reinstated, receipt of a copy of some or all of the same material does
    not give you any rights to use it.
    
    
    10. FUTURE REVISIONS OF THIS LICENSE
    
    The Free Software Foundation may publish new, revised versions of the
    GNU Free Documentation License from time to time.  Such new versions
    will be similar in spirit to the present version, but may differ in
    detail to address new problems or concerns.  See
    http://www.gnu.org/copyleft/.
    
    Each version of the License is given a distinguishing version number.
    If the Document specifies that a particular numbered version of this
    License "or any later version" applies to it, you have the option of
    following the terms and conditions either of that specified version or
    of any later version that has been published (not as a draft) by the
    Free Software Foundation.  If the Document does not specify a version
    number of this License, you may choose any version ever published (not
    as a draft) by the Free Software Foundation.  If the Document
    specifies that a proxy can decide which future versions of this
    License can be used, that proxy's public statement of acceptance of a
    version permanently authorizes you to choose that version for the
    Document.
    
    11. RELICENSING
    
    "Massive Multiauthor Collaboration Site" (or "MMC Site") means any
    World Wide Web server that publishes copyrightable works and also
    provides prominent facilities for anybody to edit those works.  A
    public wiki that anybody can edit is an example of such a server.  A
    "Massive Multiauthor Collaboration" (or "MMC") contained in the site
    means any set of copyrightable works thus published on the MMC site.
    
    "CC-BY-SA" means the Creative Commons Attribution-Share Alike 3.0 
    license published by Creative Commons Corporation, a not-for-profit 
    corporation with a principal place of business in San Francisco, 
    California, as well as future copyleft versions of that license 
    published by that same organization.
    
    "Incorporate" means to publish or republish a Document, in whole or in 
    part, as part of another Document.
    
    An MMC is "eligible for relicensing" if it is licensed under this 
    License, and if all works that were first published under this License 
    somewhere other than this MMC, and subsequently incorporated in whole or 
    in part into the MMC, (1) had no cover texts or invariant sections, and 
    (2) were thus incorporated prior to November 1, 2008.
    
    The operator of an MMC Site may republish an MMC contained in the site
    under CC-BY-SA on the same site at any time before August 1, 2009,
    provided the MMC is eligible for relicensing.
    
    
    ADDENDUM: How to use this License for your documents
    
    To use this License in a document you have written, include a copy of
    the License in the document and put the following copyright and
    license notices just after the title page:
    
        Copyright (c)  YEAR  YOUR NAME.
        Permission is granted to copy, distribute and/or modify this document
        under the terms of the GNU Free Documentation License, Version 1.3
        or any later version published by the Free Software Foundation;
        with no Invariant Sections, no Front-Cover Texts, and no Back-Cover Texts.
        A copy of the license is included in the section entitled "GNU
        Free Documentation License".
    
    If you have Invariant Sections, Front-Cover Texts and Back-Cover Texts,
    replace the "with...Texts." line with this:
    
        with the Invariant Sections being LIST THEIR TITLES, with the
        Front-Cover Texts being LIST, and with the Back-Cover Texts being LIST.
    
    If you have Invariant Sections without Cover Texts, or some other
    combination of the three, merge those two alternatives to suit the
    situation.
    
    If your document contains nontrivial examples of program code, we
    recommend releasing these examples in parallel under your choice of
    free software license, such as the GNU General Public License,
    to permit their use in free software.


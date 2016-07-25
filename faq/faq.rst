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

	The source code as well as the installer setups can be downloaded from GitHub (`MapInfo <https://github.com/LERCAutomation/DataSearches-MapInfo/releases>`_ or `ArcGIS <https://github.com/LERCAutomation/DataSearches--ArcObjects2/releases>`_). Please ensure that you use the correct configuration file, copies of which are included in the :doc:`Appendix <../appendix/appendix>`. An example file is also included with the release.

**Can several people use the tool at the same time?**

	Any number of users can use the tool if they have a copy of the tool installed on their PC. The tool uses all layers that are loaded in the interface in a read-only fashion, and so there is no limit to the number of users of the tool. Where all outputs are written to a central (network) location, it is important to ensure that no two users are running a search on the same search reference at the same time as this can lead to unexpected results. [Andy, we could safeguard against this by allowing for tagging output folders with a %user% tag. That may also help a little with traceability?]

**Does the tool work with QGIS?**

	Currently only ArcGIS and MapInfo implementations of the tool exist. However, if funding was available the tool could be adapted to also support QGIS.

Operating the tool
==================

**One of the data layers I want to use isn't showing in the form. How do I get it to show up?**

	This issue can arise in several ways:

	- The layer isn't loaded in your GIS document. In this case, a `message will pop up <../execute/execute.html#figlaunchwarning>`__ before the form is shown telling you the layer isn't loaded. Add the layer to the GIS and the problem should be resolved.
	- The layer isn't listed in the XML configuration document. Please refer to the :doc:`setup <../setup/setup>` section and add it as a map layer.
	- The map layer is listed in the configuration document, but the `LayerName <../setup/setup.html#layername>`_ is spelled incorrectly. Note that the name is case sensitive and must follow the exact format of the name of the layer in the GIS document.

**I ran a data search twice with different radius settings. The combined sites table only has one set of results**

	When the same search reference is used twice, the combined sites table is overwritten in the second search. Please see the `warning <../execute/execute.html#OverwriteWarning>`_  in the 'Running the Tool' section for details. To avoid this situation occurring, move the results from the first search to a different folder before carrying out the second search.

**I ran a data search twice with different radius settings and included the same data layers. There is only one set of results**

	When the same search reference is used twice, the output from any layers that were included in the first search will be overwritten. Please see the `warning <../execute/execute.html#overwritewarning>`_  in the 'Running the Tool' section for details. To avoid this situation occurring, move the results from the first search to a different folder before carrying out the second search.


Tool issues
===========

**How do I report a new bug or propose a change in the tool?**

	Please check the existing known issues and change requests on the LERCAutomation pages on GitHub (`ArcGIS <https://github.com/LERCAutomation/DataSearches--ArcObjects2/issues>`_, `MapInfo <https://github.com/LERCAutomation/DataSearches-MapInfo>`_) before reporting/proposing new issues or changes. If you have a new issue or request you can submit it there and it will be picked up by the developers. Alternatively, you can email suggestions to `Hester <mailto:Hester@HesterLyonsConsulting.co.uk>`_ or `Andy <mailto:Andy@AndyFoyConsulting.co.uk>`_. 



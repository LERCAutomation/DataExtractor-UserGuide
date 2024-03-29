*******
Preface
*******

The most up to date version of this documentation can be found in **HTML** and **PDF** form on `ReadTheDocs <https://readthedocs.org/projects/dataextractor-userguide/>`_.

.. index::
	single: Recommended user knowledge

Recommended User Knowledge
==========================

Users
-----

This user guide assumes that users of the DataExtractor tool have:

* General IT experience including the use of Microsoft Windows.
* Experience in the use of a relevant GIS application supported by the tool (currently MapInfo and ArcGIS), including selecting and querying features and attributes.
* An understanding of the datasets that are used by the DataExtractor tool.


Administrators
--------------
It is recommended that a person within each organisation is designated as the tool and database administrator. This person should:

* Have an understanding and experience of IT systems management.
* Understand relational database structures.
* Be an expert user of SQL Server.
* Have certified training or equivalent experience in advanced features of the relevant GIS software.
* Become familiar with how the DataExtractor tool has been configured within the organisation.
* Have a good understanding of XML.

.. raw:: latex

   \newpage

.. index::
	single: Reading guide

Reading Guide
=============

This Preface explains a little about the DataExtractor tool, the community of people who develop and use it, and the licensing conditions for using and distributing it. It also explains how to read this user guide.

:doc:`../introduction/introduction` \ explains why the DataExtractor tool is needed, what it does and where it comes from.

:doc:`Anatomy of data extraction <../anatomy/anatomy>` \ is a brief outline of the key stages of data extraction, and how the DataExtractor tool addresses these.

:doc:`Setting up the tool <../setup/setup>` \ describes how to install and set up the DataExtractor tool.

:doc:`Running the tool <../execute/execute>` \ describes how to run the DataExtractor tool.

:doc:`FAQs <../faq/faq>` \ has a list of commonly asked questions and their answers.

:doc:`../appendix/appendix` \ contains examples of the XML configuration files for MapInfo and ArcGIS, lists known issues with the tool and contains a copy of the GNU Free Documentation License v1.3 covering this guide.


.. index::
	single: Licensing

Licensing
=========

The code for the DataExtractor tool is 'open source' and is released under the `GNU General Public License (GPL) v3 <http://www.gnu.org/licenses/gpl.html>`_. Users are free to install it on as many computers as they like, and to redistribute it according to the GPLv3 license.

This guide is released under the `GNU Free Documentation License (FDL) v1.3 <http://www.gnu.org/licenses/fdl.html>`_. Permission is granted to copy, distribute and/or modify this document under the terms of the license.

The tool took a lot of time and money to develop and still requires further development and ongoing support to maintain and enhance it. As a contribution towards this cost there is now a voluntary support fee of £30 for the DataExtractor per organisation per year. Any additional contributions towards costs would also be gratefully received. Enquiries can be made via email to `Andy <mailto:andy@andyfoyconsulting.co.uk>`_.


.. index::
	single: Useful links

Useful links
============

Related community links:

* Administrators: (`MapInfo Installation <https://github.com/LERCAutomation/DataExtractor-MapInfo/releases/>`_) and (`ArcGIS Installation <https://github.com/LERCAutomation/Data-Extractor-ArcObjects/releases>`_) - Release notes and installers.
* Developers (`MapInfo Source Code <https://github.com/LERCAutomation/DataExtractor-MapInfo>`_) and (`ArcGIS Source Code <https://github.com/LERCAutomation/Data-Extractor-ArcObjects>`_)- Source code for the DataExtractor tool.
* Issues (`Known issues for MapInfo and ArcGIS versions <https://trello.com/b/qYhAX0wX/gis-tools-development>`_) - Details of known issues and planned maintenance/enhancements.


.. index::
	single: Acknowledgements

Acknowledgements
================

The DataExtractor tool was developed with funding from:

* Greenspace Information for Greater London CIC
* Thames Valley Environmental Records Centre
* Sussex Biodiversity Records Centre
* Surrey Biodiversity Information Centre

The DataExtractor user guide was developed with additional funding from:
* Dorset Environmental Records Centre
* Isle of Wight Local Records Centre

Many thanks are due to all the LERCs and their staff who have, and continue to, fund and contribute towards the DataExtractor tool.


.. raw:: latex

	\newpage

.. index::
	single: Conventions used in this user guide

Conventions used in this user guide
===================================

The following typographical conventions are used in this manual:

:kbd:`Ctrl-A`
	Indicates a key, or combination of keys, to press.

**Commit**
	Indicates a label, button or anything that appears in user interfaces.

**Tools... --> About**
	Indicates a menu choice, or a combination of menu choices, tab selections or GUI buttons.

:file:`C:\\Program Files (x86)\\MapInfo\\Professional`
	Indicates a filename or directory name.

.. tip::
	Tips can help save time or provide shortcuts.

.. note::
	Notes explain things in more detail or highlight important points.

.. caution::
	Warnings where users should pay attention.


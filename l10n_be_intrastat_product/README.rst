=========================================
Intrastat Product Declaration for Belgium
=========================================

.. 
   !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
   !! This file is generated by oca-gen-addon-readme !!
   !! changes will be overwritten.                   !!
   !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
   !! source digest: sha256:77286cf03d7fe5c34efac30a602baaf600af3d111cc132d64038c62517c174e9
   !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

.. |badge1| image:: https://img.shields.io/badge/maturity-Beta-yellow.png
    :target: https://odoo-community.org/page/development-status
    :alt: Beta
.. |badge2| image:: https://img.shields.io/badge/licence-AGPL--3-blue.png
    :target: http://www.gnu.org/licenses/agpl-3.0-standalone.html
    :alt: License: AGPL-3
.. |badge3| image:: https://img.shields.io/badge/github-OCA%2Fl10n--belgium-lightgray.png?logo=github
    :target: https://github.com/OCA/l10n-belgium/tree/16.0/l10n_be_intrastat_product
    :alt: OCA/l10n-belgium
.. |badge4| image:: https://img.shields.io/badge/weblate-Translate%20me-F47D42.png
    :target: https://translation.odoo-community.org/projects/l10n-belgium-16-0/l10n-belgium-16-0-l10n_be_intrastat_product
    :alt: Translate me on Weblate
.. |badge5| image:: https://img.shields.io/badge/runboat-Try%20me-875A7B.png
    :target: https://runboat.odoo-community.org/builds?repo=OCA/l10n-belgium&target_branch=16.0
    :alt: Try me on Runboat

|badge1| |badge2| |badge3| |badge4| |badge5|

This module implements the Belgian Intrastat reporting.

The report can be reviewed and corrected where needed before
the creation of the XML file for the online declaration (ONEGATE).

More information can be found on the National Bank website:
https://www.nbb.be/en/statistics/foreign-trade

**Table of contents**

.. contents::
   :local:

Installation
============

Conflicting modules
~~~~~~~~~~~~~~~~~~~

This module conflicts with the *account_intrastat* and *l10n_be_intrastat*
modules from the Odoo Enterprise addons.
If you have already installed these modules,
you should uninstall them before installing this module.

Refund handling
~~~~~~~~~~~~~~~

We recommend to also install the OCA stock_picking_invoice_link module,
cf. https://github.com/OCA/stock-logistics-workflow.
This modules establishes a link between invoice lines and stock pickings.
When this module is installed the declaration will take into account refunds created via return pickings.

Configuration
=============

* Accounting -> Configuration -> Settings

  Section Intrastat:

  - Arrivals : Exempt, Standard or Extended
  - Dispatches : Exempt, Standard or Extended
  - Default Intrastat Transport Mode (Required for Extended Declaration)
  - Default Intrastat Region

  Section Customer Invoices:

  - Default Incoterm

|

* Warehouse

  Intrastat Region to cope with warehouses in different regions

|

* Inrastat Codes, Supplementary Units, Transaction Tyoes, Transport Modes, Regions

  Cf. menu Accounting / Configuration / Intrastat

  The configuration data is loaded when installing the module.
  We do not recommend to change these settings.

  A configuration wizard (part of the **intrastat_product** module) also allows to update the
  Intrastat Codes so that you can easily synchronise your Odoo instance with the latest list
  of codes supplied by the configuration wizard.
  (an update is published on an annual basis by the Belgian National Bank).

|

* Product

  You can define a default Intrastat Code on the Product or the Product Category.

|

* Fiscal Positions

  Check your Fiscal Positions and set the 'Intrastat' field for transactions that must be included
  in the intrastat declaration.
  We recommend to set the 'VAT required' flag on the 'Intra Community Regime' Fiscal Position
  for B2B customers.

  If you have B2C customers or B2B customers which are not subject to VAT you can create a
  'Intra Community Regime NA' Fiscal Position on which the 'Intrastat' field is set to B2C
  while the 'VAT required' flag has been turned off.

|

* Partner

  Ensure that your B2B Customer records have a valid VAT Number.

  Consider the use of the OCA **account_fiscal_position_vat_check module** to enforce the correct setting.
  Cf. https://github.com/OCA/account-financial-tools.

Known issues / Roadmap
======================

* The current version of the Belgian Intrastat reporting module is only based on invoices.
  Since associated stock moves are not taken into consideration, it is possible that manual
  corrections are required, e.g.
  Product movements without invoices are not included in the current version
  of this module and must be added manually to the report lines
  before generating the ONEGATE XML declaration.

* Refunds on invoices within the same reporting period are deducted from the declaration lines.
  No controls are executed on Refunds that are not linked to an invoice
  in the same reporting period.
  Such Refunds are reported under the default transaction code for refunds.
  It is recommend to manually set the correct transaction code while Credit Notes
  are created.

* The current version of the Belgian Intrastat reporting module does not perform a
  cross-check with the VAT declaration.

Changelog
=========

This module is also available for olders Odoo versions:

- Odoo 12.0 - 13.0: cf. https://github.com/Noviat/noviat-apps

- Odoo 7.0 - 11.0: cf. https://github.com/luc-demeyer/noviat-apps

Bug Tracker
===========

Bugs are tracked on `GitHub Issues <https://github.com/OCA/l10n-belgium/issues>`_.
In case of trouble, please check there if your issue has already been reported.
If you spotted it first, help us to smash it by providing a detailed and welcomed
`feedback <https://github.com/OCA/l10n-belgium/issues/new?body=module:%20l10n_be_intrastat_product%0Aversion:%2016.0%0A%0A**Steps%20to%20reproduce**%0A-%20...%0A%0A**Current%20behavior**%0A%0A**Expected%20behavior**>`_.

Do not contact contributors directly about support or help with technical issues.

Credits
=======

Authors
~~~~~~~

* Noviat

Contributors
~~~~~~~~~~~~

* Noviat <https://noviat.com>
    * Luc De Meyer <luc.demeyer@noviat.com>
    * Jérémy Didderen <jeremy.didderen@noviat.com>

Maintainers
~~~~~~~~~~~

This module is maintained by the OCA.

.. image:: https://odoo-community.org/logo.png
   :alt: Odoo Community Association
   :target: https://odoo-community.org

OCA, or the Odoo Community Association, is a nonprofit organization whose
mission is to support the collaborative development of Odoo features and
promote its widespread use.

.. |maintainer-luc-demeyer| image:: https://github.com/luc-demeyer.png?size=40px
    :target: https://github.com/luc-demeyer
    :alt: luc-demeyer
.. |maintainer-jdidderen-noviat| image:: https://github.com/jdidderen-noviat.png?size=40px
    :target: https://github.com/jdidderen-noviat
    :alt: jdidderen-noviat

Current `maintainers <https://odoo-community.org/page/maintainer-role>`__:

|maintainer-luc-demeyer| |maintainer-jdidderen-noviat| 

This module is part of the `OCA/l10n-belgium <https://github.com/OCA/l10n-belgium/tree/16.0/l10n_be_intrastat_product>`_ project on GitHub.

You are welcome to contribute. To learn how please visit https://odoo-community.org/page/Contribute.

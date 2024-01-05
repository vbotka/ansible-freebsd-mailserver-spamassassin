========================================================
vbotka.freebsd_mailserver_spamassassin 2.5 Release Notes
========================================================

.. contents:: Topics


2.5.0
=====

Release Summary
---------------
Ansible 2.15 update


Major Changes
-------------
* Add FreeBSD 14.0

Minor Changes
-------------
* Update README
* Remove redundant quotes defaults/main.yml
* sa-update fails when rc>1. rc=1 means download only no ruleset
  update yet.

Bugfixes
--------

Breaking Changes / Porting Guide
--------------------------------

Changelog
=========

All notable changes to this project will be documented in this file.

The format is based on `Keep a Changelog`_,
and this project adheres to `Semantic Versioning`_.

.. _Keep a Changelog: https://keepachangelog.com/en/1.0.0/
.. _Semantic Versioning: https://semver.org/spec/v2.0.0.html

3.0.0 - 2024-07-22
------------------

Changed
~~~~~~~~

* Complete overhaul of the documentation

2.2.0 - 2024-07-08
------------------

Changed
~~~~~~~~

* Update rules.
* Update README.
* Update SonarScanner for Ant.

2.1.0 - 2022-09-22
------------------

Added
~~~~~

* Manage branches for developer edition and above.

Changed
~~~~~~~~

* Add rule that verifies that a NOSONAR tag is followed by an explanation.
* Update rules (add new and remove deprecated ones and erroneous ones).

Fixed
~~~~~

* Fill properties example with dummy information.
* Fix JRE version requirement in README (requires JRE8 or later).

2.0.2 - 2021-08-25
------------------

Fixed
~~~~~

* Fix missing properties in some rules (MicroEJ custom ones).
* Fix docker command line to start the right version of SonarQube.

Changed
~~~~~~~

* Update license.

2.0.1 - 2020-11-19
------------------

Changed
~~~~~~~

* Update README.

2.0.0 - 2020-10-06
------------------

Changed
~~~~~~~

* Server launched manually using Docker.
* Update to SonarQube 8.4.2.
* Simplified analysis and parameterized using a properties file.
* Update rules (add new and modify existing rules severity).

1.2.0 - 2019-02-27
------------------

Removed
~~~~~~~

* Remove source of SonarQube to avoid github limitation.

1.1.0 - 2019-01-18
------------------

Changed
~~~~~~~

* Update to Sonar 5.6.7.
* Update to latest Rules.

Added
~~~~~

* Add process to use sonar on easy ant builds.

1.0.1 - 2017-10-26
------------------

Fixed
~~~~~

* Add Windows-64 in running script.

1.0.0 - 2015-06-15
------------------

* Initial revision.

..
  Copyright 2015-2022 MicroEJ Corp. All rights reserved.
  Use of this source code is governed by a BSD-style license that can be found with this software.

Overview
========

This project presents how to run the SonarQube™ source code quality analyzer on a MicroEJ Java project.
This project installs and runs a local SonarQube server and provides locally a report holding the code inspection.

SonarQube is an open source platform for continuous inspection of code quality. SonarQube offers reports on duplicated code, coding standards, unit tests, code coverage, code complexity, potential bugs, comments and architecture.

SonarQube is available at www.sonarqube.org.

Requirements
------------

- JRE 7 x86 or later.

Project structure
-----------------

- `lib/`: SonarQube client, Ivy, HTTP ant task.
- `rules/`: MicroEJ coding rules.
- `scripts/`: Ant script to run SonarQube analysis.
- `CHANGELOG.rst`.
- `LICENSE.md`.
- `README.rst`.

Usage
-----

Run SonarQube server with Docker
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

- Install Docker following instructions on https://www.docker.com/get-started.
- Install SonarQube on Docker: `docker pull sonarqube:8.4.2-community`
- Run SonarQube instance on Docker: `docker run -d --name mysonar -p 9000:9000 sonarqube`
- Once the Docker container is created, it can be:

  - stopped: `docker container stop mysonar`,
  - and restarted: `docker container start mysonar`.

Install necessary plugins
~~~~~~~~~~~~~~~~~~~~~~~~~

- Go to http://localhost:9000/.
- Log in. By default, the login and password are `admin`.
- Go to `Administration`, `Marketplace`,
- Install the following plugins:

  - Checkstyle (version 8.35 or later),
  - Findbugs (version 4.0.1 or later),
  - PMD (version 3.2.1 or later)

Analysis configuration
~~~~~~~~~~~~~~~~~~~~~~

Open the **scripts/sonarAnalysis.properties** file, edit it to match the project you want to analyze:

- `sonar.projectBaseDir`: path to the project to analyze.
- `sonar.login`: login token for the SonarQube server - https://docs.sonarqube.org/latest/user-guide/user-token/.

Other properties can also be configured. Please refer to the properties file.

Launch an analysis
~~~~~~~~~~~~~~~~~~

- Launch MicroEJ.
- `File->Import->General->Existing project into workspace`: import ExampleTool-Sonar folder.
- Edit the configuration **scripts/sonarAnalysis.properties** as described in the configuration section.
- Right-click on **scripts/sonarAnalysis.ant** `->Run as…->Ant build`.
- The MicroEJ quality profile is automatically added on the server and set as default.
- The analysis report is then available on your SonarQube server. The URL is printed in the console during the analysis in the form: `ANALYSIS SUCCESSFUL, you can browse http://localhost:9000/dashboard?id=[organisation]:[name]`

Execute sonar when building project
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

MicroEJ's build types can execute sonar when being executed. By default the functionality is turned off. To enable it:

- Launch the server.
- In `Window->Preferences->Ant->Runtime`.
- Go to `Properties` tab.
- Remove `skip.sonar` property.
- Add `sonar.host.url` property with the url of your local SonarQube instance (usually http://localhost:9000).
- Add `sonar.login` property with the login token of your local SonarQube instance.

Now when a MicroEJ project is built using EasyAnt (right-click on the project `-> Build with EasyAnt`), the sonar server will be populated.

..  
  Copyright 2015-2020 MicroEJ Corp. All rights reserved.
  Use of this source code is governed by a BSD-style license that can be found with this software.

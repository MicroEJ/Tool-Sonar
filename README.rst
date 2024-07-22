********
Overview
********

This project presents how to run the SonarQube™ source code quality analyzer on a MicroEJ Java project.
It explains how to install and run a local SonarQube server, then how to analyze MicroEJ Java projects with MicroEJ recommended rules.

SonarQube is an open source platform for continuous inspection of code quality. SonarQube offers reports on duplicated code, coding standards, unit tests, code coverage, code complexity, potential bugs, comments and architecture.

SonarQube is available at https://www.sonarsource.com/products/sonarqube/.


************************************
Integrate Sonar analysis to your IDE
************************************

Run SonarQube server with Docker
================================

- Install Docker following the instructions on https://docs.docker.com/engine/install/.
- Pull the SonarQube Docker image: ``docker pull sonarqube:10.6.0-community``.
- Run a SonarQube instance on Docker: ``docker run -d --name sonarqube -e SONAR_ES_BOOTSTRAP_CHECKS_DISABLE=true -p 9000:9000 sonarqube:10.6.0-community``.
- Once your instance is up and running, log in to http://localhost:9000 using System Administrator credentials (admin/admin).

Create your token 
-----------------

- Go to your *Account* > *Security*.
- Create a **User** Token and note it.

Import MicroEJ Quality Profiles
-------------------------------

- Go to *Quality Profiles* > *Restore*.
- Choose the ``MicroEJ_rules.xml`` file from this repository.
- Go to Java profiles and set ``MicroEJ way 2024`` as Default.

Create your project 
-------------------

- Go to *Project* > *Create Projects*.
- Import your project from a DevOps platform or create a local project.

Configure your IDE
==================

You have to install the SonarLint plugin on your IDE and bind your project to the Sonarqube server to be able to use the MicroEJ Quality Profile.

With Eclipse
------------

If you use the SDK 5.x you need to install the Eclipse Marketplace plugin
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
- Go to Help > Install New Software... > Manage...
- Select the line ``https://download.eclipse.org/releases/202x-03`` (2020 or 2022, it depends on the version of SDK installed) and click on *Apply and Close*.
- In the list select *All Available Software*, then select *Marketplace Client* in the category *General Purpose Tools*.
- Click *Next* twice, accept the license then click *Finish*.
- After restarting the IDE, the menu *Eclipse Marketplace* should be available in the Help menu.

Configure Eclipse
^^^^^^^^^^^^^^^^^
- Go to *Eclipse Marketplace*, search and install ``sonarlint``.
- Go to *File* > *New* > *Other…* to open Eclipse's *Select a wizard* menu. Then find *SonarLint* > *New SonarQube/SonarCloud Connection* and select *Next*.
- Select *sonarqube*.
- Provide the URL of your Sonarqube server (http://localhost:9000).
- Select *Token* and paste your Sonar User Token.
- Enter a connection name, then click *Next* and *Finish*.
- Select Projects to bind: select your SDK project and your Sonarqube project.
- Then you can right click on your project and select SonarLint > Analyse.
- The report is available in *SonarLint* Report window.

With VSCode
-----------

- To enable the support for Java analysis, you need the `Language support for Java VSCode extension <https://marketplace.visualstudio.com/items?itemName=redhat.java>`_ (version 0.56.0 or higher).
- Install the `SonarLint extension <https://marketplace.visualstudio.com/items?itemName=SonarSource.sonarlint-vscode>`_.
- Then navigate to the *SONARLINT* > *CONNECTED MODE* view container from the Activity Bar.
- Click on "Add SonarQube connection".
- Enter the URL of your Sonar server (http://localhost:9000), your Sonar User Token and a Connection name.
- Still in the *CONNECTED MODE* view container, add a project binding to your Sonar server project.
- SonarLint for VSCode can now analyze files open in the IDE.

With IntelliJ
-------------

- Go to *Settings* > *Plugins* and search for sonarlint in the Marketplace tab. Select Install. When complete, you must select Restart IDE and confirm the restart to activate the new plugin.
- Go to *Settings* > *Tool* > *SonarLint* > *Settings* and add a new connection to SonarQube.
- Enter a Connection Name.
- Select SonarQube and enter your Sonar server URL (http://localhost:9000).
- Enter your Sonar User Token, click *Next* and *Create*.
- Then go to *Settings* > *Tool* > *SonarLint* > *Project Settings*.
- Check *Bind Project* and select your connection.
- Select your Sonar server project.
- You now analysed your source code with SonarLint and MicroEJ's rules.


***********************************
Run Sonar Scanner and upload report
***********************************

If you want to upload the analysis report to your Sonar server, you need to run Sonar Scanner. We will use the Sonar Scanner Docker image for this, but you can also install Sonar Scanner for your OS here: https://docs.sonarsource.com/sonarqube/latest/analyzing-source-code/scanners/sonarscanner/.

- Create a configuration file in your project's root directory called ``sonar-project.properties``:

.. code-block::

  # must be unique in a given SonarQube instance
  sonar.projectKey=myProject
  sonar.token=<myUserToken>

  # --- optional properties ---

  # defaults to project key
  #sonar.projectName=My project
  # defaults to 'not provided'
  #sonar.projectVersion=1.0
  
  # Path is relative to the sonar-project.properties file. Defaults to .
  #sonar.sources=.
  
  # Encoding of the source code. Default is default system encoding
  #sonar.sourceEncoding=UTF-8

- Launch a Docker container:

.. code-block::

  docker run \
      --rm \
      -e SONAR_HOST_URL="http://${SONARQUBE_URL}"  \
      -v "${YOUR_REPO}:/usr/src" \
      sonarsource/sonar-scanner-cli:10
  
- If the analysis is successful, it is now available on your Sonar server.

    
..  
  Copyright 2015-2024 MicroEJ Corp. All rights reserved.
  Use of this source code is governed by a BSD-style license that can be found with this software.

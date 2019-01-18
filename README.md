# Overview
This project presents how to run the SonarQube™ source code quality analyzer on a MicroEJ Java project.
This project installs and runs a local SonarQube server and provides locally a report holding the code inspection.

SonarQube is a an open source platform for continuous inspection of code quality. SonarQube offers reports on duplicated code, coding standards, unit tests, code coverage, code complexity, potential bugs, comments and architecture.

SonarQube is available at www.sonarqube.org.

### Requirements
- JRE 7 x86 or later.
- MicroEJ 3.0 or later.

### Project structure
- [lib/](lib): SonarQube server & client, HTTP ant task.
- [rules/](rules): MicroEJ coding rules.
- [scripts/](scripts): ant scripts to run SonarQube server and execute analysis.
- [LICENSE.md](LICENSE.md).
- [README.md](README.md).

### Configuration
Open the [sonarAnalysis.ant](scripts/sonarAnalysis.ant) file, edit it to match the project you want to analyze:
- pathelement location,
- sonar.projectName,
- sonar.projectKey,
- sonar.projectVersion.

## Usage
### Launch an analysis
- Launch MicroEJ.
- File->Import->General->Existing project into workspace: import ExampleTool-Sonar folder.
- Edit the configuration ([scripts/sonarAnalysis.ant](scripts/sonarAnalysis.ant)) as described in the configuration section.
- Right-click on [scripts/sonarAnalysis.ant](scripts/sonarAnalysis.ant)->Run as…->Ant build.
- The server is automatically started.
- The report can be viewed at http://localhost:9000/dashboard/ (note: adapt the path to match your project's name if required).

### Launch the server
- Right-click on scripts/sonarServer.ant->Run as…->Ant build.
- All your previous analysis are available at http://localhost:9000/.

<!--
	Markdown
	
	Copyright 2015-2019 IS2T. All rights reserved.
	IS2T PROPRIETARY. Use is subject to license terms.
-->

# Overview
This project presents how to run the SonarQube™ source code quality analyzer on a MicroEJ Java project.
This project installs and runs a local SonarQube server and provides locally a report holding the code inspection.

SonarQube is a an open source platform for continuous inspection of code quality. SonarQube offers reports on duplicated code, coding standards, unit tests, code coverage, code complexity, potential bugs, comments and architecture.

SonarQube is available at www.sonarqube.org.

### Requirements
- JRE 7 x86 or later.
- MicroEJ 3.0 or later.

### Project structure
- `launches/`: Ant analysis launch.
- `lib/`: SonarQube server & client, HTTP ant task.
- `rules/`: MicroEJ coding rules.
- `scripts/`: ant scripts to run SonarQube server and execute analysis.
- `LICENSE.md`.
- `README.md`.

### Configuration
You can either runs the SonarQube analysis on one of the MicroEJ java example (see 1) or one of your Java project (see 2).
1- The provided example assumes the MyMVCSample example Java project is present in the workspace. To do that: File->New->MicroEJ->Java Example-> select any JPF (e.g. STM32F429I-DISCO KickStart) and select MicroUI->MVC example.
2- Open the Example-Sonar/scripts/sonarAnalysis.ant file, edit it to match the project you want to analyze:
- pathelement location,
- sonar.projectName,
- sonar.projectKey,
- sonar.projectVersion.

## Usage
- Launch MicroEJ.
- File->Import->General->Existing project into workspace: import Example-Sonar folder.
- Edit the configuration (/scripts/sonarAnalysis.ant) as described in the configuration section if needed.
- Right-click on scripts/sonarAnalysis.ant->Run as…->Ant build.
- The report can be viewed at http://localhost:9000/dashboard/index/com.is2t:MyMVCSample (note: adapt the path to match your project's name if required).

## Changes
- Initial version.

## License
See the license file 'LICENSE.md' located at the root of this repository.



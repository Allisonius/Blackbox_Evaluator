# Blackbox_Evaluator
This github repo contains the source code to provide an annotated AST of an Evaluator result to highlight the intermediate evaluations the Evaluator discovered on the way to produce the set for an expression or boolean for a formula.

# Requirements:

* Operating Systems
  - Linux (64 bit)
  - Windows 10 (64 bit)

* Dependencies
  - Java 8: Must be installed and accessible from `PATH`.

# Installation:
If you elect to build and compile the Blackbox Evaluator yourself, it is recommended you follow the installation instructions outlined [here](https://github.com/AlloyTools/org.alloytools.alloy) and reproduced below for convenience. Since the Blackbox Evaluator builds on the Analyzer, it requires the user to set up and install the Analyzer's code base.

## Building Alloy

The Alloy build is using a _bnd workspace_ setup using a maven layout. This means it can be build  with Gradle and  the Eclipse IDE for interactive development. Projects are setup to continuously deliver the executable.

### Projects

The workspace is divided into a number of projects:

* [cnf](cnf) – Setup directory. Dependencies are specified in [cnf/central.xml] using the maven POM layout
* [org.alloytools.alloy.application](org.alloytools.alloy.application) – Main application code includes the parser, ast, visualiser, and application code
* [org.alloytools.alloy.dist](org.alloytools.alloy.dist) – Project to create the distribution executable JAR
* [org.alloytools.alloy.extra](org.alloytools.alloy.extra) – Models and examples
* [org.alloytools.pardinus](org.alloytools.pardinus) – A Kodkod extension without native code
* [org.alloytools.kodkod.nativesat](org.alloytools.kodkod.nativesat) – The native code libraries for Kodkod

### Relevant Project files

This workspace uses bnd. This means that the following have special meaning:

* [cnf/build.xml](cnf/build.xml) – Settings shared between projects
* ./bnd.bnd – Settings for a project. This file will _drag_ in code in a JAR.
* [cnf/central.xml](cnf/central.xml) – Dependencies from maven central

### Eclipse

The workspace is setup for interactive development in Eclipse with the Bndtools plugin. Download [Eclipse](https://www.eclipse.org/downloads/) and install it. You can then `Import` existing projects from the Git workspace. You should be asked to install Bndtools from the market place. You can also install Bndtools directly from the [Eclipse Market](https://marketplace.eclipse.org/content/bndtools) place (see `Help/Marketplace` and search for `Bndtools`). 

Bndtools will continuously create the final executable. The projects are setup to automatically update when a downstream project changes.

### IntelliJ IDEA (Ultimate Edition only)

Ensure you have the [Osmorc] plugin is enabled, as this plugin is needed for
Bndtools support. It should be enabled by default.

1. Choose "Import Project"
2. Select the `org.alloytools.alloy` directory.
3. Choose "Import project from external model: Bnd/Bndtools" and click "Next"
4. For "Select Bnd/Bndtools project to import", all projects should be checked
   by default, click "Next"
5. For project SDK, Choose "1.8", Click Finish

Note: do *not* link the Gradle project, as this will prevent you from running
Alloy within IDEA.

To run the Alloy GUI within IDEA, navigate to
org.alloytools.alloy.application/src/main/java/edu/mit/csail/sdg/alloy4whole/SimpleGUI and run the SimpleGUI class.

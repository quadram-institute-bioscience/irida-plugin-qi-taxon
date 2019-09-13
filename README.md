# IRIDA QI Taxon Plugin

This project contains a read classification pipeline implemented as a plugin for the [IRIDA][] bioinformatics analysis system. 

# Workflow

![workflow.png][]  

# Required Galaxy tools

* testtoolshed.g2.bx.psu.edu/repos/jdv/centrifuge/centrifuge/1.0.3
* irida.corefacility.ca/galaxy-shed/repos/irida/bundle_collections/bundle_collection/1.0.2

# Building/Packaging

Building and packaging this code is accomplished using [Apache Maven][maven]. However, you will first need to install 
[IRIDA][] to your local Maven repository. The version of IRIDA you install will have to correspond to the version found 
in the `irida.version.compiletime` property in the [pom.xml][] file of this project. Right now, this is IRIDA version 
`19.09-SNAPSHOT`.

## Installing IRIDA to local Maven repository

To install IRIDA to your local Maven repository please do the following:

1. Clone the IRIDA project

```bash
git clone https://github.com/phac-nml/irida.git
cd irida
```

2. Checkout appropriate version of IRIDA

```bash
git checkout 19.09-SNAPSHOT
```

3. Install IRIDA to local repository

```bash
mvn clean install -DskipTests
```

## Building the plugin

Once you've installed IRIDA as a dependency, you can proceed to building this plugin. Please run the following commands:

```bash
cd irida-plugin-qi-taxon

mvn clean package
```

Once complete, you should end up with a file `target/qi-taxon-0.1.0-SNAPSHOT.jar` which can be installed as a plugin to IRIDA.

If you have previously [setup IRIDA][irida-setup] before you may copy this JAR file to `/etc/irida/plugins` and restart IRIDA.  The plugin should now show up in the **Analyses > Pipelines** section of IRIDA.

You should be able to run a pipeline with this plugin and get analysis results. And, you should be able to save and view 
these results in the IRIDA metadata table.


# Dependencies

The following dependencies are required in order to make use of this plugin.

* [IRIDA][] >= 0.23.0
* [Java][] >= 1.8 and [Maven][maven] (for building)



[maven]: https://maven.apache.org/
[IRIDA]: http://irida.ca/
[Galaxy]: https://galaxyproject.org/
[Java]: https://www.java.com/
[irida-pipeline]: https://irida.corefacility.ca/documentation/developer/tools/pipelines/
[irida-pipeline-galaxy]: https://irida.corefacility.ca/documentation/developer/tools/pipelines/#galaxy-workflow-development
[irida-wf-ga2xml]: https://github.com/phac-nml/irida-wf-ga2xml
[pom.xml]: pom.xml
[workflows-dir]: src/main/resources/workflows
[workflow-structure]: src/main/resources/workflows/0.1.0/irida_workflow_structure.ga
[example-plugin-java]: src/main/java/ca/corefacility/bioinformatics/irida/plugins/ExamplePlugin.java
[irida-plugin-java]: https://github.com/phac-nml/irida/tree/development/src/main/java/ca/corefacility/bioinformatics/irida/plugins/IridaPlugin.java
[irida-updater]: src/main/java/ca/corefacility/bioinformatics/irida/plugins/ExamplePluginUpdater.java
[irida-setup]: https://irida.corefacility.ca/documentation/administrator/index.html
[properties]: https://en.wikipedia.org/wiki/.properties
[messages]: src/main/resources/workflows/0.1.0/messages_en.properties
[maven-min-pom]: https://maven.apache.org/guides/introduction/introduction-to-the-pom.html#Minimal_POM
[pf4j-start]: https://pf4j.org/doc/getting-started.html
[workflow.png]: doc/images/workflow.png
# AEM Sling Pipes Configurations/Layouts/Recipes

This project contains [Apache Sling Pipes](https://sling.apache.org/documentation/bundles/sling-pipes.html) configurations for Adobe Experience Manager. These configurations could potentially be useful for an AEM project. Hopefully they'll at least be helpful examples what can be done with Sling Pipes.

## Configurations

Remove all macOS/OS X `.DS_Store` and `._.DS_Store` files from the `/content` folder which may have been added through WebDAV or another process:

    curl -u admin:admin -X POST http://localhost:4502/etc/pipes/removeDsStore.json

Get a list of Pages from `/content` that are missing the `jcr:content` child resource:

    curl -u admin:admin -F size=-1 http://localhost:4502/etc/pipes/getPagesWithoutPageContent.json

More to come...

## Install Dependencies

### Sling Pipes

Download Sling Pipes: [org.apache.sling.pipes-0.0.10.jar](http://central.maven.org/maven2/org/apache/sling/org.apache.sling.pipes/0.0.10/org.apache.sling.pipes-0.0.10.jar).

### Sling Query

Download Sling Query: [org.apache.sling.query-3.0.0.jar](http://central.maven.org/maven2/org/apache/sling/org.apache.sling.query/3.0.0/org.apache.sling.query-3.0.0.jar).

### Install

Install the downloaded JAR files into your running AEM instance: [http://localhost:4502/system/console/bundles](http://localhost:4502/system/console/bundles).

## How to build

To build all the modules run in the project root directory the following command with Maven 3:

    mvn clean install

If you have a running AEM instance you can build and package the whole project and deploy into AEM with

    mvn clean install -PautoInstallPackage

Or to deploy it to a publish instance, run

    mvn clean install -PautoInstallPackagePublish

Or alternatively

    mvn clean install -PautoInstallPackage -Daem.port=4503

## Maven settings

The project comes with the auto-public repository configured. To setup the repository in your Maven settings, refer to:

    http://helpx.adobe.com/experience-manager/kb/SetUpTheAdobeMavenRepository.html
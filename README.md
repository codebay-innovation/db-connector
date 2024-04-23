# Issue repository
This is the main repository for report issues related with the Codebay AEM "DB Connector"
# DB Connector [![Codebay Innovation](https://www.codebay-innovation.com/components-auto-generator/codebay_logo.png)](https://www.codebay-innovation.com/)

## Introduction

This product allows you to make queries into a database that was previously configured by a driver in the AEM instance. 

The type of queries that can be executed are the following: 

- Select queries 

- Delete queries 

- Insert queries	 

- Update queries 

## Installation

### Local instance

To install the current product on a local instance, you can directly install the provided package using the package manager.

### Cloud instance

To install the current product on a cloud instance, you need to include the package on your project, and install it through the deployment pipeline. Follow the next steps to install the DB Connector:

1. Create a new “resources” folder inside your ui.apps module.

2. Add the connector package provided inside the “resources” folder.

3. Add the following dependency on the dependencyManagement section of your main POM.xml
``` xml 
    <dependency>
        <groupId>com.codebay</groupId>
        <artifactId>db-connector</artifactId>
        <version>1.0.0</version>
        <type>zip</type>
        <scope>system</scope>
        <systemPath>${project.basedir}/ui.apps/src/main/resources/db-connector-1.0.0.zip</systemPath>
    </dependency>
```
4. Add the dependency in your POM.xml file of module “all”.
```xml
    <dependency>
        <groupId>com.codebay</groupId>
        <artifactId>db-connector</artifactId>
        <type>zip</type>
        <scope>system</scope>
        <systemPath>${project.basedir}/../ui.apps/src/main/resources/db-connector-1.0.0.zip</systemPath>
    </dependency>
```
5. Add the connector package as embedded dependency in “embeddeds” section of your POM.xml file of module “all”.
```xml
    <plugin>
        <groupId>org.apache.jackrabbit</groupId>
        <artifactId>filevault-package-maven-plugin</artifactId>
        <extensions>true</extensions>
        <configuration>
            ...
            <embeddeds>
                ...
                <embedded>
                    <groupId>com.codebay</groupId>
                    <artifactId>db-connector</artifactId>
                    <type>zip</type>
                    <target>/apps/codebay-db-connector-vendor-package/application/install</target>
                </embedded>
                ...
            </embeddeds>
            ...
        </configuration>
    </plugin>
```
6. Add a filter for the connector package on your filter.xml file of module “all”.
```xml
    <workspaceFilter version=”1.0”>
        ...
        <filter root=”/apps/codebay-db-connector-vendor-package/application/install”/>
        ...
    </workspaceFilter>
```
## How to use it:

1. Go to the “Tools” of AEM and go to “Codebay-Innovation” tab, click on "DB Connector".

2. Configure your desired options to the behavior of the queries.

3. Execute the queries like a traditional database.

## Available Configuration Options

- Read Mode Only: Allows you to execute only read queries.

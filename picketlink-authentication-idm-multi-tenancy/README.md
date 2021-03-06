picketlink-authentication-idm-multi-tenancy: PicketLink Multi-Tenancy Example
===============================
Author: Pedro Igor
Level: Intermediate
Technologies: CDI, PicketLink, JSF
Summary: Basic example that demonstrates how to use multi-tenancy using PicketLink with a JSF view layer
Source: <https://github.com/picketlink/picketlink-quickstarts/>


What is it?
-----------

This example demonstrates the use of *PicketLink* and *Identity Management (IdM) with Multi-Tenancy* in *JBoss Enterprise Application Platform 6* or *WildFly*.

Multi-tenancy allows an application to be used equally but separately across different clients, or tenants.  PicketLink supports identity data partitioning where each tenant has its own data that is separated and protected from others. This is a critical requirement for Cloud-based/SaaS applications that serve many different clients and users.

This application provides a multi-tenancy architecture and security model for accessing different companies and their resources.
Each company maps to a single realm, from where resources and identity data are located and isolated from each other.
Each realm has its own resources and security policies and is not accessible to users of another realms.

The application provides a login page where you can sign in from different companies. Each company has its own
directory where its resources are located.

    src/
        main/
            webapp/
                companies/
                    acme/
                    umbrella/
                    wayne/

Users from one company, or realm, can not have access to the directory or resources from another company. This authorization
logic is provided by the `org.jboss.as.quickstarts.picketlink.idm.multitenancy.jsf.RealmProtectionFilter`, which is a
simple `@WebFilter`.

The latest PicketLink documentation is available [here](http://docs.jboss.org/picketlink/2/latest/).


System requirements
-------------------

All you need to build this project is Java 6.0 (Java SDK 1.6) or better, Maven 3.0 or better.

The application this project produces is designed to be run on JBoss Enterprise Application Platform 6 or WildFly.

 
Configure Maven
---------------

If you have not yet done so, you must [Configure Maven](http://www.jboss.org/jdf/quickstarts/jboss-as-quickstart/#configure_maven) before testing the quickstarts.


Start JBoss Enterprise Application Platform 6 or WildFly with the Web Profile
-------------------------

1. Open a command line and navigate to the root of the JBoss server directory.
2. The following shows the command line to start the server with the web profile:

        For Linux:   JBOSS_HOME/bin/standalone.sh
        For Windows: JBOSS_HOME\bin\standalone.bat

 
Build and Deploy the Quickstart
-------------------------

_NOTE: The following build command assumes you have configured your Maven user settings. If you have not, you must include Maven setting arguments on the command line. See [Build and Deploy the Quickstarts](../README.md#build-and-deploy-the-quickstarts) for complete instructions and additional options._

1. Make sure you have started the JBoss Server as described above.
2. Open a command line and navigate to the root directory of this quickstart.
3. Type this command to build and deploy the archive:

        For EAP 6:     mvn clean package jboss-as:deploy
        For WildFly:   mvn -Pwildfly clean package wildfly:deploy

4. This will deploy `target/picketlink-authentication-idm-multi-tenancy.war` to the running instance of the server.


Access the application 
---------------------

The application will be running at the following URL: <http://localhost:8080/picketlink-authentication-idm-multi-tenancy>. 


Undeploy the Archive
--------------------

1. Make sure you have started the JBoss Server as described above.
2. Open a command line and navigate to the root directory of this quickstart.
3. When you are finished testing, type this command to undeploy the archive:

        For EAP 6:     mvn jboss-as:undeploy
        For WildFly:   mvn -Pwildfly wildfly:undeploy


Run the Quickstart in JBoss Developer Studio or Eclipse
-------------------------------------
You can also start the server and deploy the quickstarts from Eclipse using JBoss tools. For more information, see [Use JBoss Developer Studio or Eclipse to Run the Quickstarts](../README.md#use-jboss-developer-studio-or-eclipse-to-run-the-quickstarts) 


Debug the Application
------------------------------------

If you want to debug the source code or look at the Javadocs of any library in the project, run either of the following commands to pull them into your local repository. The IDE should then detect them.

        mvn dependency:sources
        mvn dependency:resolve -Dclassifier=javadoc

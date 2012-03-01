# JBoss Diagnostic Reporter

The JBoss Diagnostic Reporter (JDR, pronounced like 'jitter') is an AS7 subsystem built to collect useful information and documents to aid in troubleshooting. The types of information gathered by JDR includes:

* configuration files
* log files
* deployment information
* runtime information (so long as AS7 is running during collection)

# Executing JDR

There are two ways to execute JDR currently:

1. via the AS7 administration interface using jboss-cli.sh
2. via the jdr.sh script in $JBOSS_HOME/bin

### via the administration interface

The operation used to invoke JDR depends on the operation mode of AS7.

In standalone mode:

    /subsystem=jdr/:generate-jdr-report

In domain mode:

    /host=$host/server=$server/subsystem=jdr/:generate-jdr-report

### via jdr.sh

    $JBOSS_HOME/bin/jdr.sh

The script will prompt you for administration credentials if necessary.

# What do the reports look like?

    JBOSSHOME/standalone/configuration/standalone-ha.xml
    JBOSSHOME/standalone/configuration/standalone-full.xml
    JBOSSHOME/standalone/configuration/standalone_xml_history/standalone.initial.xml
    JBOSSHOME/standalone/configuration/standalone_xml_history/standalone.boot.xml
    JBOSSHOME/standalone/configuration/standalone_xml_history/standalone.last.xml
    JBOSSHOME/standalone/configuration/logging.properties
    JBOSSHOME/standalone/configuration/standalone.xml
    JBOSSHOME/standalone/configuration/application-users.properties
    JBOSSHOME/standalone/configuration/standalone-full-ha.xml
    JBOSSHOME/standalone/configuration/application-roles.properties
    JBOSSHOME/domain/configuration/host-master.xml
    JBOSSHOME/domain/configuration/host.xml
    JBOSSHOME/domain/configuration/logging.properties
    JBOSSHOME/domain/configuration/application-users.properties
    JBOSSHOME/domain/configuration/application-roles.properties
    JBOSSHOME/domain/configuration/domain.xml
    JBOSSHOME/domain/configuration/host-slave.xml
    JBOSSHOME/standalone/log/boot.log
    JBOSSHOME/standalone/log/server.log
    sos_strings/as7/configuration.json
    sos_strings/as7/dump-services.json
    sos_strings/as7/cluster-proxies-configuration.json
    sos_strings/as7/threaddump.json
    sos_strings/as7/jarinfo.txt
    sos_strings/as7/jboss_home_tree.txt
    sos_reports/sos.html
    sos_reports/sos.txt
    version.txt
    sos_logs/sos.log
    sos_logs/ui.log

* Files copied from the system are placed beneath `JBOSSHOME`.
* Files generated from runtime commands are placed beneath sos_strings/as7/
* Simple text and html reports are placed under sos_reports
* sos_logs contains logfiles that pertain the execution of sosreport itself

# jarinfo.txt

    JBOSSHOME/modules/org/w3c/css/sac/main/sac-1.3.jar
    eb04fa63fc70c722f2b8ec156166343b
    Manifest-Version: 1.0
    Created-By: 1.2.2 (Blackdown Java-Linux Team)

    JBOSSHOME/modules/org/yaml/snakeyaml/main/snakeyaml-1.8.jar
    59099d0b410dc146e7e76375ad260dcd
    Manifest-Version: 1.0
    Archiver-Version: Plexus Archiver
    Created-By: Apache Maven
    Built-By: somov
    Build-Jdk: 1.5.0_19

### format:

    path/to/jar
    md5 checksum
    manifest
    \n

# jboss_home_tree.txt

    /home/jjaggars/workspace/jboss-as/build/target/jboss-as-7.1.1.Final-SNAPSHOT
    [user group 4.0K]       +-- appclient
    [user group 4.0K]       |   +-- configuration
    [user group 7.0K]       |       +-- appclient.xml
    [user group 2.0K]       |       +-- logging.properties
    [user group 4.0K]       +-- bin
    [user group 1.9K]       |   +-- add-user.bat
    [user group 2.0K]       |   +-- add-user.sh
    [user group 2.5K]       |   +-- appclient.bat
    [user group 1.9K]       |   +-- appclient.conf
    [user group 2.6K]       |   +-- appclient.conf.bat
    [user group 3.6K]       |   +-- appclient.sh
    [user group 4.0K]       |   +-- client
    [user group 3.2M]       |   |   +-- jboss-client.jar
    [user group 1.5K]       |   |   +-- README.txt
    [user group 3.5K]       |   +-- domain.bat
    [user group 2.7K]       |   +-- domain.conf
    [user group 3.4K]       |   +-- domain.conf.bat
    [user group 8.0K]       |   +-- domain.sh
    [user group 4.0K]       |   +-- init.d
    [user group 3.6K]       |   |   +-- jboss-as-standalone.sh
    [user group 369]        |   |   +-- jboss-as.conf
    ...

# Deployments

Each deployment will be represented by a deployment_name.txt file under sos_strings/as7

    META-INF/MANIFEST.MF:127
    META-INF/maven/org.jboss.as.quickstarts/jboss-as-helloworld/pom.properties:137
    META-INF/maven/org.jboss.as.quickstarts/jboss-as-helloworld/pom.xml:4219
    WEB-INF/beans.xml:289
    WEB-INF/classes/org/jboss/as/quickstarts/helloworld/HelloService.class:678
    WEB-INF/classes/org/jboss/as/quickstarts/helloworld/HelloWorldServlet.class:1749
    index.html:144

### format:

    path/to/file:size in bytes

Be aware that empty folders are not captured.

# Questions?

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

From $JBOSS_HOME execute bin/jdr.sh. The script will prompt you for administration credentials if necessary.

# What do the reports look like?

The report is a zip file containing a fairly simple directory structure:

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

* contains name, md5sum, and manifest for every AS7 system jar
* name\nmd5sum\nmanifest\n\n is the format

# jboss_home_tree.txt

This is a tree-like representation of $JBOSS_HOME

# Deployments

* Each deployment will be represented by a deployment_name.txt file under sos_strings/as7
* The contents of the text file will be a file listing of the internals of the deployment

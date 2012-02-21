# JBoss Diagnostic Reporter

The JBoss Diagnostic Reporter (JDR, pronounced like 'jitter') is an AS7 subsystem built to collect useful information and documents to aid in troubleshooting. The types of information gathered by JDR includes:

* configuration files
* log files
* deployment information
* runtime information (so long as AS7 is running during collection)

\pagebreak

# Executing JDR

There are two ways to execute JDR currently:

1. via the AS7 administration interface using jboss-cli.sh
2. via the jdr.sh script in $JBOSS_HOME/bin

\pagebreak

### via the administration interface

The operation used to invoke JDR depends on the operation mode of AS7.

In standalone mode:

    /subsystem=jdr/:generate-jdr-report

In domain mode:

    /host=$host/server=$server/subsystem=jdr/:generate-jdr-report

\pagebreak

### via jdr.sh

From $JBOSS_HOME execute bin/jdr.sh. The script will prompt you for administration credentials if necessary.

\pagebreak

### What do the reports look like?

The report is a zip file containing a fairly simple directory structure:

    File Name                                             Modified             Size
    sosreport-localhost.localdomain-20120209102909/JBOSSHOME/standalone/configuration/standalone-ha.xml 2012-02-09 10:21:36        19763
    sosreport-localhost.localdomain-20120209102909/JBOSSHOME/standalone/configuration/standalone-full.xml 2012-02-09 10:21:36        20405
    sosreport-localhost.localdomain-20120209102909/JBOSSHOME/standalone/configuration/standalone_xml_history/standalone.initial.xml 2012-02-09 10:28:42        15090
    sosreport-localhost.localdomain-20120209102909/JBOSSHOME/standalone/configuration/standalone_xml_history/standalone.boot.xml 2012-02-09 10:28:42        15090
    sosreport-localhost.localdomain-20120209102909/JBOSSHOME/standalone/configuration/standalone_xml_history/standalone.last.xml 2012-02-09 10:28:42        15090
    sosreport-localhost.localdomain-20120209102909/JBOSSHOME/standalone/configuration/logging.properties 2012-02-09 10:21:34         2042
    sosreport-localhost.localdomain-20120209102909/JBOSSHOME/standalone/configuration/standalone.xml 2012-02-09 10:21:36        15090
    sosreport-localhost.localdomain-20120209102909/JBOSSHOME/standalone/configuration/application-users.properties 2012-02-09 10:21:34          813
    sosreport-localhost.localdomain-20120209102909/JBOSSHOME/standalone/configuration/standalone-full-ha.xml 2012-02-09 10:21:36        24668
    sosreport-localhost.localdomain-20120209102909/JBOSSHOME/standalone/configuration/application-roles.properties 2012-02-09 10:21:34          787
    sosreport-localhost.localdomain-20120209102909/JBOSSHOME/domain/configuration/host-master.xml 2012-02-09 10:21:34         1799
    sosreport-localhost.localdomain-20120209102909/JBOSSHOME/domain/configuration/host.xml 2012-02-09 10:21:34         2931
    sosreport-localhost.localdomain-20120209102909/JBOSSHOME/domain/configuration/logging.properties 2012-02-09 10:21:34         1976
    sosreport-localhost.localdomain-20120209102909/JBOSSHOME/domain/configuration/application-users.properties 2012-02-09 10:21:34          813
    sosreport-localhost.localdomain-20120209102909/JBOSSHOME/domain/configuration/application-roles.properties 2012-02-09 10:21:34          787
    sosreport-localhost.localdomain-20120209102909/JBOSSHOME/domain/configuration/domain.xml 2012-02-09 10:21:34        73128
    sosreport-localhost.localdomain-20120209102909/JBOSSHOME/domain/configuration/host-slave.xml 2012-02-09 10:21:34         2019
    sosreport-localhost.localdomain-20120209102909/JBOSSHOME/standalone/log/boot.log 2012-02-09 10:28:42         7363
    sosreport-localhost.localdomain-20120209102909/JBOSSHOME/standalone/log/server.log 2012-02-09 10:29:00         2640
    sosreport-localhost.localdomain-20120209102909/sos_strings/as7/configuration.json 2012-02-09 10:29:16        36825
    sosreport-localhost.localdomain-20120209102909/sos_strings/as7/dump-services.json 2012-02-09 10:29:16        48635
    sosreport-localhost.localdomain-20120209102909/sos_strings/as7/cluster-proxies-configuration.json 2012-02-09 10:29:16          172
    sosreport-localhost.localdomain-20120209102909/sos_strings/as7/threaddump.json 2012-02-09 10:29:16        76890
    sosreport-localhost.localdomain-20120209102909/sos_strings/as7/jarinfo.txt 2012-02-09 10:29:16       393362
    sosreport-localhost.localdomain-20120209102909/sos_strings/as7/jboss_home_tree.txt 2012-02-09 10:29:16       125919
    sosreport-localhost.localdomain-20120209102909/sos_reports/sos.html 2012-02-09 10:29:16        11240
    sosreport-localhost.localdomain-20120209102909/sos_reports/sos.txt 2012-02-09 10:29:16         5799
    sosreport-localhost.localdomain-20120209102909/version.txt 2012-02-09 10:29:16           32
    sosreport-localhost.localdomain-20120209102909/sos_logs/sos.log 2012-02-09 10:29:14         3322
    sosreport-localhost.localdomain-20120209102909/sos_logs/ui.log 2012-02-09 10:29:16          643

* Files copied from the system are placed beneath `JBOSSHOME`.
* Files generated from runtime commands are placed beneath sos_strings/as7/
* Simple text and html reports are placed under sos_reports
* sos_logs contains logfiles that pertain the execution of sosreport itself


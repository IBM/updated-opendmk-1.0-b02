# updated-opendmk-1.0-b02 
OpenDMK package updated for Java versions above Java 8 - Clone of Betfair OpenDMK

Given the lack of an opendmk binary in a central repo, this work builds upon that of
[nickman](https://github.com/nickman/OpenDMK) to provide such a binary, albeit under a different groupId,
such that it doesn't clash should the main project one day publish their own artifact.

The latest (and only) released version is 1.0-b02, available in the
[Maven Central repository](http://repo1.maven.org/maven2/com/betfair/net/java/opendmk/).

The original code is released under and governed by either the GNU General Public License, Version 2 only (GPL) or
the Common Development and Distribution License (CDDL), and so this project chooses to run under the same
[dual license](https://opendmk.java.net/legal_notices/licenses.txt).

The acsp-opendmk edition has modified to use the IBM CCC internal GitHub repository and artifactory, and bound
to the git repository <https://github.ibm.com/cccc/acsp-opendmk>.

## JMX Remote Optional with Messaging Protocol

An optional part of the JMX Remote API, which is not included in the Java SE platform, is a generic connector. This connector can be configured by adding pluggable modules to define the following:

- The transport protocol used to send requests from the client to the server, and to send responses and notifications from the server to the clients
- The object wrapping for objects that are sent from the client to the server and whose class loader can depend on the target MBean

The JMX Messaging Protocol (JMXMP) connector is a configuration of the generic connector where the transport protocol is based on TCP and the object wrapping is native Java serialization. Security is more advanced than for the RMI connector. Security is based on the Java Secure Socket Extension (JSSE), the Java Authentication and Authorization Service (JAAS), and the Simple Authentication and Security Layer (SASL).

The generic connector and its JMXMP configuration are optional, which means that they are not always included in an implementation of the JMX Remote API. The Java SE platform does not include the optional generic connector.

This project is based on the implementation of the OpenDMK project that has been discontinued and disappeared. Some bugs have been fixed and is actually used in production for several years without any issue.

The version hosted suffered from several issues that have been fixed. It is used in an actual production environment flawlessly since several years.

You can find a clone of the original Open DMK project here <https://github.com/betfair/opendmk> since the original repository opendmk.java.net no longer exists.

Note! This project  is a local clone of the above mentioned <https://github.com/betfair/opendmk> project, to be able to locally debug the code for troubleshooting.


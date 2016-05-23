# Ladok Integration
The new Ladok integration component is the use of the generic Java based components for communication with new Ladok in a OSGi-based runtime environment using Apache Camel as routing specification. The component act as an adapter for a message channel.  

![alt text](https://raw.githubusercontent.com/uppsala-university/ladok-integration/master/docs/ladok-atom-adapter.png "Ladok integration component")

The adapter consumes events from the new Ladok ATOM feeds and put each event as a separate message in a message channel. The adapter is implemented from the [idempotent receiver pattern](http://www.enterpriseintegrationpatterns.com/patterns/messaging/IdempotentReceiver.html) to prevent that events are processed more than once. The log database, which the idempotency is based on, is also used as source for reading the last consumed message.

## Dependencies
Ladok integration depends on common-integration and ladok projects. They are available on github:

https://github.com/uppsala-university


## Build
Build the respective projects (common-integration, ladok, and ladok-integration) using maven:

    mvn install


## Deploy in Karaf/Servicemix
Karaf has the ability to load features and OSGi bundles either by dropping them in the deploy folder or by
logging in to the Karaf shell and deploying them by a set of deploy commands.

Karaf will look for bundles and features referenced by a 'mvn:'-url in the local maven repository and in any
additional repositories specified in $SERVICEMIX_HOME/etc/org.ops4j.pax.url.mvn.cfg.

To deploy the Ladok Integration features and bundles, in Karaf/Servicemix shell type the following commands:

    repo-add mvn:se.sunet.ati.integration.ladok/ladok-integration-packaging-karaf/1.0.0-SNAPSHOT/xml/features
    feature:install ladok-atom-adapter

Or, drop ladok-integration/ladok-integration-packaging-karaf/target/classes/features.xml in $SERVICEMIX_HOME/deploy/


## Configuration
Karaf reads property files in $KARAF\_HOME/etc/, so to add runtime properties needed in the OSGi bundles
copy the property file ladok-integration-packaging-karaf/se.sunet.ati.integration.ladok.cfg to $KARAF\_HOME/etc/
and update with appropriate values.


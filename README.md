# Ladok Integration
The new Ladok integration component is the use of the [generic Java based components for communication with new Ladok](https://github.com/uppsala-university/ladok) in an OSGi-based runtime environment using Apache Camel as routing specification. The component act as an adapter for a message channel.  

![alt text](https://raw.githubusercontent.com/uppsala-university/ladok-integration/master/docs/ladok-atom-adapter.png "Ladok integration component")

The adapter consumes events from the new Ladok ATOM feeds and put each event as a separate message in a message channel. The adapter is implemented from the [idempotent receiver pattern](http://www.enterpriseintegrationpatterns.com/patterns/messaging/IdempotentReceiver.html) to prevent that events are processed more than once. The log database, which the idempotency is based on, is also used as source for reading the last consumed message.

## Dependencies
Ladok integration depends on common-integration and ladok projects. They are available on github:

https://github.com/uppsala-university


## Build
Build the respective projects (common-integration, ladok, and ladok-integration) using maven:

    mvn install

## Deploy in Karaf/Servicemix
Deployment is bound to the execution enviroment. For deployment in a Karaf/ServiceMix environment read the [Karaf deployment documentation](https://github.com/uppsala-university/ladok-integration/tree/master/ladok-integration-packaging-karaf).

## Configuration
Karaf reads property files in $KARAF\_HOME/etc/, so to add runtime properties needed in the OSGi bundles
copy the property file ladok-integration-packaging-karaf/se.sunet.ati.integration.ladok.cfg to $KARAF\_HOME/etc/
and update with appropriate values.


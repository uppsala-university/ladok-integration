# Application Packaging for Karaf
Karaf has the ability to load features and OSGi bundles either by dropping them in the deploy folder or by
logging in to the Karaf shell and deploying them by a set of deploy commands.

![alt text](https://raw.githubusercontent.com/uppsala-university/ladok-integration/master/docs/ladok-atom-adapter-deployment.png "Ladok Integration component deployment")

Karaf will look for bundles and features referenced by a 'mvn:'-url in the local maven repository and in any
additional repositories specified in $KARAF\_HOME/etc/org.ops4j.pax.url.mvn.cfg.

## Configuration
Copy the property file se.sunet.ati.integration.ladok.cfg to $KARAF_HOME/etc/ and update with appropriate values.

## Build
    mvn install

## Deploy
To deploy the Ladok Integration features and bundles, in Karaf/ServiceMix shell type the following commands:

    repo-add mvn:se.sunet.ati.integration.ladok/ladok-integration-packaging-karaf/1.0.0-SNAPSHOT/xml/features
    feature:install ladok-atom-adapter

Or, drop ladok-integration/ladok-integration-packaging-karaf/target/classes/features.xml in $KARAF_HOME/deploy/
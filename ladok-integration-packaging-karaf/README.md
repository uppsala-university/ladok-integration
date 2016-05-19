Application Packaging for Karaf
===============================

Features XML for Application Packaging in Karaf:


Configuration
-------------

Copy the property file se.sunet.ati.integration.ladok.cfg to $KARAF_HOME/etc/ and update with appropriate values.


Build
-----

    mvn install


Deploy
------

In Karaf/Servicemix shell:

	repo-add mvn:se.sunet.ati.integration.ladok/ladok-integration-packaging-karaf/1.0.0-SNAPSHOT/xml/features
	feature:install ladok-atom-adapter

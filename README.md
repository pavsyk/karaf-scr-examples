Karaf SCR Examples
---------------------------

These Examples are used for sully6768's SCR Components with Karaf Articles:

http://sully6768.blogspot.com/2012/09/scr-components-with-karaf.html

-----------

Updated for OSGi 4.3 / Karaf 2.3.3. New versions of other libraries and tools.

-----------

How To:
---------

* JAVA_HOME to JDK 1.7 directory
* MAVEN_HOME to mvn 3.1.1 directory
* both JAVA_HOME\\bin and MAVEN_HOME\\bin should be on PATH (replace the environment variables with values)
* run:

	```sh
mvn install
	```

* install the SCR to Karaf, e.g.:

	```sh
bin\karaf
osgi:install -s  mvn:org.apache.felix/org.apache.felix.scr/1.8.0
	```

* copy one of built JARs to the Karaf's "deploy" directory, e.g. org.apache.karaf.scr.examples.managed.service-2.3.3.jar
* in the Karaf's shell (for the managed services example):

	```sh
scr:list
# you can see the both components unsatisfied
config:edit ManagedGreeterService
config:propset salutation "Hello"
config:propset name "Pavel"
config:update
scr:list
# now you can see the both components active 
	```

* see the log file, if the components works (Ctrl+C to stop showing the log):

	```sh
log:tail
	```

* delete the configuration and check that the components are deactivated and uninstalled

	```sh
config:delete ManagedGreeterService
log:tail
scr:list
	```

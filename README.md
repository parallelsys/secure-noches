# secure-noches
Here you will find a list of default and custom firewalld xml's.

This xml files (OS Dependent) will go on firewalld non-standard definitions.

OS Dependent because location can change IE: Centos, Fedora, RHEL tracks custom xml's under: /etc/firewalld/services/

This is also a good place to track custom created definitions.

From firewalld Docs:

Copy a file in the services directory in /etc/firewalld

As root copy the file:

cp myservice.xml /etc/firewalld/services  

#
From firewalld Docs  
After you have copied the file into /etc/firewalld/services it takes about 5 seconds till the new service will be visible in firewalld.
Place a file in the services directory in /usr/lib/firewalld

This is the way how a package or system service could add a new service to firewalld. The benefit of placing the service into /usr/lib/firewalld/services is that the admin or user is able to modify the service and that he could go back to the original service easily by loading the defaults of the service. Then the by firewalld created and modified copy in /etc/firewalld/services will be renamed to <service>.xml.old and the original service in /usr/lib/firewalld/services will be used again. The original service will be effective in the runtime environment only after a reload.

A package that places a service in the /usr/lib/firewalld/services directory should require the firewalld package or sub package that is providing the path. In an RPM based distribution that is using or that bases on the firewalld provided spec file this package is firewalld-filesystem.

For more information please visit: [firewalld](https://firewalld.org/documentation/howto/add-a-service.html)  
#

After you place your xml file in to the correct directory execute:

firewall-cmd --reload

After you do that you can run:

firewall-cmd --get-services

And look for your added service.

Now you can proceed to enable the service and test:

firewall-cmd --zone=yourzonehere --add-service=rooncore 

Note: that you can run firewall-cmd --add-service=rooncore and it will add the service to your default running zone.

Once you add your service and test you and verify it works as expected than you can proceed to make the change permanent...

firewall-cmd --zone=publicweb --add-service=rooncore --permanent

Note: The firewalld-default folder is the default services from Fedora 28.

Done.

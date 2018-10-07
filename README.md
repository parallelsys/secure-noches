# secure-noches
Here you will find a list of created firewalld xml's.

This xml files (OS Dependent) will go on firewalld non-standard definitions.

IE: Centos, Fedora, RHEL are located in: /etc/firewalld/services/

This is also a good place to track custom created definitions.

After you place your xml file in to the correct directory execute:

firewall-cmd --reload

After you do that you can run:

firewall-cmd --get-services

And look for your added service.

Now you can proceed to enable the service and test:

firewall-cmd --zone=yourzonehere --add-service=rooncore 

Note: that you can run firewall-cmd --add-service=rooncore and it will add the service to your default running zone.

Once you add your service and test you and verify it works as expected than you can proceed to make the change permanent...

firewall-cmd --zone=publicweb --add-service=ssh --permanent

Done.

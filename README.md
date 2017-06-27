# Traffic management demonstration

This application is a good way to demonstrate tying multiple containers into a cohesive application. It simulates transport management software, identifying where all the gps enabled vehicles for a 
company are located on the roads. By clicking each 'vehicle' you are shown their location (via google street view). You can easily scale the amount of 'traffic' on the map, by scaling up 
the GPS simulator container deployment.

There are 5 services that make up the application:

Gps simulator (Virtual GPS sensor)
Database (Mongo DB)
UI (Angular front end)
Binary Data server (takes the GPS data and inserts it into the DB)
Data server (aggregates all the gps co-ordinates from the DB and sends the co-ordinates via sockets to the UI)

The source for all of these is available [here] (https://github.com/hpepanda/fleet-mgmt) , and all credit for the code goes to this user.. I have simply built docker images for these components  
and parameterised some of the variables (eg the lat and lon of the desired map location).

This has been packaged into a helm chart for easy deployment to Kubernetes.  

# Installing  
Edit the values.yaml file, and change the required settings.
Eg, to change the location of the map from Auckland, New Zealand to Los Angeles, USA change the below:  
```latitude:  -36.8485
longtitude: 174.7633```  
  
to :  
  
```latitude: 34.0522
longtitude: 118.2437```
  
Please note that this assumes you have an ingress controller set up. You will need to change the annotation in the values file to your preferred ingress controller.  
Also, you will need to change the ingress hostnames to something that works for you.  



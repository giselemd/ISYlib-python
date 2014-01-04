ISYlib-python
=============

Simple Python lib for the ISY home automation netapp Supporting a Simple and OO interface
 
  
The Goal / design concept is to provide a fast and simple to use  interface 
   
   Providing both object oriented and procedural methods
	
    Caching system state for fast operation my avoiding  excessive device queries 
   ( Supports real time cache updating by optionally running a sub-thread subscribing to event stream ) 

----


This is a work in progress ( so expect new features )

nodes, programs and iay  vars can be controled with ia objects or call methods.

Get and print the status for the node called "Garage Light"
 
    import ISY
    myisy = ISY.Isy(addr="admin", userp="admin, userl="isy")
 
    garage_light = myisy.get_node("Garage Light")
 
    print "Node {:} is {:}".format(garage_light.name, garage_light.formatted)
 
 
--
 
Get an object that represents the node called "Garage Light"
and turn it off if it is on
 
    import ISY
    myisy = ISY.Isy()
 
    garage_light = myisy.get_node("Garage Light")
    if garage_light :
        garage_light.off()


--
 
Alternately you can obtain a Node's object by indexing
a Isy obj my the node name or address
 
    import ISY
    myisy = ISY.Isy()
    myisy["Garage Light"].off()

 
 on 50% :
 
    garage_light = myisy["Garage Light"]
    garage_light.on(128)
    
 or without node device objs

    myisy.node_comm("Garage Light", "on", 128)

list all nodes and scenes and their status :

    pfmt = "{:<22} {:>12}\t{:<12}{!s:<12}"
    print(pfmt.format("Node Name", "Address", "Status", "Enabled"))
    print(pfmt.format("---------", "-------", "------", "------"))
    for nod in isy :
        if nod.objtype == "scene" :
            print(pfmt.format(nod.name, nod.address, "-", "-", ))
        else :
            print(pfmt.format(nod.name, nod.address, nod.formatted, nod.enabled, ))
   
see also : http://www.universal-devices.com/residential/
	   http://wiki.universal-devices.com/index.php?title=Main_Page
	   
NOTE: This Libaray is not written my or supported by universal devices
		



ISYlib-python Documentation
---------------------------
[This needs to be updated]

* [Using_Isy_Class]  (/docs/Using_Isy_Class.txt) This is the main class that used to represent the ISY device iitself

* [Using_IsyNode_Class]  (/docs/Using_IsyNode_Class.txt) This class is used to represent and control individual Nodes ( aka: 

* [Using_IsyVar_Class]  (/docs/Using_IsyVar_Class.txt)




![img_3369 1](https://cloud.githubusercontent.com/assets/19006/10417242/56eb1770-7002-11e5-9081-f511a432c876.png)

#FruityMesh

The [FruityMesh](https://github.com/mwaylabs/fruitymesh) project is under active development at [M-Way Solutions GmbH](http://www.mwaysolutions.com/), Germany.

#This repo

This *clone* of [FruityMesh](https://github.com/mwaylabs/fruitymesh) is for learning purposes and does not aspire to be a fork of [FruityMesh](https://github.com/mwaylabs/fruitymesh).

##Goal

The goal was to use the Ping example as an introduction to mesh programming using the FruityMesh framework. The exercise is to have a module control an RGB LED to reflect its node's proximity to other nodes.

The LED is dimmed when disconnected from other nodes and turns green when its signal strength is high, orange when medium and red when low.

##Implementation

The LED is connected to GPIOs 18, 19 and 20. PingModule was added to the project and modified to support the Timer Tick callback, to check signal strength every second.

Using simple arithmetic, it changes the LED's colours based on the node's signal strength with its neighbours.

![ezgif com-optimize](https://cloud.githubusercontent.com/assets/19006/10417277/df09c7a4-7003-11e5-94cc-f0ff5cafa608.gif)

##Modified makefile

The [makefile](https://github.com/ihassin/fruitymesh-ping/blob/master/makefile) is slightly different than the [one contributed](https://github.com/tkadom/fruitymesh) by my colleague [Tim Kadom](https://www.linkedin.com/in/tkadom) in that it adds the Ping module and a goal to flash the device.

##Modified Ping Module

The original PingModule was adapted [here](https://github.com/ihassin/fruitymesh-ping/blob/master/src/modules/PingModule.cpp).

The highlights of the changes are:

* Include NRF GPIO support
* Initialise GPIOs and timer values in ```PingModule::ConfigurationLoadedHandler```
* Implement the ```PingModule::TimerEventHandler``` method to send a ping to other nodes in broadcast mode.
* Modified the ```PingModule::ConnectionPacketReceivedEventHandler``` method to control the LED's colours based on the absolute value of the sum of the RSSI values for all neighbouring nodes.
 
#Up and running

You are welcome to [use my VM setup](https://github.com/ihassin/fruitymesh-ubuntu-vm) to quickly bring up a complete NRF51/FruityMesh development up and running to experiment with this exciting platform.

#Other efforts

* [Tim's repo](https://github.com/tkadom/fruitymesh)
* [Rosalie's repo](https://github.com/rosatolen/fruitymesh)
* [Andy's repo](https://github.com/microcosm/fruitygate-nodejs) - Showcasing a gateway between meshes.

#Contributing

* Fork it (https://github.com/ihassin/fruity-ping/fork)
* Create your feature branch (git checkout -b my-new-feature)
* Commit your changes (git commit -am 'Add some feature')
* Push to the branch (git push origin my-new-feature)
* Create a new Pull Request


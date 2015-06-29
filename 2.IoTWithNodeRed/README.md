Internet of Things with Intel Edison
=======

Intel Edison is a tiny computer, developed by Intel. This computer can be connected in wifi, so it's a great tool to work on the **Internet of Things** (or IoT).

![Intel Edison](http://www.seeedstudio.com/depot/images/102990161%201.jpg)

> This tutorial is written using Linux x64


##  Node-RED##
###  Installation###

IBM's Node-RED visual coding tools are simplifying the job of wiring up today's world of computers, sensors and online services.

Hacking the world around you to bend it to your will is getting easier and easier.

Whether it's setting up a lamp to flash when someone retweets you or a system to text you when the washing's done, work is taking place to make it simpler for machine to speak unto machine. Hooking up the wealth of computers, sensors and online services in the modern world can lead to weird and wonderful creations

[More information](http://www.techrepublic.com/article/node-red/)

NodeRed allows you to create some applications related to the web. With this, your board can do some researches on different websites, send some emails, SMS or even tweets. You can literally do everything with this library, in particularly by creating your own components.
More informations [here](http://nodered.org/).

To install Node-RED, run ;

  ```sh
    npm install -g node-red
    node-red
```

Then type :

```
    ifconfig
```

And get the IP adress of your board. You can now use node-RED in your navigator by typing this adress in the search bar, with the 1880 port. (ex : 192.168.1.147:1880 for me)

###  Read an analog input###

We've seen how to read an analog value with the MRAA library. This is useful, but not as much as Node-RED !
With Node-RED, we can also read any analog sensor value, but we can use these values to create web applications !

> I'm now following another tutorial, you can find it [here](http://www.rs-online.com/designspark/electronics/eng/blog/wiring-the-internet-of-things-with-intel-edison-and-node-red).

First, I encourage you to learn how to use Node-RED, this shouldn't be very complicated.
You can use [this tutorial.](http://nodered.org/docs/getting-started/first-flow.html) It will show you how to create your firsts applications (or "flows") with Node-RED.

Once you've done that, we can start talking seriously ! ;-)

To read analog values with Node-RED, you need to download a now node.

Download these [two files.](https://github.com/abopen/node-red/tree/master/nodes)

Place them in the following directory : ***/usr/lib/node_modules_node-red/nodes***

Start (or restart) Node-RED.
You should now see a new node on the sidebar, named **"mraaAnalogRead"**. This node will allow you to read any analog value of any analog sensor plugged on your board.

#Using MQTT broker. 

Try to send this data to your broker using Node-Red

 

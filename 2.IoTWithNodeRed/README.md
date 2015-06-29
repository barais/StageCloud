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

##  First flow ##
To create your first flow, 


1. Add an Inject node

The Inject node allows you to inject messages into a flow, either by clicking the button on the node, or setting a time interval between injects.

Drag one onto the workspace from the palette.

Open the sidebar (Ctrl-Space, or via the dropdown menu) and select the Info tab.

Select the newly added Inject node to see information about its properties and a description of what it does.

2. Add a Debug node

The Debug node causes any message to be displayed in the Debug sidebar. By default, it just displays the payload of the message, but it is possible to display the entire message object.

3. Wire the two together

Connect the Inject and Debug nodes together by dragging between the output port of one to the input port of the other.

4. Deploy

At this point, the nodes only exist in the editor and must be deployed to the server.

Click the Deploy button. Simple as that.

With the Debug sidebar tab selected, click the Inject button. You should see numbers appear in the sidebar. By default, the Inject node uses the number of milliseconds since January 1st, 1970 as its payload. Let’s do something more useful with that.

5. Add a Function node

The Function node allows you to pass each message though a JavaScript function.

Wire the Function node inbetween the Inject and Debug nodes. You’ll need to delete the existing wire (select it and hit delete on the keyboard).

Double-click on the Function node to bring up the edit dialog. Copy the follow code into the function field:

```js
// Create a Date object from the payload
var date = new Date(msg.payload);
// Change the payload to be a formatted Date string
msg.payload = date.toString();
// Return the message so it can be sent on
return msg;
```


Click Ok to close the edit dialog and then click the deploy button.

Now when you click the Inject button, the messages in the sidebar will be more readable time stamps.

### Source

The flow created in this example is represented by the following json. It can be imported straight into the editor by pasting the json into the Import dialog (Ctrl-I or via the dropdown menu).

```json
[{"id":"58ffae9d.a7005","type":"debug","name":"","active":true,"complete":false,"x":640,"y":200,"wires":[]},{"id":"17626462.e89d9c","type":"inject","name":"","topic":"","payload":"","repeat":"","once":false,"x":240,"y":200,"wires":[["2921667d.d6de9a"]]},{"id":"2921667d.d6de9a","type":"function","name":"Format timestamp","func":"// Create a Date object from the payload\nvar date = new Date(msg.payload);\n// Change the payload to be a formatted Date string\nmsg.payload = date.toString();\n// Return the message so it can be sent on\nreturn msg;","outputs":1,"x":440,"y":200,"wires":[["58ffae9d.a7005"]]}]
```


### Read an analog input###

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

Try to send this data to your broker using Node-Red, 

Create two flows, the first one will serve to send data to MQTT broker. The second one will be used to receive message and send an email. 

#Using azure service bus

* [Documentation to configure azure](https://azure.microsoft.com/fr-fr/documentation/articles/service-bus-nodejs-how-to-use-topics-subscriptions/)
* [Documentation to configure azure](https://azure.microsoft.com/fr-fr/documentation/articles/service-bus-nodejs-how-to-use-queues/)
* [Node-Red with Azure](https://github.com/ppatierno/azure-nodes)


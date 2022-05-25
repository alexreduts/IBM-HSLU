# 3 - Exercise: Simple IoT App

<img src={require('@site/static/img/Clipboard_2022-05-02-11-14-33.png').default} />

:::caution
- One Node-RED Application is running on the RaspberryPi
- The other Node-RED Application runs on the IBM Cloud
- They communicate with each other using HTTP protocol
:::

## The RaspberryPi Part
### Create Node-RED App on RPi
Instead of running our Node-RED App in the cloud you can also run it on a RaspberryPi for example. This mini computers have become quite powerful and are used for a lot of stuff nowadays. The next step show you how to do this

1. Open the terminal on your computer and connect to your RPi with the following SSH command:
```bash
ssh pi@TJxx.simple.eee.intern
password: raspberry
```

2. Open Node-RED with the following command:
```bash
node-red start
```
:::note
We already installed Node-RED for you on this devices to save you some hustle. But if you like to use Node-RED on your own RaspberryPi just download it following the Guide on the Node-RED website.
:::

3. Open your internetbrowser and navigate to the Node-RED Editor:
```
http://TJxx.simple.eee.intern:1880/
```
:::info
Again, the RaspberryPi is hosting the Node-RED App. But you can access it from any devices browser which is currently in the same local network
:::

4. Create a new Flow/Canvas by pressing "+"

<img src={require('@site/static/img/Clipboard_2022-05-23-16-05-29.png').default} />


### Create the Node-RED Program
The architecture of our Node-RED program can be explained rather simple. It only needs four components or nodes as they are called in Node-RED. The first node gives a trigger, that start one run of our programm with a preset intervall. Then we use a node that simple runs a terminal command on the raspberry pi. This command extracts the CPU Temperature. Then we just need a http node to send our data to the Cloud. Finally it is good practice to add a debug node at the end to check, what the http node is sending. But this is not strictly neccessary.

<img src={require('@site/static/img/Clipboard_2022-05-23-16-06-28.png').default} />

**Connection to the Cloud**:
Have a look at the URL of your partner Node-RED app in his browser

BaseURL: https://Host.Domain 
Example: https://node-red-rt2.eu-gb.mybluemix.net/

Endpoints ("http in" node): BaseURL/Endpoint
Example:
- Endpoint = /data
- Full URL = https://node-red-rt2.eu-gb.mybluemix.net/data


## The IBM Cloud Part
On the Cloud all of you already created a Node-Red App. The task remaining is creating Node-RED flow or you could say writing the actual program.

### Creating the Node-RED Flow on the IBM Cloud
This program has a little bit more to it than the one on the Raspi. Http node -> receive data, http response, function to parse the information, debug node and dashboard

<img src={require('@site/static/img/Clipboard_2022-05-23-16-16-41.png').default} />
<img src={require('@site/static/img/Clipboard_2022-05-23-16-16-16.png').default} />
<img src={require('@site/static/img/Clipboard_2022-05-23-16-15-56.png').default} />
<img src={require('@site/static/img/Clipboard_2022-05-23-16-15-39.png').default} />



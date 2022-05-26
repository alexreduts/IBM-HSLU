# 3 - Exercise: Simple IoT App

<img src={require('@site/static/img/Clipboard_2022-05-02-11-14-33.png').default} />

:::danger
Please read this next few sentence very carefully!!! You do this exercise ideally in groups of two but of course you can do it alone or with more people. With two people one person does **Part 1** and the other **Part 2**.

**Part 1** of the exercise is about accessing an RaspberryPi (a mini Computer) and then creating a programm locally with a Node-RED instance also running locally on the Raspi. This program simply runs a command in on the Raspi to read its CPU temperatur every second and then sends it to the cloud.

**Part 2** is about using our Node-RED service on the IBM Cloud to create an other program. This one should then receive the CPU temperatur from the Raspi and create a dashboard to visualize the evlution of the CPU temperatur.
:::

## Part 1: RaspberryPi
### Step 1: Create Node-RED App on RPi
Instead of running our Node-RED App in the cloud you can also run it on a RaspberryPi for example. This mini computers have become quite powerful and are used for a lot of stuff nowadays. The next step show you how access the Raspi and start a Node-RED instance.

1. Open the terminal on your computer and connect to your RPi with the following SSH command:
```bash
ssh pi@TJxx.simple.eee.intern
password: raspberry
```

2. Open Node-RED with the following command:
```bash
node-red start
```
:::info
We already installed Node-RED for you on this devices to save you some hustle. But if you like to use Node-RED on your own RaspberryPi just download it following the Guide on the Node-RED website.
:::

3. Open your internetbrowser and navigate to the Node-RED Editor:
```
http://TJxx.simple.eee.intern:1880/
```
:::caution
Again, the RaspberryPi is hosting the Node-RED App. But you can access it from any devices browser which is currently in the same local network
:::

4. Create a new Flow/Canvas by pressing "+"

<img src={require('@site/static/img/Clipboard_2022-05-23-16-05-29.png').default} />


### Step 2: Create the Node-RED flow
The architecture of our Node-RED program can be explained rather simple. It only needs four components or nodes as they are called in Node-RED.

**The inject node**: It is the first node of the flow and triggers once started your programm to rerun in a preset intervall.
- Payload: ```timestamp```
- Topic: leave empty, and don't check box.
- Repeat: ```interval```, ```3```, ```seconds```
- Name: ```Set measure intervall```

**The exec node**: This node simply runs a terminal command on the RaspberryPi. This command reads the CPU Temperature.
- Command: ```vdcgencmd measure_temp | cut -c6-9```
- Append: don't check msg.payload box and leave extra input parameters empty.
- Output: ```when the command is compilete - exec mode```
- Timeout: leave empty
- Name: ```Read Raspi CPU Temperature```
- **Note**: The exec node has multiple connections, you need to use the top one as it is the output.

**The http request node**: The http node sends the measured CPU temperature to a specified location on the Internet. We gonna send it to your partners IBM Cloud Node-RED service. For that you need to figure out the host address of your partners IBM Cloud Node-RED service. Just check his App URL on the IBM Cloud and than add ```/data``` at the end. Your URL should look like http://159.122.179.33:32223/data just with different numbers.
- Method: ```POST```
- URL: ```Your URL```
- Return: ```a paresd JSON object````
- Name: ```HTTP Send```

**The debug node**: Finally, it is good practice to add a debug node at the end to check what the http node is sending and receiving. But this is not strictly neccessary for your programm to work.

<img src={require('@site/static/img/Clipboard_2022-05-23-16-06-28.png').default} />


## Part 2: IBM Cloud
On the Cloud all of you already created a Node-Red App. The task remaining is creating a Node-RED flow or you could say writing the actual program.

### Creating the Node-RED Flow on the IBM Cloud

**The http in node**:
- Method: ```POST```
- URL: ```/data```
- Name: ```HTTP Receive```

**The function node**:
- Name: ```String parsing````
- Function: add the following code
  ```
  const temp = parseFloat(msg.payload);
  msg.payload = temp;
  return msg;
  ```

**The http reponse node**:
- Leave at it is.

<img src={require('@site/static/img/Clipboard_2022-05-23-16-16-41.png').default} />
<p></p>

**The chart node**: The chart not is used to visualize our CPU measurements on the Raspberry Pi over time. It is not yet installed. See on the Node-RED Getting Started documentation on how to install new nodes or just have a look at the image below.

<img src={require('@site/static/img/Clipboard_2022-05-23-16-16-16.png').default} />

After the installation process you can now add the chart node to your flow and configure it.

- Group: Click on edit symbol
  - Name: ```Raspi CPU temperature [C]```
  - Tab: Click on edit symbol
    - Name: ```Home```
    - Icon: ```dashboard```
    - State: Enabled
    - Nav. Menu: Enabled
  - Width: ```15```
  - Display groupe name: Check this box.
  - Allow group to be collapsed: Don't check this box.
- Size: ```auto````
- Label: ```CPU temp```
- Type: ```Line chart```, don't check "enlarge points"
- X-axis: last ```1```, ```hours``` OR ```1000```
- X-axis Label: ```HH:mm:ss```, don't check "as UTC"
- Y-axis: leave min and max empty
- Legend: ```None```, Interpolate: ```linear```
- Blank label: leave empty
- Name: ```CPU Temp. Chart```

<img src={require('@site/static/img/Clipboard_2022-05-23-16-15-56.png').default} />
<img src={require('@site/static/img/Clipboard_2022-05-23-16-15-39.png').default} />


**The debug node**: Finally, it is good practice to add a debug node at the end to check what the http node is sending and receiving. But this is not strictly neccessary for your programm to work.


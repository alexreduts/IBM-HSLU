# 1 - IBM Cloud Getting Started

## Step 1: Get access to IBM Cloud
To use any kind of public cloud resources you will need to register yourself at a public cloud provider. This is very similar wheter you chose Amazon, Google, Microsoft or IBM as your cloud provider. For security reasons, everyone needs to be identified and the simplest way to do this is forcing new user to register with a credit card. But luckely for students there is an other solution.

1. Register for the IBM Academic Initiative with your university issued email. Just follow the instructions given on the website.
<https://www.ibm.com/academic/home>

2. As soon as you are registred and loged in. Navigate to "Topics" -> "IBM Cloud". Scroll down a little until you see multiple boxes giving information to further resources. Choose the "Software" tab and then open "IBM Cloud Feature Code". Now you only need to click on "Request Feature Code" and then copy it. Open the other link "How to create your IBM Cloud trial account" in a new tab as well, you will need it.

3. Follow "How to Create an IBM Cloud Account" guide on GitHub. If you haven't opened it in the previous step. You can find it with the following link:
<https://github.com/academic-initiative/documentation/blob/main/academic-initiative/how-to/How-to-create-an-IBM-Cloud-account/readme.md>

## Step 2: Navigating the IBM Cloud UI
Now, that you have access to the IBM Cloud you should get to know where you can find what. There are not many places you really need to know. Just navigate once to all the places listed below and make sure you know how to get there. There will be references to this places throughout this documentation.

- ```Manage -> Account -> Account Settings```: Your "Account Type" should be "Trial (Free)"
- ```Navigation Menu (top left corner) -> Resource List```: Most important place, here you see all the services you have created.
- ```Catalog & Search Bar```: Place where you can find / search for available services

## Step 3: Create a service on the IBM Cloud
Finally, we show you how to create your own application running on the IBM Cloud. We do this by example, as the process can be different depending on the type of application you wanna build. We show you how to run a Node-RED App (more about Node-RED later) on the Cloud.

### What service can you use for free?
All the services associated to the Free and Lite plan can be used for free with a Trial account. See more on <https://mycatalog.mybluemix.net/> (Filter for "Free" and "Lite")

### Creating a deployment target
Before we can create our Node-RED service we need to configure some platform where we can run this service on. We gonna use the 30-day free kubernetes cluster.

1. Navigate to ```Navigation Menu -> Kubernetes -> Create Cluster```
2. Pricing Plan: Chose ```Free```
3. Cluster name: Something like ```K8s-Name-Surname```
4. Leave the rest as it is and click ```Create```
5. Now it will take a while for the cluster to be setup in the datacenter. Thus you can move on to the next task.

<details>
  <summary>What is a "Kubernetes Cluster"?</summary>
  <markdown>
  Open Source container platform. 
  </markdown>
</details>

<details>
  <summary>What does "K8s" mean?</summary>
  <markdown>
  K8s is just a commenly used abbriviation for "Kubernetes". 
  </markdown>
</details>

### Creating a Node-RED App
We will now create our service, the Node-RED App.

1. Navigate to the ```Search Bar``` and search for ```Node-RED App```
2. Check that you are in the ```Create-Tab``` in the Web UI
3. App name: Something like ```Node-RED-Name-Surname```
4. You can leave Resource group and Tags as they are
5. Region: Chose ```Frankfurt```.
6. Leave Resource Group as ```Default```.
7. Set Pricing plan as ```Lite```.
8. Let's ```Create```. Be pationed as the Cloudant database is provisioned.

<details>
  <summary>What is Cloudant and why do we need it?</summary>
  <markdown>
  Our database where all the data from the application will be stored.
  </markdown>
</details>


### Deploying the "Node-RED App" service on the Kubernetes cluster
The final step is to specify where your service should run. In our case, that is the kubernetes cluster which we have just created.

1. Navigate to ```Navigation Menu -> Resource List -> Apps -> Node-RED-Name-Surname -> Deployment Automation```
2. Click on ```Deploy your app```
3. Deployment target: ```Kubernetes Service```
4. IBM Cloud API key: Click ```New```, Click ```Ok```
5. Container registry region: ```Frankfurt```
6. Container registry namespace: Leave empty
7. Cluster region: ```Frankfurt```
8. Cluster resource group: ```Default```
9. Cluster name: Chose the cluster you just created -> ```K8s-Name-Surname```
10. Click ```Next```
11. DevOps toolchain name: ```Node-RED-Name-Surname```
12. Region: ```Frankfurt```
13. Click ```Create``` and again now it is time to wait.

### Access your service
1. Navigate to your Apps in the Resource List and open the Node-RED one
2. As soon as your app is deployed you can access your app by clicking on the link specified as ```App URL```.

:::tip
As your Node-RED Application is running in the cloud, you can access it from every device using the App URL. Check it out with your smartphone to see it for yourself.
:::



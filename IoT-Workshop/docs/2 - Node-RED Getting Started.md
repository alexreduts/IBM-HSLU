# 2 - Node-RED Getting Started

Node-RED is a flow-based programming tool, originally developed by IBM in 2013 and is now a part of the OpenJS Foundation. Meaning it is super easy to create simple application with it and it is open source thus you can freely use it for whatever you like :smiley:.

We are going to use Node-RED to create our simple programs in the exercise. But before you start you find here the most important informations about Node-RED and how to use it.

## Step 1: Get to know the Node-RED Editor

The editor consists of four components:

- The **header** at the top, containing the the deploy button, main menu, and, if user authentication is enabled, the user menu.
- The **palette** on the left, containing the nodes available to use.
- The main **workspace** in the middle, where flows are created.
- The **sidebar** on the right.

<img src={require('@site/static/img/Clipboard_2022-05-02-10-42-10.png').default} />

### Palette

The Node-RED palette includes a default set of nodes that are the basic building blocks for creating flows.
They are organised into a number of categories, such as inputs, outputs and functions.
Above the palette is an input that can be used to filter the list of nodes.
The entire palette can be hidden by clicking the palette toggle that is shown when the mouse is over the palette

#### Reference
```
Keyboard shurtcut      Ctrl + Command + P
Menu option            View -> Show Palette
Action                 core:toggle-palette
```

<img src={require('@site/static/img/Clipboard_2022-05-02-10-50-09.png').default} />

### Workspace

The main workspace is where flows are developed by dragging nodes from the palette and wiring them together.

- **Flows**: A flow is represented as a tab in the editor workspace and is the main way to organise nodes.
- **Adding a flow**: To add a new flow, either click the button in the top bar, or double-click on free space in the tab bar.
- **Nodes**: 
  - Nodes can be added to the workspace by either:
    - dragging them from the palette,
    - using the quick-add dialog,
    - importing from the library or clipboard
  - Nodes are then joined together by wires via their ports.
- **Editing node properties**: A node's configuration can be edited by double clicking on the node, or pressing Enter when the workspace has focus.

<img src={require('@site/static/img/Clipboard_2022-05-02-10-58-40.png').default} />

### Sidebar

The sidebar contains panels that provide a number of useful tools within the editor.
- **Information** - view information about nodes and their help
- **Debug** - view messages passed to Debug nodes
- **Configuration Nodes** - manage configuration nodes
- **Context data** - view the contents of context

<img src={require('@site/static/img/Clipboard_2022-05-02-11-01-31.png').default} />

## Step 2: Running and Debuging a Flow

Deploy Button: Before you can run the flows you have created you always need them to deploy. This is rather easy as you just need to click on the ```Deploy``` Button in the up right corner.

Run a Flow: After deploying just click on your input node to trigger your flow to run.

Debug Nodes: In the the debug view on the sidebar you see all the messages deliverd to debug nodes. Hence, to check if your application is running correctly or looking for bugs, place some debug nodes in your flow, deploy it and then check what message arrive at them when you run your flow.


## Step 3: Installing New Nodes

Node-RED comes with a core set of useful nodes, but there are many more available from both the Node-RED project as well as the wider community. You can install nodes directly within the editor.

1. Click on the hamburger symbol (the three white stripes) in the top right corner
2. Click on **Manage palette**
3. Click on **Install** and search for whatever node you need. Example: node-red-dashboard

<img src={require('@site/static/img/Clipboard_2022-05-02-11-06-07.png').default} />




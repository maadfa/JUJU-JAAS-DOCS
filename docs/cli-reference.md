# Juju CLI Reference

This guide provides an overview of essential Juju CLI (Command-Line Interface) commands. It's a text-based interface that allows users to interact with a computer, software, or system by typing commands into a terminal or console,instead of clicking on tabs,buttons or menu etc.Use Windows Powershell terminal to run commands and interact with juju.The Juju CLI is the primary way users interact with Juju to deploy, manage, and scale applications on various cloud platforms.



##  Getting Started

To verify that Juju is installed correctly, open your terminal and type:

```bash
juju version
```


This should return the current version of Juju installed on your machine. 

## Bootstrap a Controller

A **controller** is the brain of Juju operations. It manages models, machines, and applications. Before you can deploy any services or charms, you need to **bootstrap** a controller. Bootstrapping sets up the initial environment where Juju can operate and manage your deployments.Run the following command for bootstrapping .


```bash
    juju bootstrap <cloud-name> <controller-name>
```   



The cloud name specifies which cloud environment one  wants to deploy Juju on.A cloud can be a public cloud (like AWS, Azure, Google Cloud), a private cloud (like OpenStack), or even a local environment (like LXD).

The controller name is a custom name given  to your Juju controller
A controller is the brain of Juju; it manages your models and deployments.
Naming the controller helps you identify it, especially if one  manages multiple controllers.

 ** Example

Suppose you want to bootstrap Juju on the public cloud called aws and name your controller my-controller.Then

```bash
juju bootstrap aws my-controller
```


Juju will start provisioning resources on AWS.

You will see output showing the bootstrap process, including creating instances and setting up the controller.

Once complete, you get a success message like:

!!! success "Bootstrap Successful"
    Controller "my-controller" bootstrapped on cloud "aws"

After bootstrapping, you can start deploying applications with Juju using this controller.

## Add a Model

After bootstrapping a controller in Juju, the next step is to **add a model**. A **model** in Juju is like a workspace or environment where you deploy and manage your applications.
A model is a container for applications and their configurations.

Each model is isolated from others. This means you can have different versions of the same application deployed in different models without any error.

```bash
juju add-model <model-name>
```



<model-name> is the name you want to give your model. It should be simple and descriptive.Good examples are  dev, testing, production, or my-webapp etc.

```bash
juju add-model dev
```

This command adds a new model named dev under the currently active controller.

## Expected Output

```
Added 'dev' model on my-controller/default with credential 'default' for user 'admin'
```

This message confirms that your model has been successfully added and is ready for deployments.

## Useful Tips

You can view all your models using:

```bash
juju models
```

## To switch between models:

To switch between the Models ,run  the following  commands on your terminal 

```bash
juju switch <controller-name>:<model-name>
```

Example

```bash
juju switch my-controller:dev
```



##  Deploy an Application (Charm)

Run the following command in your terminal .

```bash
juju deploy <charm-name>
```

This command deploys an application using a "charm" (a package of operational code). Charms automate the installation and configuration of software.

Example

```bash
juju deploy mysql
```

This command Deploys MySQL database.

##  Relate Applications

Many applications depend on others. This command connects services so they can communicate e.g., linking a web app to a database.

```bash
juju relate <app-1> <app-2>
```


Example 

```bash
juju relate wordpress mysql
```

## Add Units (Scale Application)

Add units to  to scale your app by adding more instances (units). This improves reliability and handles more user traffic.

```bash
juju add-unit <app-name> -n <number>
```



Example

```bash
juju add-unit mysql -n 2
```

This command adds two more MYSQL.

## Check Status

This shows a real-time overview of all deployed services, units, machines, and their health status.

```bash
juju status
```

 ## Remove Application

 It is  useful for cleanup or switching apps. It uninstalls an application and removes it from your model.

```bash
juju remove-application <app-name>
```

  ## Destroy Model

  This deletes the entire model and all applications and units inside it.

```bash
juju destroy-model <model-name>
```

Example 

```bash
juju destroy-model wordpress-site
```


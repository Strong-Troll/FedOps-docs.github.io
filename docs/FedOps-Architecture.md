# **FedOps Architecture**

![](./img/architecture.PNG)

FedOps has five key features:

1. FLScalize: It simplifies the application of data and models in a FL environment by leveraging Flower's Client and Server.

2.  the manager oversees and manages the real-time FL progress of both clients and server
3. Contribution Evaluation and Client Selection processes incentivize individual clients through a BCFL based on their performance.

4. the CI/CD/CFL system integrates with a Code Repo, 
enabling code deployment to multiple clients and servers for continuous or periodic federated learning

5. the FL dashboard is available for monitoring and observing the lifecycle of FL clients and server

-----
![FedOps work](./img/architecture2.PNG)

## 1. Create and Manage FL Task
![](./img/demo1.PNG)
![](./img/demo1-1.PNG)

To get started, create your FL Task in the FedOps web interface. Enter the title, description, and tags for your Task. Additionally, provide the address of the FL server Git repository that you have created. Once registered, it is not cumbersome to upload the code file to the web because you can separately manage the FL server code only in Git. This will allow the FL server to be deployed and run in our server environment.

## 2. Register FL clients
![](./img/demo2.PNG)

Once your FL Task is created, it will be assigned a unique task ID. In order to register a client in this FL task, the client’s config file needs to be updated with the assigned task ID and the user's WandB information for client monitoring. And run the client and client manager. In this way, the client is registered in the FL task.

-run the client and client manager
```
# run client
$ sh python client/client_task.py

# run client manager
$ sh python client_manager/client_manager.py
```
-docker
```
# run docker-compose.yaml file
$ docker-compose -f docker-compose.yml up -d --build
```

-shell
```
# run client and client manager to background env
$ sh run_shell_client.sh
```
## 3. Select FL clients and Run FL task
![](./img/demo3.PNG)

After selecting the client, click the "FL Start" button.This deploy and execute the FL server code that you previously set up in the server repository. The FL server creates FL rounds for task.

## 4. FL lifecycle Monitoring by FedOps Web
![](./img/demo4.PNG)
FedOps provides lifecycle management for FL tasks. You can monitor the performance of the global/local models and track the client's system resource usage based on the model version. Additionally, you can save and manage the global models according to different versions.

## 5. Client Lifecycle Monitoring
![](./img/demo5.PNG)

 To monitor the performance of the client's local model and the status of the client's data, you can check the information using the WandB that you set up earlier.

![](./img/demo5-1.PNG)
The FedOps also supports a docker-based client environment. 
Clients can monitor their data and performance through the ELK stack.

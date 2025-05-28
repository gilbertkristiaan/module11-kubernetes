# Gilbert Kristian - 2306274951 - Adpro A

## Tutorial: Hello Minikube

1. Compare the application logs before and after you exposed it as a Service. Try to open the app several times while the proxy into the Service is running. What do you see in the logs? Does the number of logs increase each time you open the app?<br><br>
![Foto](images/1.png)

When accessing the application directly inside the pod before exposing it as a service, the logs show only the initial startup messages "Started HTTP server on port 8080 & Started UDP server on port 8081." This is seen in the log at 10:46:38.

Once the application is exposed as a service, the initial startup messages continue to appear in the logs. In addition, the logs now capture incoming requests that pass through the service, allowing external access to the application.

For example, the screenshot shows a GET request logged at 10:49:57 and another at 10:59:28. Each time the application is accessed or refreshed in the browser, more log entries appear because the browser sends GET requests to the service.

This illustrates that exposing the pod via a Kubernetes service allows external traffic to reach the app, which results in an increase in log entries.

2. Notice that there are two versions of kubectl get invocation during this tutorial section. The first does not have any option, while the latter has -n option with value set to kube-system. What is the purpose of the -n option and why did the output not list the pods/services that you explicitly created? 

The -n option in the `kubectl` get command is used to specify a particular namespace in Kubernetes. This is especially helpful when multiple services share the same name across different namespaces. If we omit the -n flag, `kubectl` get will default to showing resources from the default namespace. Namespaces serve to isolate resources within a cluster, allowing better organization and management. For example, using -n kube-system will display resources within the kube-system namespace, which contains core Kubernetes components like DNS and the API server. Without specifying -n, the command only shows user-created resources in the default namespace.



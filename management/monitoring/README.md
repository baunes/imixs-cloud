# Monitoring

To get better insights of your *Imixs-Cloud* project you can install a monitoring service. 
Kubernetes provides several ways to collect and monitor cluster metrics like the memory or cpu usage of cluster nodes or pods. Kubernetes makes these data available through the Metrics API. These metrics can be accessed either directly by the user with the kubectl top command, or by a controller in the cluster, for example Horizontal Pod Autoscaler, to make decisions.


The *Imixs-Cloud* monitoring provides different setups to install a monitoring solution. 


 * [metrics-server](metrics-server/README.md) is a scalable, efficient source of container resource metrics for Kubernetes built-in autoscaling pipelines.
 * [imixs-prometheus](imixs-prometheus/README.md) is the recommended monitoring dashboard for *Imixs-Cloud*
 * [kube-prometheus](kube-prometheus/README.md) provides a configuration setup for a complete cluster monitoring stack based on the  Prometheus Operator project. 

After a metric server was installed you can monitor your Kubernetes cluster from the commandline tool **kubectl top**:


	$ kubectl top nodes
	NAME       CPU(cores)   CPU%   MEMORY(bytes)   MEMORY%   
	master-1   297m         14%    1358Mi          36%       
	worker-1   1424m        35%    13913Mi         89%       
	worker-2   1258m        31%    11278Mi         72%       
	worker-3   1133m        28%    9956Mi          63%       

	
You can also get the data of a singel POD:

	$ kubectl top pod traefik-797d34bc7d-l7k8j -n kube-system
	NAME                       CPU(cores)   MEMORY(bytes)   
	traefik-797d34bc7d-l7k8j   22m          50Mi      



The [k9s tool](../../tools/k9s/README.md) provides the core functionality to display metrics of the cluster and for each namespace. With the :pulse view you can see node dashboard.


<img src="../../doc/images/monitoring-008.png" />



	
See the install guides for the [imixs-prometheus](imixs-prometheus/README.md) for further details.
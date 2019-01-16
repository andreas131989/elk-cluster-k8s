This demo provides an out-of the box deployment of an elasticsearch-kibana Kubernetes cluster. Below, the architecture of the demo is displayed.

![alt text](https://raw.githubusercontent.com/andreas131989/elk-cluster-k8s/master/esk8s.png?token=AhcYFG-I9sP_TTbYTlDAWiEwVid65U3dks5cPxr5wA%3D%3D)

To run the demo, first create a new namespace with the name monitoring. Then, apply the service account and the config maps.

- kubectl create namespace monitoring
- kubectl apply -f es-sa.yaml
- kubectl apply -f es-configmap.yaml
- kubectl apply -f kibana-cm.yaml

Afterwards, create the 4 deployments

- kubectl apply -f es-master.yaml
- kubectl apply -f es-data.yaml
- kubectl apply -f es-ingest.yaml
- kubectl apply -f kibana.yaml

Finally, create the internal cluster services for elasticsearch and the external loadbalancer service for kibana

- kubectl apply -f es-discovery-svc.yaml
- kubectl apply -f es-svc.yaml
- kubectl apply -f es-ingest-svc.yaml
- kubectl apply -f kibana-svc.yaml

After the load balancer is provisioned automatically and configured, you can reach Kibana by using the url:
http://kibanaExternalIp:5601

# federated service mesh demo

## Prerequisites
<ul>
  <li> 2 OCP (4.12) on AWS Cluster (1 in ap-southeast-1 region and 1 in us-east-2 region)
  <li> Install Kiali Operator in both cluster
  <li> Install OpenShift Distributed Tracing Operator in both cluster
  <li> Install OpenShift ServiceMesh in both cluster
<ul>

## Run the following in ap-southeast Cluster
<ol>
  <li> Apply all yaml files in south-east-mesh directory
  <li> Apply all yaml files in book-info-south-east directory
<ol>

## Run the following in us-east Cluster
<ol>
  <li> Apply all yaml files in us-east-mesh directory
  <li> Apply all yaml files in book-info-us-east directory
<ol>

## Update Root Certificate
<ol>
  <li> get root-cert.pem from configmap south-east-mesh/istio-ca-root-cert from ap-southeast cluster
  <li> copy the value to configmap us-east-mesh/south-east-mesh-ca-root-cert in us-east cluster
  <li> get root-cert.pem from configmap us-east-mesh/istio-ca-root-cert from us-east cluster
  <li> copy the value to configmap south-east-mesh/us-east-mesh-ca-root-cert in ap-southeast cluster
<ol>

## Update Remote host in ServiceMeshPeer definition

<ol>
  <li> get load balancer host name of service/ingress-us-east-mesh from ap-southeast cluster
  <li> update spec.remote.addresses value of ServiceMeshPeer/south-east-mesh in us-east cluster
  <li> get load balancer host name of service/ingress-south-east-mesh from us-east cluster
  <li> update spec.remote.addresses value of ServiceMeshPeer/us-east-mesh in ap-southeast cluster
<ol>

# Blue-Green Deployment

Blue-green deployment is a technique that enables continuous delivery to production with reduced downtime and risk. It achieves this by running two identical production environments called Blue and Green. Let's assume, Green is the existing live instance and Blue is the new version of the application. At any time, only one of the environments is live, with the live environment serving all production traffic.

In the Blue/Green deployment pattern, a load balancer directs traffic to the active(Blue) environment while you upgrade the standby (Green) environment. After smoketesting the application in the Green environment and establishing that it is operating
correctly, you adjust the load balancer to direct traffic from the Blue environment to the Green environment.

### Benefits:

1)It helps to reduce the downtime and even reduces it to zero depending on the application design and deployment approach.

2)It gives a rapid way of rollback of the application in case of production issue.

3)It helps to build confidence to business users as testing of new version can be done in Production in isolation before rollout.

## Sample Helm Chart for Blue/Green Deployment

This helm chart has been created to deploy the applications using blue/green strategy.

### Pre-Requisites:

Helm Installed on your local machine, Go through following documentation if you do not have it already installed:
https://github.build.ge.com/torq/GeneralDocs.

### Steps Involved:

1)Pull the Helm chart folder into your local machine.

2)Do the Changes required according to the application you are deploying to the helm chart, like hostname, image, etc

3)Go inside the folder and run the following command to install the helm chart into your cluster.


Switch into the namespace you want this chart to be installed:   kubens namespace-name

Execute the below helm command to install:   helm install --name test -f values.yaml  .

To confirm if that chart is deployed or not, you can run:  kubectl get all

Also test via:   helm ls

Execute this helm command to delete the chart:   helm del --purge test

Use this command to delete the created service account:   kubectl delete sa serviceaccount-name




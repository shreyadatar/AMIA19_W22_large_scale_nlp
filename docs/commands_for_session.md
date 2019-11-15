# Cheatsheet

### Hands On

#### 1. Accessing the Virtual Machine (VM)
     ssh amia@<ip_address>
     Password: Tutorial2019

#### 2. Common Commands 
     ls     # list the files in a directory
     pwd    # display the current working directory
     cd     # change directories
     less   # scroll the contents of the file
     cat    # display all contents of file at once
     nano   # a way to edit text
     vim    # another, more complicated way to edit text
     
#### 3. Explore your cloud image(notes: use of `-la` to list with full attributes, and `~/` equivalence to `/home/amia`)
     cat /etc/os-release
     ls /home/amia
     ls /bin
     
#### 4. Basic Docker Commands (notes: Docker build!)
     docker images  # list available docker images on VM 
     docker --help
     docker pull docker/whalesay # pull docker image from Docker hub
     docker run docker/whalesay cowsay "Hello W22" # run docker image's version of "Hello World" 
     
#### 5. Let's use Docker!
     docker pull nlpieumn/ml # pull ML image from nlpieumn repository
     docker run -it nlpieumn/ml /bin/bash # ssh into ML image command shell
     
#### 6. Explore your docker image
     cat /etc/os-release
     ls /home/tutorial
     ls /bin 
     exit   # when you're done
     
#### 7. Build your own docker image
     cd tutorial
     docker build -t nlpieumn/vote --target vote . # build image from Dockerfile at target = "vote"; need to set env variable BUILDKIT=1
     
#### 8. Let's use Kubernetes! 
     kubectl get nodes # list all nodes in cluster
     ls /home/amia/.kube # list config file that allows unprivileged user to run commands
     kubectl get pods # list all pods in default namespace
     kubectl get pods --all-namespaces # list all pods in all namespaces
     kubectl get services # list all services in default namespace
     
     # create a kubernetes pod from a spec file
     kubectl create -f specs/dnstools.yaml kubectl get pods # list all pods in default namespace again and notice the difference from before
     
##### Kubernetes network troubleshooting resources (very useful!)
     # Advanced network diagnostics (using newly creeated pod) to determine if built-in kubernetes DNS is functiopning properly
     
     # Lookup (aka dig) a local cluster resources and get time to response for service/ep in kube-system namespace by servicename.kube-system
     
     kubectl get service --namespace=kube-system # get service name
     kubectl get endpoints --namespace=kube-system # show service endpoint name
     kubectl exec -ti dnstools -- time dig @10.96.0.10 kube-dns.kube-system # query by endpoint name

     # Lookup for external resources and get time to response
     kubectl exec -ti dnstools -- time dig @10.96.0.10 google.com
     
#### 9. Word Sense Disambiguation (WSD) (run of `python ~/tutorial/scripts/ml.py` from command line)
     docker run -it -e DOCKER='True' -v /home/amia/tutorial:/data nlpieumn/ml 
     /bin/bash -c "python /home/tutorial/ml.py -c svm" # run svm classifier from within docker image
     
#### 10. Let's use Argo!
     argo list # list all argo workflopws
     nano specs/evaluation.yaml 
     argo lint specs/evaluation.yaml # validate yaml file
     argo submit --watch specs/evaluation.yaml # submit argo workflow spec and watch status in real time
     argo get <workflow_name> # list workflow pods in workflow
     argo logs <pod_name> # view log of pod

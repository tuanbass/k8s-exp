# Components 
  
- Master node
  - ETCD: Store all the configuration information. Accessible only from API server. 
  - API server: 
    - Basically a Swagger/OpenAPI server.  
    - accessible via **kubectl proxy**
    - OpenAPI spec is at: http://localhost:8001/openapi/v2 ( version befire 1.10 use another swagger link http://localhost:8001/swaggerapi )
    - beyond of normal REST operation (CRUD), also provide some stream operation using websocket (/logs, /exec, /proxy, /attach)
    - **watch** request (?watch=true) to observer change
    - request life-cycle: authentication --> authorization (RBAC)==>admission (provide some default value for request)==>validation 
    - provide bassic log (activated with something like **kubectl --v=10** ) and audit logs  
    - work as a hub, most component talks together via API server
  - Scheduler:
    - Scheduler choose the node to run the pod (using **predicate** and **priority**)
    - Node selector: predicate base (require)  
    - Affinity: preference base . also provide more complex condition (multi condition, cross pod condition)
    - **Taint** mark a node as not suitable for schedule a pod. To override the taint, add a **toleration** in the pod descriptor. 
  - 
- Worker nodes
  - kubelet  
  - CRI (Docker/RKT/CRI-O)
  
- Special distribution: 
  - Kind (K IN Docker ) 
  - k3s 
  - Minikube 
  - microK8

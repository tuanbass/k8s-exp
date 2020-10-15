- metric server: sometime (especially for self build k8s , you need to disable ssl to have metrics-server work ) 
change in your deployment manisfest 
```
command:
    - /metrics-server 
    - --kubelet-insecure-tls
```

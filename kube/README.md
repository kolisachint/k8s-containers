cat >codercom-codeserver.yaml
      
apiVersion: v1
kind: Pod
metadata:
  labels:
    app: code-server
  name: code-server
spec:
  containers:
  - name: code-server
    image: codercom/code-server:latest
    ports:
    - containerPort: 8080
    
kubectl apply -f codercom-codeserver.yaml

kubectl get pods

kubectl exec -it code-server  cat /home/coder/.config/code-server/config.yaml |  grep password: | awk '{print $2}'
c52b39ffa8a0a9fab8638a16

kubectl port-forward code-server 8080:8080

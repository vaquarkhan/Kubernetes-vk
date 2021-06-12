# Kubernetes-vk

### Creating Kubernetes Pods:

Pods are the essential building-block of any Kubernetes application. When learning to use Kubernetes, one of the first things you will need to know is how to create pods.

The nginx server will need to be accessible via network in the future, so you will need to expose port 80 as a containerPort for the nginx container. Your team has also asked you to ensure that nginx runs in quiet mode for the time being to cut down on unnecessary log output. You can do this by setting the command to nginx and passing the following arg to the container: -g daemon off; -q. As this nginx server belongs to the Web team, you will need to create it in the team's web namespace.

To summarize:

- Use the nginx container image.
- The container needs a containerPort of 80.
- Set the command to nginx
- Pass in the -g daemon off; -q args to run nginx in quiet mode.
- Create the pod in the web namespace.

------------------------------------

/home/user/nginx.yml 


            apiVersion: v1
            kind: Pod
            metadata:
              name: nginx
              namespace: web
            spec:
              containers:
              - name: nginx
                image: nginx
                command: ["nginx"]
                args: ["-g", "daemon off;", "-q"]
                ports:
                - containerPort: 80
    
------------------------------------

kubectl create -f /home/user/nginx.yml

               kubectl get pods -n web


=========================================================






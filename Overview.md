The following are required to have a working CI/CD pipeline:

1. Access to a kubernetes cluster ( ie...admin to RHOS cluster )
2. create your own project to deploy your application and protect it from intemixing with other things
3. The pipeline.yaml and the pipelinerun.yaml are replaced by the tekton tasks
4. event-listener.yaml,podman-credentials.yaml,trigger-template.yaml,rbac.yaml,trigger-binding.yaml
These are the four main yaml files required.
 	The event listener declares that when an event is detected, it will run the trigger binding, and the trigger
        template.
        The event listener requires a service account to run. To create an SA for this the rbac.yaml is used.
        [you must ensure that registry (in my case i am using redhat quay.io ) has the permissions for the robot account set.
        i made the robot account with ADMIN.
        The trigger template exposes the parameters of the git repo i am pulling from, and the target registry the built image
        is going to. It also includes the secret created to access the registry in quay.io 
	The trigger binding specifies git hub repo url, and quay.io registry as the target
4a. kubectl apply -f trigger-binding.yaml ( be sure to be in your own namespace )
    kubectl apply -f rbac.yaml
    kubectl apply -f event-listener.yaml
    kubectl apply -f trigger-template.yaml
5. The route is created on the RHOS cluster with all the defaults and non-encrypted in my case
6. The webhook is created on my github the route has the complete URL when its created to then paste into the github webhook.


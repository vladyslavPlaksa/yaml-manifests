# Kubectl AI prompts

This table shows several examples of creating kubernetes resources using requests to the generative model

<table>
    <tr>
        <th>Name</th>
        <th>Prompt</th>
        <th>Description</th>
        <th>Example</th>
    </tr>
    <tr>
        <td>app</td>
        <td>Create yaml file to run Pod with image europe-central2-docker.pkg.dev/wise-coyote-417310/test/burylo_demo:v2.0.0, with labels app=demo and run=demo. Also, container port set as 8000 and port name as HTTP</td>
        <td>Creating a YAML manifest for Kubernetes that runs a simple application on port 8000</td>
        <td> 
            <a href='./yaml/app.yaml'>app.yaml</a>
        </td>
    </tr>
    <tr>
        <td>app-volumeMounts</td>
        <td>Create a YAML Pod manifest for Kubernetes with the following specifications: Pod name: app-volume; container based on the image gcr.io/kuar-demo/kuard-amd64:1; Liveness probe HTTP on /healthy:8080 with delay 5s, period 10s, timeout 1s, max. unsuccessful attempts 3; Readiness probe HTTP on /ready:8080, period 2s, delay 0s, max. 3 unsuccessful, 1 successful; open port 8080 with name http ; data volume "data" with hostPath /var/lib/app is mounted in /data</td>
        <td>Creating a YAML manifest for Kubernetes that runs a simple application on port 8000, has per-port availability checks, and a data store</td>
        <td> 
            <a href='./yaml/app-volumeMounts.yaml'>app-volumeMounts.yaml</a>
        </td>
    </tr>
    <tr>
        <td>app-secret</td>
        <td>Create a YAML Pod manifest for Kubernetes with the following specifications: Pod name: app-secret; container based on the redis image with the name mypod; data volume "foo" with secretName simple-secret and by mounting /etc/foo read-only</td>
        <td>Create a YAML Pod manifest for Kubernetes</td>
        <td> 
            <a href='./yaml/app-secret.yaml'>app-secret.yaml</a>
        </td>
    </tr>
    <tr>
        <td>app-secret-env</td>
        <td>Create a YAML Pod manifest for Kubernetes with the following specifications: Pod name: app-secret-env; container based on the redis image with the name mycontainer; two variables SECRET_USERNAME and SECRET_PASSWORD of the secret key mysecret1 are transferred to the environment; the container does not restart</td>
        <td>Creating a YAML manifest for Kubernetes that runs a Redis application with the secret data mounted as volume</td>
        <td> 
            <a href='./yaml/app-secret-env.yaml'>.app-secret-env.yaml</a>
        </td>
    </tr>
    <tr>
        <td>app-resources</td>
        <td>Create a YAML pod manifest for Kubernetes with the following specifications: Pod name: app-resource; a container based on the image gcr.io/kuar-demo/kuard-amd64:1 with the name app; Liveness probe HTTP on /healthy:8080 with delay 5s, period 10s, timeout 1s, max. failed attempts 3; Readiness probe HTTP on /ready:8080, period 2s, delay 0s, max. 3 unsuccessful, 1 successful; open port 8080 with name http; and determination of resources and limits of CPU 100m, RAM 256Mi</td>
        <td>Creating a YAML manifest for Kubernetes that launches the application and defines the limits for the containers it can use. Also, we will set availability checks</td>
        <td> 
            <a href='./yaml/app-resources.yaml'>app-resources.yaml</a>
        </td>
    </tr>
    <tr>
        <td>app-readinessProbe</td>
        <td>Create a YAML Pod manifest for Kubernetes with the following specifications: Pod Name: app-readinessprob; container based on the image gcr.io/kuar-demo/kuard-amd64:1 with the name app; Liveness probe HTTP on /:8000 with delay 5s, period 10s, timeout 1s, max. unsuccessful attempts 3; Readiness probe HTTP on /ready:8000, period 2s, delay 0s, max. 3 unsuccessful, 1 successful; open port 8000 with name http</td>
        <td>Creating a YAML manifest for Kubernetes launches the application and defines checks for the container's readiness to accept traffic and its viability</td>
        <td> 
            <a href='./yaml/app-readinessProbe.yaml'>app-readinessProbe.yaml</a>
        </td>
    </tr>
    <tr>
        <td>app-multicontainer</td>
        <td>Create a YAML Pod manifest for Kubernetes with the following specifications: Pod name: app-multi-containers; the first container based on the nginx image with the name 1st and by mounting /usr/share/nginx/html; a second container based on the debian image with the name 2nd, the same volume and mount path /html; the second container should add date information to the /html/index.html file every second in an endless loop</td>
        <td>Creating a YAML manifest for Kubernetes that runs two containers that share a shared space and work in pairs</td>
        <td> 
            <a href='./yaml/app-multicontainer.yaml'>app-multicontainer.yaml</a>
        </td>
    </tr>
    <tr>
        <td>app-livenessProbe</td>
        <td>Create a YAML Pod manifest for Kubernetes with the following specifications: Pod Name: app-livenessprob; namespace demo; container based on the image gcr.io/kuar-demo/kuard-amd64:1 with the name app; Liveness probe HTTP on /:8000 with delay 5s, period 10s, timeout 1s, max. unsuccessful attempts 3; open port 8080 with name http</td>
        <td>Creating a YAML manifest for Kubernetes launches the application and defines a health check</td>
        <td> 
            <a href='./yaml/app-livenessProbe.yaml'>app-livenessProbe.yaml</a>
        </td>
    </tr>
    <tr>
        <td>app-job</td>
        <td>Create a YAML Job manifest for Kubernetes with the following specifications: Job name: app-job-rsync; mount GCP volume glow-data-disk-200 type ext4 to container named init with image google/cloud-sdk:275.0.0-alpine running gsutil -m rsync -dr gs://glow-sportradar/ /data/input using sh; mount path /data/input; mount name data-input; the container is never reloaded and the backoff limit is 0</td>
        <td>Creating a YAML manifest for Kubernetes that creates a Job resource that will start the storage data synchronization process</td>
        <td> 
            <a href='./yaml/app-job.yaml'>app-job.yaml</a>
        </td>
    </tr>
    <tr>
        <td>app-cronjob</td>
        <td>Create a YAML CronJob manifest for Kubernetes with the following specifications: CronJob name: app-cronjob; the main task is to output the expression 'Hello world' every 5 minutes using a container with the name hello and the image bash</td>
        <td>Creating a YAML manifest for Kubernetes that creates a CronJob resource that will run a bash command every 5 minutes</td>
        <td> 
            <a href='./yaml/app-cronjob.yaml'>app-cronjob.yaml</a>
        </td>
    </tr>
    <tr>
        <td>app-configmap</td>
        <td>Create a YAML Pod manifest for Kubernetes with the following specifications: Pod name: app-config; a base redis image with the name mypod always pulling; the CONFIGMAP_PARAM parameter obtained from the config-param key of the configMapKeyRef value with the name app-config should be transferred to the environment; the config-volume volume is mounted in /config and receives configurations from app-config; Pod never restarts</td>
        <td>Creating a YAML manifest for Kubernetes that creates a Pod and passes the configMap parameters to the container environment</td>
        <td> 
            <a href='./yaml/app-configmap.yaml'>app-configmap.yaml</a>
        </td>
    </tr>
</table>
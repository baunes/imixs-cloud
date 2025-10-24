# Applications

The /apps/ directory holds the configuration of applications running as services in the _Imixs-Cloud_.
Each application has its own application directory holding at least a kubernetes .yaml file to deploy objects and services.

You can define your own services within the /apps/ directory. Each application has its own sub-folder:

     |+ apps/
        |+ MY-APP/
           |  020-deployment.yaml

Using the _kubectl apply_ command you can easily create or delete your services and objects defined within a apps/ or management/ sub-directory:

    $ kubectl apply -f apps/MY-APP/

For example to deploy the whoami sample service you just need to call:

    $ kubectl apply -f app/whoami/

In kubernetes all resources and services are typically described in separate files. Use a naming convention to create an implicit order in which your objects should be created.

     |+ whoami/
        |- 010-MY-APP.yaml
        |- 020-MY-DATABASE.yaml

If you want to remove an already deployed service or object just use the delete command:

    $ kubectl delete -f app/whoami/

If you just want to restart your Pods - for example if you have made changes to your deployed container image - cou can call the method `rollout restart`. This will restart all Pods within your deployment:

```
kubectl rollout restart apps/MY-APP/
```

To start all Pods in an explizit namespace you use the option `-n` :

```
kubectl rollout restart deployment -n <namespace>
```

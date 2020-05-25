# helmDemo
Helm Implimentation Demo with Basic App


## Run with HelmFile


List of Commands to Run with HelmFile

```
1. helmfile repos
2. helmfile sync
```

List of Commands to Run with helm if individual


```
1. helm install -f kanban-postgres.yaml postgres ./postgres
2. helm install -f adminer.yaml adminer ./app
3. helm install -f kanban-app.yaml kanban-app ./app
4. helm install -f kanban-ui.yaml kanban-ui ./app
5. helm dependency update ./ingress/
6. helm install -f ingress.yaml ingress ./ingress
7. helm list
8. kubectl get deployments
```


## Architecture of App:

![alt text](https://miro.medium.com/max/1400/1*OfGTPIUBBnwF7QYgWTYkSA.png)

## Architecture of PosgreSQL HA:

The Bitnami PostgreSQL chart is configured with password-based authentication enabled by default, and no RBAC rules are required for its deployment. The default administrator username is postgres, and the default replication account username is repl_user. Passwords for both accounts should be specified at deployment time, as shown in the previous section.

The values-posgres.yaml configuration configures two nodes by default: a master and a slave. However, you can scale the cluster up or down by adding or removing nodes even after the initial deployment. The PostgreSQL service is available on the standard port 5432. Remote connections are enabled for this port by default.

![alt text](https://engineering.bitnami.com/images/postgres-helm/topology-2fec18cd.png)


## Data Replication and Persistence
A key feature of Bitnami's PostgreSQL Helm chart is that it comes pre-configured to provide a horizontally scalable and fault-tolerant deployment. Data automatically replicates from the master node to all slave nodes. The master node receives all write operations, while the slave nodes repeat the operations performed by the master node on their own copies of the data set and are used for read operation. This model improves the overall performance of the solution. It also simplifies disaster recovery, because a copy of the data is maintained on each node in the cluster.

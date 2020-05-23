# helmDemo
Helm Implimentation Demo with Basic App

List of Commands to Run

1. helm install -f kanban-postgres.yaml postgres ./postgres
2. helm install -f adminer.yaml adminer ./app
3. helm install -f kanban-app.yaml kanban-app ./app
4. helm install -f kanban-ui.yaml kanban-ui ./app
5. helm dependency update ./ingress/
6. helm install -f ingress.yaml ingress ./ingress
7. helm list
8. kubectl get deployments

Architecture of App:

![alt text](https://miro.medium.com/max/1400/1*OfGTPIUBBnwF7QYgWTYkSA.png)

Docker:
1. Run all containers
    1. docker-compose up 
2. Test user endpoints in Postman
    1. POST http://localhost:8080/signup
    2. POST http://localhost:8080/login
3. Test task endpoints in Postman
    1. GET http://localhost:8000/tasks
    2. POST http://localhost:8000/tasks

Kub:
1. Build images
    1. docker build -t ievgeniimasko/kub-user ./users-api 
    2. docker build -t ievgeniimasko/kub-auth ./auth-api 
    3. docker build -t ievgeniimasko/kub-task ./task-api
2. Push images to repo (e.g DockerHub)
    1. docker push ievgeniimasko/kub-user
    2. docker push ievgeniimasko/kub-auth
    3. docker push ievgeniimasko/kub-task
3. Start minikube with Docker driver
    1. minikube start --driver=docker 
4. Apply deployment and services
    1. kubectl apply -f=users-deployment.yaml -f=users-service.yaml -f=auth-deployment.yaml -f=auth-service.yaml  -f=tasks-deployment.yaml -f=tasks-service.yaml
5. Check status of deployments and pods
    1. kubectl get deployments
    2. kubectl get pods
6. Get external ip 
    1.  minikube service users-service
    2.  minikube service tasks-service    
7. Test user and task endpoints in Postman with generated ip
    1. Remember to include  Bearer Token ‘abc’ for tasks

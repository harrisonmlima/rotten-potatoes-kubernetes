# Projeto rotten-potatoes

### Sobre o projeto
O projeto rotten potatoes é um projeto desenvolvido em Python. O projeto tem como objetivo ser um exemplo para a criação de ambiente com containers usando Python.

### Observações do projeto
A aplicação é exposta usando a porta 5000

### Observação do build
Ir para a pasta src, e então executar o docker build para geração da imagem, e então alterar na pasta k8s/api/deployment.yaml

### Observação do inicio do cluster
Executar kubectl apply -f k8s/db -f k8s/api -f k8s/adb

### Acesso dos 2 programas
Na hora de criar o cluster k3d, você tem q dar 2 port binding, como mostrado abaixo:
k3d cluster create meucluster -p "80:30000" -p "8080:31000"
Onde o localhost acessa o mongo-express e localhost:8080 acessa rotten-potatoes 

# Project rotten-potatoes

### About the project
The project rotten potatoes is a project developed in Python. The project goal is to be a example to environment creation with containers using Python.

### Project observation
The application runs using PORT 5000

### Build Observation
Go to src folder, then execute docker build to generate the image, then changes the image name in the file deployment-web.yaml in k8s folder

### Cluster initialize Observation
Execute kubectl apply -f k8s/db -f k8s/api -f k8s/adb

### Access both programs
Before create the cluster k3d, You have to port binding both of them, as shown next:
k3d cluster create meucluster -p "8080:30000" -p "8080:31000"
localhost access mongo-express and localhost:8080 acess rotten-potatoes

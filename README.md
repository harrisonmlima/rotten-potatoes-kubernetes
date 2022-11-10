# Projeto rotten-potatoes

## Configuração / Configuration

MONGODB_DB => Nome do database

MONGODB_HOST => Host do MongoDB

MONGODB_PORT => Porta de acesso ao MongoDB

MONGODB_USERNAME => Usuário do MongoDB

MONGODB_PASSWORD => Senha do MongoDB


### Sobre o projeto
O projeto rotten potatoes é um projeto desenvolvido em Python. O projeto tem como objetivo ser um exemplo para a criação de ambiente com containers usando Python.

### Observações do projeto
A aplicação é exposta usando a porta 5000

### Observação do build
Ir para a pasta src, e então executar o docker build para geração da imagem, e então alterar na pasta k8s/deployment-web.yaml

### Observação do inicio do cluster
Executar kubectl apply -f k8s/

### Acesso dos 2 programas
Na hora de criar o cluster k3d, você tem q dar 2 port binding, como mostrado abaixo:
k3d cluster create meucluster -p "8080:30000" -p "80:31000"
Onde o localhost:8080 acessa o rotten-potatoes e o localhost acessa o mongo-express

# Project rotten-potatoes

### About the project
The project rotten potatoes is a project developed in Python. The project goal is to be a example to environment creation with containers using Python.

### Project observation
The application runs using PORT 5000

### Build Observation
Go to src folder, then execute docker build to generate the image, then changes the image name in the file deployment-web.yaml in k8s folder

### Cluster initialize Observation
Execute kubectl apply -f k8s/

### Access both programs
Before create the cluster k3d, You have to port binding both of them, as shown next:
k3d cluster create meucluster -p "8080:30000" -p "80:31000"
localhost:8080 access rotten-potatoes and localhost access mongo-express
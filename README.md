# GS-Devops-Floodian

LINK VIDEO DEMONSTRATIVO YOUTUBE: https://youtu.be/ZeBhg7iYh2I

Comandos essenciais utilizados para criar, buildar e rodar a API Java com Docker:

1. Atualizar e instalar dependências
sudo apt update
sudo apt install git curl openjdk-17-jdk maven docker.io -y

2. Clonar o projeto do GitHub
mkdir -p ~/projetos
cd ~/projetos
git clone https://github.com/CmarxS/MySQL-Java-Floodian.git floodian
cd floodian

3. Criar rede Docker para os containers se comunicarem
docker network create floodian-net

4. Dockerfile
(Dockerfile fara tudo que resta agora)

5. Buildar a imagem da API Java
docker build -t floodian-api .

 6. Rodar o container da API
docker run -d \
  --name floodian-api \
  --network floodian-net \
  -p 8080:8080 \
  floodian-api





-----------CONTAINER DO BANCO DE DADOS

docker run -d \
  --name db-gs-floodian \
  -e MYSQL_ROOT_PASSWORD=root123 \
  -e MYSQL_DATABASE=dbgsflood \
  -e MYSQL_USER=floodianuserjava \
  -e MYSQL_PASSWORD=floodpass \
  -v mysql-data:/var/lib/mysql \
  -p 3306:3306 \
  mysql:8
  
🧩 Explicação dos parâmetros
Parâmetro	Descrição
-d	Executa o container em segundo plano (modo detached).
--name db-gs-floodian	Define um nome para o container.
-e MYSQL_ROOT_PASSWORD=root123	Define a senha do usuário root do MySQL.
-e MYSQL_DATABASE=dbgsflood	Cria automaticamente o banco de dados dbgsflood.
-e MYSQL_USER=floodianuserjava	Cria um usuário MySQL adicional.
-e MYSQL_PASSWORD=floodpass	Define a senha do usuário criado acima.
-v mysql-data:/var/lib/mysql	Cria e monta um volume persistente chamado mysql-data.
-p 3306:3306	Mapeia a porta do host (externa) com a porta do container (interna).
mysql:8	Utiliza a imagem oficial do MySQL na versão 8.

-----------CRUD

▶️ Criar um usuário (POST)
curl -X POST http://localhost:8080/Floodian/usuarios \
-H "Content-Type: application/json" \
-d '{
  "nome": "João da Silva",
  "email": "joao@teste.com",
  "telefone": "11999999999",
  "tipoUsuario": "ADMIN",
  "senha": "senha123"
}'

📋 Listar todos os usuários (GET)
curl http://localhost:8080/Floodian/usuarios

🔍 Buscar por ID (GET)
curl http://localhost:8080/Floodian/usuarios/1

✏️ Atualizar um usuário (PUT)
curl -X PUT http://localhost:8080/Floodian/usuarios/1 \
-H "Content-Type: application/json" \
-d '{
  "nome": "João Atualizado",
  "email": "joaoatualizado@teste.com",
  "telefone": "11988887777",
  "tipoUsuario": "USER",
  "senha": "novaSenha"
}'

❌ Excluir (DELETE)
curl -X DELETE http://localhost:8080/Floodian/usuarios/1


PRINTS DE COMPROVAÇÃO:

Docker ps (Os dois containers rodando)
![image](https://github.com/user-attachments/assets/4564dec8-9da2-474d-9192-4e73816336f1)

Logs Container do Banco MySQL
![image](https://github.com/user-attachments/assets/732ac8be-16f0-4153-9bf4-66d3280f7795)

Logs Container da API Java
![image](https://github.com/user-attachments/assets/8a7abf19-25b3-4fa6-a041-28ba7712bfc9)
![image](https://github.com/user-attachments/assets/51f0a1d5-eacd-4cb3-bfa5-88a05b562dd6)








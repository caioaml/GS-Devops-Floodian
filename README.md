# GS-Devops-Floodian

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

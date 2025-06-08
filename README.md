# GS-Devops-Floodian

-----------CRUD

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

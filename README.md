# Auth Server

Servidor de autenticação e autorização com Spring Boot, JWT e banco H2.

## Funcionalidades

- Autenticação JWT
- Autorização baseada em roles (USER/ADMIN)
- Banco H2 em memória
- Usuários padrão pré-configurados

## Execução

```bash
mvnw.cmd spring-boot:run
```

## Endpoints

### Autenticação
- `POST /api/auth/signin` - Login
- `POST /api/auth/signup` - Registro

### Teste
- `GET /api/test/all` - Público
- `GET /api/test/user` - Requer role USER ou ADMIN
- `GET /api/test/admin` - Requer role ADMIN

### Banco
- `GET /h2-console` - Console H2 (url: jdbc:h2:mem:authdb, user: sa)

## Usuários Padrão

| Username | Password | Role |
|----------|----------|------|
| admin    | admin123 | ADMIN |
| user     | user123  | USER |

## Exemplos de Uso

### Login
```bash
curl -X POST http://localhost:8080/api/auth/signin \
  -H "Content-Type: application/json" \
  -d '{"username":"admin","password":"admin123"}'
```

### Acesso com Token
```bash
curl -H "Authorization: Bearer <TOKEN>" \
  http://localhost:8080/api/test/admin
```

### Registro
```bash
curl -X POST http://localhost:8080/api/auth/signup \
  -H "Content-Type: application/json" \
  -d '{"username":"novo","password":"123","role":["admin"]}'
```
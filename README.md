# Desencaixados - Plataforma de Acessibilidade Web

Projeto desenvolvido para hackathon com foco em **acessibilidade digital**. A solucao combina:

- **Frontend Angular** para autenticacao e configuracao de preferencias
- **Extensao de navegador** para aplicar ajustes de acessibilidade em paginas web
- **API Spring Boot** para persistencia de perfis, autenticacao e auditoria


## Teste 


### 1. Pre-requisitos

- Docker
- Java 21
- Node.js 18 ou superior
- npm

### 2. Subir a API e o banco

Em um terminal:

```bash
cd backend
docker compose up -d
./mvnw spring-boot:run
```

Ao final, a API ficara disponivel em:

- `http://localhost:8080`
- Swagger: `http://localhost:8080/swagger-ui.html`

### 3. Subir a interface

Em outro terminal:

```bash
cd frontend
npm install
npm start
```

Abra no navegador:

- `http://localhost:4200`

### 4. Entrar com o usuario de demonstracao

O backend cria automaticamente um usuario padrao para agilizar a avaliacao:

```text
Email: usuario@caixa.gov.br
Senha: SenhaForte123
```

> Nao e necessario cadastrar usuario, criar banco manualmente nem configurar variaveis de ambiente para o fluxo local padrao.

## Fluxo sugerido de avaliacao

Para a banca testar o sistema de ponta a ponta:

1. Inicie o backend e o frontend com os comandos acima.
2. Acesse `http://localhost:4200`.
3. Faca login com o usuario de demonstracao.
4. Ajuste as preferencias de acessibilidade disponiveis na interface.
5. Confirme que as preferencias sao persistidas e recuperadas pelo usuario autenticado.
6. Se quiser validar a API diretamente, abra o Swagger em `http://localhost:8080/swagger-ui.html`.

## Teste da extensao no navegador

Se a avaliacao exigir a experiencia completa da extensao:

```bash
cd frontend
npm install
npm run build:extension
```

Isso gera a pasta `frontend/extension/`.

### Chrome / Edge / Brave

1. Abra `chrome://extensions/` ou `edge://extensions/`.
2. Ative o **Modo do desenvolvedor**.
3. Clique em **Carregar sem compactacao**.
4. Selecione a pasta `frontend/extension/`.

### Firefox

1. Abra `about:debugging#/runtime`.
2. Clique em **Carregar extensao temporaria**.
3. Selecione o arquivo `frontend/extension/manifest.json`.

## O que a solucao entrega

- Login com autenticacao JWT
- Persistencia de preferencias de acessibilidade por usuario
- Ajustes visuais para leitura e navegacao
- Preparacao para uso como extensao de navegador
- Auditoria de alteracoes no backend

## Estrutura do repositorio

```text
backend/   API Spring Boot + PostgreSQL
frontend/  Angular + build da extensao
```

## Documentacao complementar

- Backend: [`backend/README.md`](backend/README.md)
- Frontend: [`frontend/README.md`](frontend/README.md)

## Encerrando o ambiente

Para parar o banco local:

```bash
cd backend
docker compose down
```

### Passo a Passo para Resolver o Problema do Teste

# Error: connect ECONNREFUSED 172.19.0.2:3306
79ca8df0f551_app    |     at TCPConnectWrap.afterConnect [as oncomplete] (node:net:1555:16) {
79ca8df0f551_app    |   errno: -111,
79ca8df0f551_app    |   code: 'ECONNREFUSED',
79ca8df0f551_app    |   syscall: 'connect',
79ca8df0f551_app    |   address: '172.19.0.2',
79ca8df0f551_app    |   port: 3306,
79ca8df0f551_app    |   fatal: true
79ca8df0f551_app    | }

database exited with code 0
database            | 2024-08-11 04:56:59+00:00 [Note] [Entrypoint]: Switching to dedicated user 'mysql'

  
1. # Problema Enfrentado com Docker Compose e Banco de Dados

Erro de Comunicação com o Banco de Dados:
Ao executar o comando docker-compose, você poderá enfrentar erros na comunicação com o banco de dados. O erro indica que o cliente de conexão estava tendo dificuldades para acessar o banco de dados.

2. # Solução Tentada:

Alterar o cliente de conexão MySQL para mysql2. O mysql2 é um cliente que já foi utilizado em desafios anteriores e apresentou uma maior estabilidade.
Essa alteração resolverá o problema de conexão com o banco de dados, permitindo que o sistema se conecte sem problemas.

3. # Próxima Alteração - Banco de Dados:

Se o banco de dados estiver incompleto, especificamente faltando a criação da tabela people.
siga os demais passos para solucionar.

**Iniciando os Containers**

- **Comando**:
  ```bash
  docker compose up
  ```
- **Função**: Este comando inicia todos os serviços definidos no `docker-compose.yaml`, incluindo o banco de dados e o servidor web.

---

**. Verificando os Containers Ativos**

- **Comando**:
  ```bash
  docker container ps
  ```
- **Função**: Lista todos os containers ativos, permitindo verificar se o MySQL e o servidor web estão em execução.

---

**. Erro: Tabela Não Existente**

- **Problema**: Ao tentar acessar a aplicação, ocorreu um erro indicando que a tabela no banco de dados não existia.
- **Solução**: Acessar o container do banco de dados para criar manualmente a tabela.

---

**. Acessando o Container do Banco de Dados**

- **Comando**:
  ```bash
  docker exec -it <id-do-container> bash
  ```
- **Função**: Este comando permite que você entre no shell do container especificado. Substitua `<id-do-container>` pelo ID real do container do banco de dados.

---

**. Criando a Tabela no MySQL**

- **Passos**:

  1. **Acessar o MySQL**:
     - **Comando**:
       ```bash
       mysql -uroot -p
       ```
     - **Login**: Use a senha definida no arquivo de configuração do MySQL (provavelmente `root`).

  2. **Selecionar o Banco de Dados**:
     - **Comando**:
       ```bash
       USE nodedb;
       ```
     - **Objetivo**: Escolher o banco de dados onde a tabela será criada.

  3. **Criar a Tabela**:
     - Execute o comando DDL (Data Definition Language) para criar a tabela desejada.

     **Exemplo**:
     ```sql
     CREATE TABLE exemplo (
       id INT AUTO_INCREMENT PRIMARY KEY,
       nome VARCHAR(255) NOT NULL
     );
     ```

---

1. **Acessando a Aplicação**

- **URL**: [http://localhost:8080](http://localhost:8080)
- **Função**: Acesse a aplicação através deste endpoint para verificar se tudo está funcionando conforme o esperado.

---

**Resumo**: Siga cada passo cuidadosamente para garantir que o ambiente Docker esteja configurado corretamente e que todos os serviços estejam funcionando conforme o esperado. Se encontrar problemas, verifique os logs dos containers para diagnósticos mais detalhados.
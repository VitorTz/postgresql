# Instalação


```bash
sudo apt update
sudo apt sudo apt install postgresql postgresql-contrib -y
```  

# Inicialização


```bash
sudo systemctl enable postgresql
sudo systemctl start postgresql
sudo systemctl status postgresql
```


# Configuração


```bash
sudo -i -u postgres
psql
```


```bash
CREATE USER nome_usuario WITH PASSWORD 'senha';
ALTER USER nome_usuario CREATEDB;
ALTER USER nome_usuario WITH SUPERUSER;

CREATE DATABASE nome_banco OWNER nome_usuario;
\c nome_banco
GRANT ALL PRIVILEGES ON DATABASE nome_banco TO nome_usuario;
ALTER DEFAULT PRIVILEGES IN SCHEMA public GRANT ALL ON TABLES TO nome_usuario;
ALTER DEFAULT PRIVILEGES IN SCHEMA public GRANT ALL ON SEQUENCES TO nome_usuario;
```
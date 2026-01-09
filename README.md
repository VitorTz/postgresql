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


# Backup

## Apenas inserts
```postgresql
pg_dump --data-only --table=schema.tabela --inserts "postgresql://usuario:senha@host:5432/banco" > backup.sql

psql "postgresql://usuario:senha@host:5432/banco" < backup.sql
```

# Delete

> sudo -u postgres dropdb nome_do_banco

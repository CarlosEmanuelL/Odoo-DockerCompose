# Odoo com Docker Compose

Este repositório fornece um ambiente pré-configurado para rodar o Odoo utilizando Docker Compose, garantindo uma instalação simples e eficiente.

## Requisitos
Antes de iniciar, certifique-se de ter os seguintes softwares instalados:

- [Docker](https://docs.docker.com/get-docker/)
- [Docker Compose](https://docs.docker.com/compose/install/)

## Estrutura do Projeto

O projeto contém os seguintes arquivos e diretórios:

```
.
├── docker-compose.yml  # Arquivo de configuração do Docker Compose
├── config/             # Diretório para arquivos de configuração do Odoo
├── addons/             # Diretório para módulos extras do Odoo
├── odoo_pg_pass        # Arquivo contendo a senha do banco de dados
```

## Configuração

### 1. Criar o arquivo de senha do banco de dados

Antes de iniciar os containers, crie um arquivo `odoo_pg_pass` no mesmo diretório do `docker-compose.yml` e adicione uma senha para o banco de dados. Exemplo:

```sh
echo "sua_senha_forte" > odoo_pg_pass
```

Certifique-se de que o arquivo tenha as permissões corretas:

```sh
chmod 600 odoo_pg_pass
```

### 2. Subir os containers

Para iniciar os containers, execute o seguinte comando:

```sh
docker-compose up -d
```

Isso iniciará os seguintes serviços:
- **web**: Odoo
- **db**: PostgreSQL

### 3. Acessar a interface do Odoo

Depois que os containers estiverem em execução, você pode acessar o Odoo no seu navegador:

- Interface web do Odoo: [http://localhost:8069](http://localhost:8069)
- Live chat: [http://localhost:8072](http://localhost:8072)

### 4. Parar os containers

Caso precise parar os containers, use:

```sh
docker-compose down
```

## Volumes Persistentes
Os dados do Odoo e do PostgreSQL são armazenados nos volumes Docker para garantir persistência entre reinícios:

- **odoo-web-data**: Armazena os dados da aplicação Odoo.
- **odoo-db-data**: Armazena os dados do banco PostgreSQL.

## Personalização
Você pode adicionar módulos personalizados no diretório `addons/` para serem carregados pelo Odoo.

## Debug e Logs
Para visualizar os logs dos containers, utilize:

```sh
docker-compose logs -f
```

Para verificar logs específicos:

```sh
docker-compose logs web  # Logs do Odoo
docker-compose logs db   # Logs do PostgreSQL
```

## Licença
Este repositório está disponível sob a [Licença MIT](LICENSE).

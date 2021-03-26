# My5GCore Compose

Esse repositório é uma versão do my5gCore executada através de containers e automatizada via compose. Esse projeto é baseado no [Free5gC Compose](https://github.com/free5gc/free5gc-compose).



## Prerequisitos

Certifique-se de estar utilizando o kernel 5.0.0-23-generic ou superior. Você pode verificar com:

```bash
$ uname -r
```

### 1. GTP5G Kernel Module

Por conta das exigências do UPF faz-se necessário a instalação do gtp5g:

```bash
$ git clone https://github.com/PrinzOwO/gtp5g.git
$ cd gtp5g
$ make
$ sudo make install
```

### 2. Docker

Instalação de pacotes pré-requisitos

```bash
$ sudo apt install apt-transport-https ca-certificates curl software-properties-common
```

Adição da chave para o repositório oficial

```bash
$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```

Adição do repositório Docker

```bash
$ sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable"
```

Atualização do bando de pacotes

```bash
$ sudo apt update
```

Instalação do Docker

```bash
$ sudo apt install docker-ce
```

Para verificar o status

```
$ sudo systemctl status docker
```

### 3. Docker Compose

O docker compose permite gerir a inicialização e finalização de diversos containers simultaneamente. Seu funcionamento se dá através de arquivos YAML que guardam as definições dos containers.

Baixando a release `1.28.2` do binário de instalação e salvar em `/usr/local/bin/docker-compose`, que tornará este software globalmente acessível como `docker-compose`.

```bash
$ sudo curl -L "https://github.com/docker/compose/releases/download/1.28.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
```

Definição das permissões para execução

```bash
$ sudo chmod +x /usr/local/bin/docker-compose
```

Para verificar se tudo ocorreu bem execute

```bash
$ docker-compose --version
```



## Iniciando My5g Core

Como precisamos criar uma interface de tunel, necessitamos criar um containger com permissões de root.

Dowload dos arquivos do núcleo:

```bash
$ git clone https://github.com/my5G/my5Gcore-compose.git
```

Compilando os arquivos

```bash
$ cd my5Gcore-compose
$ sudo make base
```

Construção dos serviços

```bash
$ sudo docker-compose build
```

Executando os containers através do docker-compose

```bash
$ sudo docker-compose up 
```

ou

```bash
$ sudo docker-compose up -d # Para execução em segundo plano
```

Para verificar as imagens disponíveis em nosso containers execute:

```bash
$ sudo docker images
```

![my5gcore-compose](img/my5gcore.jpg)

Figura 1: Funções do My5GCore

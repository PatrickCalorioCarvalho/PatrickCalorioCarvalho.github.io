---
layout: post
title:  "Instalação Mysql no Ubunto"
date:   2022-02-18 00:53:10 -0300
categories: test
---

Atualizar Index de pacotes
``` bash
sudo apt-get update
```

Instalação do pacote ```mysql-server ```
``` bash
sudo apt-get install mysql-server
```

Configuração Inicial (Y para tudo e entre com uma senha para o usuario root)
``` bash
sudo mysql_secure_installation
```

Primeira conexão no Mysql
``` bash
sudo mysql
```

Difinir senha de acesso remoto para usuário root
``` sql
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'SUA_SENHA';
FLUSH PRIVILEGES;
exit
```

Agora para conectar ao Mysql 
``` bash
mysql -u root -p
```
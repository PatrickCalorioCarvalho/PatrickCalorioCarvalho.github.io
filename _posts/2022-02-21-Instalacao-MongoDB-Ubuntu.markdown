---
layout: post
title:  "Instalação MongoDB no Ubunto"
date:   2022-02-21 00:00:00 -0300
categories: SO
---

Importar chave pública GPG
``` bash
wget -qO - https://www.mongodb.org/static/pgp/server-5.0.asc | sudo apt-key add -
```

Adicionado Lista de Pacote de Instalação
``` bash
echo "deb [ arch=amd64,arm64 ] https://repo.mongodb.org/apt/ubuntu focal/mongodb-org/5.0 multiverse" |sudo tee /etc/apt/sources.list.d/mongodb-org-5.0.list
```

Atualizar Index de Pacotes
``` bash
sudo apt-get update
```

Instalação do pacote ```mongodb-org```
``` bash
sudo apt-get install -y mongodb-org
```

Habilidar Serviço 
``` bash
sudo systemctl enable mongod
```

 Ativar Serviço 
``` bash
sudo systemctl start mongod
```
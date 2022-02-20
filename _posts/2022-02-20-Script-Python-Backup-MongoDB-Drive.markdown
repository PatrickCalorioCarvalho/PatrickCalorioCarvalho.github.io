---
layout: post
title:  "Script Python Backup MongoDB Drive"
date:   2022-02-20 00:00:00 -0300
categories: test
---
## Criando Token de Acesso ao Google Drive

Acessar:
[Criando Token de Acesso ao Google Drive](https://patrickcaloriocarvalho.github.io/test/2022/02/19/Script-Python-Backup-Mysql-Drive.html)

## Configuração do Google Drive

Acessar:
[Configuração do Google Drive](https://patrickcaloriocarvalho.github.io/test/2022/02/19/Script-Python-Backup-Mysql-Drive.html)


## Configuração Python 

Acessar:
[Configuração Python ](https://patrickcaloriocarvalho.github.io/test/2022/02/19/Script-Python-Backup-Mysql-Drive.html)

## Codigo 

O Diretorio do Projeto vai ficar assim
``` bash
.
└── Script-Python-Backup-MongoDB-Drive
    ├── main.py
    ├── settings.yaml
```

No Arquivo ``` settings.yaml ```troque ``` COLOQUE_AQUI_SEU_CLIENT_ID ``` por ``` client_id ``` e troque ``` COLOQUE_AQUI_SEU_CLIENT_SECRET ``` por ``` client_secret ```

 ``` yaml
client_config_backend: settings
client_config:
  client_id: COLOQUE_AQUI_SEU_CLIENT_ID
  client_secret: COLOQUE_AQUI_SEU_CLIENT_SECRET

save_credentials: True
save_credentials_backend: file
save_credentials_file: credentials.json

get_refresh_token: True

oauth_scope:
  - https://www.googleapis.com/auth/drive.file
  - https://www.googleapis.com/auth/drive.install

```

No arquivo ``` main.py ``` troque ``` COLOQUE_AQUI_SEU_FOLDERID ``` por ``` FOLDERID ```
``` python
from pydrive.auth import GoogleAuth
from pydrive.drive import GoogleDrive
import os
import datetime
gauth = GoogleAuth()           
drive = GoogleDrive(gauth) 
Database = "Burger"
NomeArquivo = Database +"-"+datetime.datetime.now().strftime("%d-%m-%Y") +".gz"
LocalArquivo  = '"'+os.getcwd() + "/" + NomeArquivo+'"'
os.system('mongodump --db '+ Database +' --gzip --archive >'+LocalArquivo+'')
gfile = drive.CreateFile({'parents': [{'id': 'COLOQUE_AQUI_SEU_FOLDERID'}]})
gfile.SetContentFile(NomeArquivo)
gfile.Upload()
os.system('rm '+LocalArquivo)
```

## Execução 
Acessar:
[Execução](https://patrickcaloriocarvalho.github.io/test/2022/02/19/Script-Python-Backup-Mysql-Drive.html)

## Codigo Completo:
[Script-Python-Backup-MongoDB-Drive](https://github.com/PatrickCalorioCarvalho/Script-Python-Backup-MongoDB-Drive)


---
layout: post
title:  "Script Python Backup Mysql Drive"
date:   2022-02-19 14:49:00 -0300
categories: test
---
## Criando Token de Acesso ao Google Drive

Acessar Site:
[Console do desenvolvedor do Google](https://console.developers.google.com/)

Entre com Email:\
![TelaLoginGoogle](/assets/ScriptBackupMysqlDrive/TelaLoginGoogle.png)

Entre com Senha:\
![TelaSenhaGoogle](/assets/ScriptBackupMysqlDrive/TelaSenhaGoogle.png)

Click em ``` Home ```, depois em ``` CREATE PROJECT ``` \
![TelaCriarProjetoGoogle](/assets/ScriptBackupMysqlDrive/TelaCriarProjetoGoogle.png)

Entre com um ``` Project Name ```, depois click em ``` CREATE ``` \
![TelaNomeProjetoGoogle](/assets/ScriptBackupMysqlDrive/TelaNomeProjetoGoogle.png)

Click em ``` API & Services ```\
![TelaAPI&ServicesGoogle](/assets/ScriptBackupMysqlDrive/TelaAPI&ServicesGoogle.png)

Click em ```  ENABLE APIS AND SERVICES  ``` \
![TelaAPI&ServicesAtivarGoogle](/assets/ScriptBackupMysqlDrive/TelaAPI&ServicesAtivarGoogle.png)

Entre com um ``` Google Drive ```  na barra de pesquisa e Enter \
![TelaAPI&ServicesPesquisarGoogle](/assets/ScriptBackupMysqlDrive/TelaAPI&ServicesPesquisarGoogle.png)

Selecione ``` Google Drive ``` \
![TelaAPI&ServicesSelecionarGoogle](/assets/ScriptBackupMysqlDrive/TelaAPI&ServicesSelecionarGoogle.png)

Click em ```  ENABLE  ``` \
![TelaAPI&ServicesAtivar2Google](/assets/ScriptBackupMysqlDrive/TelaAPI&ServicesAtivar2Google.png)


Click em ```  CREATE CREDENTIALS  ``` \
![TelaAPI&ServicesGoogleDriveAPIAuth](/assets/ScriptBackupMysqlDrive/TelaAPI&ServicesGoogleDriveAPIAuth.png)

Click em ```  Credential  ``` \
![TelaAPI&ServicesGoogleDriveAPIConfig](/assets/ScriptBackupMysqlDrive/TelaAPI&ServicesGoogleDriveAPIConfig.png)

Click em ```  CREATE CREDENTIALS  ``` e depois ```  OAuth client ID  ``` \
![TelaAPI&ServicesGoogleDriveAPIClientID](/assets/ScriptBackupMysqlDrive/TelaAPI&ServicesGoogleDriveAPIClientID.png)

Click em ```  CONFIGURE CONSENT SCREEN  ``` \
![TelaAPI&ServicesGoogleDriveAPIConsent](/assets/ScriptBackupMysqlDrive/TelaAPI&ServicesGoogleDriveAPIConsent.png)

Selecione  ```  External  ``` e Click em ```  CREATE  ``` \
![TelaAPI&ServicesGoogleDriveAPIConsent2](/assets/ScriptBackupMysqlDrive/TelaAPI&ServicesGoogleDriveAPIConsent2.png)

Entre com um ``` App name ``` e Selecione um ```  Use support email  ``` \
![TelaAPI&ServicesGoogleDriveAPIConsent3](/assets/ScriptBackupMysqlDrive/TelaAPI&ServicesGoogleDriveAPIConsent3.png)

Entre com um ``` Email addresses ```, e Click em ```  SAVE AND CONTINUE  ``` \
![TelaAPI&ServicesGoogleDriveAPIConsent4](/assets/ScriptBackupMysqlDrive/TelaAPI&ServicesGoogleDriveAPIConsent4.png)

Click em ```  SAVE AND CONTINUE  ``` \
![TelaAPI&ServicesGoogleDriveAPIConsent5](/assets/ScriptBackupMysqlDrive/TelaAPI&ServicesGoogleDriveAPIConsent5.png)

Click em ```  + ADD USERS  ``` \
![TelaAPI&ServicesGoogleDriveAPIConsent6](/assets/ScriptBackupMysqlDrive/TelaAPI&ServicesGoogleDriveAPIConsent6.png)

Entre com seu ``` Email addresses ```, e Click em ```  ADD  ``` \
![TelaAPI&ServicesGoogleDriveAPIConsent6.1](/assets/ScriptBackupMysqlDrive/TelaAPI&ServicesGoogleDriveAPIConsent6.1.png)

Click em ```  SAVE AND CONTINUE  ``` \
![TelaAPI&ServicesGoogleDriveAPIConsent6.2](/assets/ScriptBackupMysqlDrive/TelaAPI&ServicesGoogleDriveAPIConsent6.2.png)

Click em ```  BACK TO DASHBOARD  ``` \
![TelaAPI&ServicesGoogleDriveAPIConsent7](/assets/ScriptBackupMysqlDrive/TelaAPI&ServicesGoogleDriveAPIConsent7.png)

Click em ```   Credentials  ``` , depois em  ```  CREATE CREDENTIALS  ``` e depois ```  OAuth client ID  ``` \
![TelaAPI&ServicesGoogleDriveAPIClientID2](/assets/ScriptBackupMysqlDrive/TelaAPI&ServicesGoogleDriveAPIClientID2.png)

Selecione um ```  Application Type ```, Entre com um ``` Name ``` e Click em ```   CREATE  ``` \
![TelaAPI&ServicesGoogleDriveAPIClientID3](/assets/ScriptBackupMysqlDrive/TelaAPI&ServicesGoogleDriveAPIClientID3.png)

Copie e reseve os valores de ```  client_id ``` e ```  client_secret ``` \
![TelaAPI&ServicesGoogleDriveAPIClientID4](/assets/ScriptBackupMysqlDrive/TelaAPI&ServicesGoogleDriveAPIClientID4.png)

## Configuração do Google Drive

Acessar site:
[Google Drive](https://drive.google.com)

Click em ```  NEW  ``` \
![TelaGoogleDrive](/assets/ScriptBackupMysqlDrive/TelaGoogleDrive.png)

Click em ```  Folder  ``` \
![TelaGoogleDrivePasta](/assets/ScriptBackupMysqlDrive/TelaGoogleDrivePasta.png)

Entre com ```  Name  ``` e Click em ```   Create  ``` \
![TelaGoogleDrivePasta2](/assets/ScriptBackupMysqlDrive/TelaGoogleDrivePasta2.png)

Click na Pasta Criada  \
![TelaGoogleDrivePasta3](/assets/ScriptBackupMysqlDrive/TelaGoogleDrivePasta3.png)

Copie e reserve o ``` FolderID ``` que esta na URL \
![TelaGoogleDrivePasta4](/assets/ScriptBackupMysqlDrive/TelaGoogleDrivePasta4.png)

## Configuração Python 

Se caso não tiver instalado ``` pip ``` execute esse comando
``` bash
sudo apt install python3-pip
```

Instalacao da  biblioteca ``` PyDrive ```
``` bash
pip install PyDrive
```

## Codigo 
O Diretorio do Projeto vai ficar assim
``` bash
.
└── Script-Python-Backup-Mysql-Drive
    ├── config.cnf
    ├── main.py
    ├── settings.yaml
    └── TestesBackup.sql
```

No Arquivo ``` config.cnf ```

 ``` bash
[client]
user = "USUARIO DE ACESSO AO BANCO"
password = "SENHA DE ACESSO AO BANCO"
host = "SERVIDOR DE BANCO"
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

O Arquivo ``` TestesBackup.sql ``` e so um Script de exemplo, caso precisar criar um Database de Teste
``` sql
Create database TestesBackup;
use TestesBackup;

create table TestesTabela
(
    IDTeste int not null auto_increment primary key,
    NomeTeste varchar(50)
);
insert into TestesTabela(NomeTeste) values('Teste01');
insert into TestesTabela(NomeTeste) values('Teste02');
insert into TestesTabela(NomeTeste) values('Teste03');
insert into TestesTabela(NomeTeste) values('Teste04');
insert into TestesTabela(NomeTeste) values('Teste05');
```
No arquivo ``` main.py ``` troque ``` COLOQUE_AQUI_SEU_FOLDERID ``` por ``` FOLDERID ```
``` python
from pydrive.auth import GoogleAuth
from pydrive.drive import GoogleDrive
import os
import datetime
gauth = GoogleAuth()           
drive = GoogleDrive(gauth) 
Database = "TestesBackup"
NomeArquivo = Database +"-"+datetime.datetime.now().strftime("%d-%m-%Y") +".sql.gz"
LocalArquivo  = '"'+os.getcwd() + "/" + NomeArquivo+'"'
LocalConfig = '"'+os.getcwd() + "/config.cnf" +'"'
os.system('mysqldump --defaults-extra-file='+ LocalConfig +' --databases '+Database+' -f | gzip > '+LocalArquivo+'')
gfile = drive.CreateFile({'parents': [{'id': 'COLOQUE_AQUI_SEU_FOLDERID'}]})
gfile.SetContentFile(NomeArquivo)
gfile.Upload()
os.system('rm '+LocalArquivo)
```
## Execução 

Execute o arquivo ``` main.py ``` usando ``` python3 main.py ```, a primeira execução será solicidado o acesso ao uma URL para salvar um aquivo de configuração do Google Drive  \
![PythonExecucao](/assets/ScriptBackupMysqlDrive/PythonExecucao.png)

Acesse a URL e Selecion o gmail que foi realizado a configuração no Cosole \
![PythonExecucao2](/assets/ScriptBackupMysqlDrive/PythonExecucao2.png)

Click em ```  Continue  ``` \
![PythonExecucao3](/assets/ScriptBackupMysqlDrive/PythonExecucao3.png)

Selecio as Caixa de Seleção e click em  ```  Continue  ``` \
![PythonExecucao4](/assets/ScriptBackupMysqlDrive/PythonExecucao4.png)


Agora so esperar o Codigo Finalizar
![PythonExecucao5](/assets/ScriptBackupMysqlDrive/PythonExecucao5.png)

Ao Finalizar será Criado um aquivo ``` credentials.json ``` que sera usado nas proximas execução do script não será mais solicidado nada

Resultado
![Resultado](/assets/ScriptBackupMysqlDrive/Resultado.png)

## Codigo Completo:
[Script-Python-Backup-Mysql-Drive](https://github.com/PatrickCalorioCarvalho/Script-Python-Backup-Mysql-Drive)


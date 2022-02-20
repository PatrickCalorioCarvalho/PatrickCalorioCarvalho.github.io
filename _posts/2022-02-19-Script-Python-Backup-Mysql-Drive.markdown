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

Click em ``` Home ```, depois em ``` CREATE PROJECT ``` 
![TelaCriarProjetoGoogle](/assets/ScriptBackupMysqlDrive/TelaCriarProjetoGoogle.png)

Entre com um ``` Project Name ```, depois click em ``` CREATE ``` 
![TelaNomeProjetoGoogle](/assets/ScriptBackupMysqlDrive/TelaNomeProjetoGoogle.png)

Click em ``` API & Services ```
![TelaAPI&ServicesGoogle](/assets/ScriptBackupMysqlDrive/TelaAPI&ServicesGoogle.png)

Click em ```  ENABLE APIS AND SERVICES  ```
![TelaAPI&ServicesAtivarGoogle](/assets/ScriptBackupMysqlDrive/TelaAPI&ServicesAtivarGoogle.png)

Entre com um ``` Google Drive ```  na barra de pesquisa e Enter
![TelaAPI&ServicesPesquisarGoogle](/assets/ScriptBackupMysqlDrive/TelaAPI&ServicesPesquisarGoogle.png)

Selecione ``` Google Drive ``` 
![TelaAPI&ServicesSelecionarGoogle](/assets/ScriptBackupMysqlDrive/TelaAPI&ServicesSelecionarGoogle.png)

Click em ```  ENABLE  ```
![TelaAPI&ServicesAtivar2Google](/assets/ScriptBackupMysqlDrive/TelaAPI&ServicesAtivar2Google.png)








Acessar Drive https://drive.google.com



##Cinfigurando Python 

Se caso nao tiver instaldo PIP execute esse comando
``` bash
sudo apt install python3-pip
```

Instalar Biblioteca ``` PyDrive ```
``` bash
pip install PyDrive
```



---
title:  "HomeLabDevelopment"
subtitle: "Proxmox, Terraform e Ansible provisionando um homelab com GPU"
image: "img/HomeLabDevelopment.svg"
date: 2026-09-20
---

## Descrição
O **HomeLabDevelopment** unifica Terraform e Ansible num único fluxo para provisionar (e reprovisionar) um homelab Proxmox de forma reprodutível, sem passos manuais. A ideia central: um único `terraform apply` sobe uma VM e dois containers LXC no host Proxmox e, assim que cada um recebe IP, o próprio Terraform já dispara o playbook Ansible correspondente para instalar o software daquele nó — tudo idempotente e reaplicável a qualquer momento. A arquitetura final inclui uma VM com Docker (Portainer, Open WebUI e observabilidade via SigNoz), um LXC com Ollama acelerado por GPU NVIDIA e um LXC com PostgreSQL.

## Tecnologias Utilizadas
- **Virtualização**: Proxmox VE (VM + LXC)
- **IaC**: Terraform (provider `bpg/proxmox`)
- **Configuração**: Ansible (playbooks YAML)
- **Containers**: Docker, Portainer
- **IA local**: Ollama com aceleração por GPU NVIDIA
- **Observabilidade**: SigNoz
- **Banco de dados**: PostgreSQL
- **Scripting**: Bash, PowerShell, WSL como ponte entre Windows e Ansible

## Desafios de Desenvolvimento
- A primeira versão usava passthrough completo de GPU (VFIO) para dentro de uma VM, e isso derrubava o host inteiro por causa de um bug conhecido de reset em GPUs NVIDIA de consumo. A solução foi migrar para device passthrough dentro de um LXC, mantendo o driver no host.
- O driver NVIDIA dentro do container precisa bater exatamente com a versão do módulo de kernel do host, senão a comunicação com a GPU simplesmente falha.
- Containers LXC privilegiados usam por padrão um perfil de segurança sem suporte a namespace de cgroup, o que travava a rede silenciosamente — resolvido habilitando nesting explicitamente.
- Chamar Ansible a partir do Terraform no Windows via WSL quebrava por causa de aninhamento de aspas entre PowerShell, WSL e Bash — resolvido com um script intermediário e uma convenção fixa de argumentos.

## Repositório
[github.com/PatrickCalorioCarvalho/HomeLabDevelopment](https://github.com/PatrickCalorioCarvalho/HomeLabDevelopment)

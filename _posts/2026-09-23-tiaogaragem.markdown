---
title:  "Tião Garagem"
subtitle: "Diário de bordo offline para carro e moto"
image: "img/TiaoGaragem.svg"
date: 2026-09-23
---

## Descrição
O **Tião Garagem** é o "diário de bordo" do veículo: um app Android que ajuda a não esquecer troca de óleo, vencimento de IPVA/licenciamento e o estado geral do carro ou da moto ao longo do tempo. A ideia central é ser 100% local e offline — os dados ficam salvos direto no celular, sem depender de servidor próprio, com notificações locais avisando sobre pendências e um botão de backup manual no Google Drive para não perder o histórico. O app também integra a tabela FIPE para acompanhar a valorização do veículo e tem um widget de tela inicial mostrando qual veículo precisa de manutenção mais urgente.

## Tecnologias Utilizadas
- **Framework**: React Native + Expo (TypeScript)
- **Banco de dados**: SQLite local, com migrações incrementais próprias
- **Backup**: Google Sign-In nativo + Google Drive API
- **Notificações**: notificações locais para lembrar de manutenções e documentos
- **Widget**: widget de tela inicial Android mostrando a manutenção mais urgente
- **API externa**: Tabela FIPE (valor de mercado do veículo)
- **CI/CD**: GitHub Actions gerando o APK a cada build

## Desafios de Desenvolvimento
- Evoluir o schema do banco local sem depender de uma biblioteca de migração, criando uma estratégia própria que verifica a estrutura das tabelas antes de aplicar cada alteração — importante para não quebrar instalações já existentes no celular do usuário.
- Construir o widget de tela inicial do Android, que usa um sistema de layout bem mais limitado que o resto do app e exigiu várias rodadas de ajuste até o tamanho e o redimensionamento ficarem corretos.
- Trocar a abordagem de login para o backup no Google Drive por uma solução nativa mais robusta depois da primeira versão.
- Estabilizar o pipeline de build no CI, incluindo o travamento de versões de dependências para builds reprodutíveis.

## Acesso
- [Página de download do app](https://patrickcaloriocarvalho.github.io/TiaoGaragem/)
- APK direto: [releases mais recentes](https://github.com/PatrickCalorioCarvalho/TiaoGaragem/releases/latest/download/TiaoGaragem.apk)

## Repositório
[github.com/PatrickCalorioCarvalho/TiaoGaragem](https://github.com/PatrickCalorioCarvalho/TiaoGaragem)

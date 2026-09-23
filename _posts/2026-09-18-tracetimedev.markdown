---
title:  "TraceTime"
subtitle: "Cronômetro de bandeja que lança tempo direto no GitLab"
image: "img/TraceTimeDev.png"
date: 2026-09-18
---

## Descrição
O **TraceTime** ataca um atrito bem comum: registrar horas trabalhadas em issues do GitLab é chato e acaba sendo deixado de lado. A ideia central é reduzir esse atrito ao máximo — um ícone fica na bandeja do sistema, o desenvolvedor escolhe grupo, projeto, issue e o tipo de trabalho, e aperta iniciar. O app cronometra localmente, com suporte a pausar e retomar, e ao finalizar abre um modal para confirmar o tempo antes de enviá-lo direto para a API do GitLab. O objetivo declarado no projeto é padronizar como um time registra tempo, usando labels consistentes (dev, bug, meeting) para categorizar os lançamentos.

## Tecnologias Utilizadas
- **Frontend**: React 19 + TypeScript, Vite
- **Desktop shell**: Rust + Tauri 2
- **Banco local**: SQLite (via rusqlite)
- **Integração**: API do GitLab v4 (autenticação por Personal Access Token)
- **CI/CD**: GitHub Actions publicando instaladores Windows automaticamente a cada push

## Desafios de Desenvolvimento
- Garantir que uma sessão de cronômetro nunca fique "perdida" rodando: ao reabrir o app após um fechamento inesperado, ele busca a última sessão salva e força seu status para pausada, fechando o intervalo em aberto.
- Construir uma janela de bandeja sem decoração, ancorada matematicamente num canto da tela, que se esconde ao perder o foco — exigindo lógica própria de posicionamento e eventos de janela, além de garantir instância única do app.
- Suportar GitLab self-hosted com certificado próprio, o que exigiu tratar certificados TLS não confiáveis nas chamadas HTTP.
- Formatar a duração da sessão exatamente no padrão que a API de time tracking do GitLab espera.

## Acesso
- [Documentação e apresentação do projeto](https://patrickcaloriocarvalho.github.io/TraceTimeDev/)
- Instaladores para Windows publicados a cada versão em [GitHub Releases](https://github.com/PatrickCalorioCarvalho/TraceTimeDev/releases)

## Repositório
[github.com/PatrickCalorioCarvalho/TraceTimeDev](https://github.com/PatrickCalorioCarvalho/TraceTimeDev)

---
title:  "ByteGasto"
subtitle: "Controle de gastos por voz, direto no Telegram, com IA rodando em casa"
image: "img/ByteGasto.png"
date: 2026-09-16
---

## Descrição
O **ByteGasto** ataca o atrito de anotar gastos manualmente: em vez de abrir uma planilha, o usuário manda um áudio para o bot no Telegram contando o que gastou (ou envia foto de comprovante, PDF ou extrato bancário), e o sistema transcreve, extrai valor/categoria/descrição por meio de um agente de IA local e grava tudo num banco de dados após confirmação. A ideia central é "tudo local, nada de cloud paga": transcrição, IA e banco de dados rodam em infraestrutura própria, o que também motivou um cuidado extra com privacidade dos dados do usuário. O projeto evoluiu para casos mais realistas de finanças pessoais, como parcelamentos com lançamento automático mensal e relatórios em PDF por categoria.

## Tecnologias Utilizadas
- **Linguagem**: Python
- **Bot**: python-telegram-bot
- **IA local**: Ollama (modelo pequeno rodando em CPU), orquestração de agentes via LangGraph
- **Transcrição de voz**: OpenAI Whisper
- **OCR/Documentos**: Tesseract OCR, leitura de PDF e de extratos bancários (OFX/QFX)
- **Banco de dados**: PostgreSQL
- **Relatórios**: ReportLab (PDF), Matplotlib (gráficos)
- **Observabilidade**: OpenTelemetry exportando para SigNoz self-hosted

## Desafios de Desenvolvimento
- Equilibrar privacidade e usabilidade: valor e categoria ficam em texto plano no banco (para permitir consultas agregadas direto em SQL), enquanto o texto bruto do gasto é criptografado e o identificador do usuário passa por hash irreversível.
- Gerenciar segredos criptográficos que, uma vez usados para gravar dados, nunca mais podem ser trocados sem tornar os gastos antigos ilegíveis.
- Diagnosticar falhas num pipeline com várias etapas assíncronas (transcrição → IA → banco → resposta no Telegram) sem instrumentação — resolvido subindo observabilidade própria em vez de espalhar logs manuais.
- Extrair dados estruturados (valor, categoria, descrição) de forma confiável usando um modelo de linguagem pequeno rodando em CPU, sem GPU dedicada.

## Repositório
[github.com/PatrickCalorioCarvalho/ByteGasto](https://github.com/PatrickCalorioCarvalho/ByteGasto)

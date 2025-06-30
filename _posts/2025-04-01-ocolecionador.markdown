---
title:  "OColecionador"
subtitle: "Projeto de Classificação de Imagens com MinIO e TensorFlow"
image: "img/OColecionador.png"
date: 2025-04-01
---
# OColecionador - Projeto de Classificação de Imagens com MinIO e TensorFlow

## Descrição
O **OColecionador** tem como objetivo capturar imagens pelo aplicativo mobile (React Native), enviá-las para um backend em Node.js, armazená-las em um bucket no MinIO e gerar automaticamente variações dessas imagens (rotação e mudança de coloração) para treinamento de um modelo de classificação com Python e TensorFlow. O modelo treinado pode ser utilizado posteriormente pelo backend ou por outro serviço para classificação automática de imagens.

Além de armazenar a imagem original no MinIO, o backend também salva no banco de dados MongoDB informações sobre a imagem, incluindo o usuário, o ID da imagem no bucket e outros metadados relevantes.

Além disso, toda vez que uma imagem é enviada para o backend, ele realiza uma requisição para uma API em Python que utiliza o modelo mais atualizado do treinamento para classificar a imagem e retornar a categoria correspondente. Essa categoria também é armazenada no banco de dados MongoDB.

## Tecnologias Utilizadas
- **Frontend**: React Native
- **Backend**: Node.js
- **Armazenamento**: MinIO
- **Banco de Dados**: MongoDB
- **Processamento e Treinamento**: Python, TensorFlow
- **API de Classificação**: Python (Flask/FastAPI) + Modelo treinado em TensorFlow

## Fluxo do Sistema
1. O usuário captura uma imagem pelo aplicativo React Native.
2. A imagem é enviada para o backend Node.js.
3. O backend salva a imagem original em um bucket no MinIO.
4. O backend registra no MongoDB informações sobre a imagem (usuário, ID no bucket e metadados).
5. O backend faz uma requisição para a API de classificação em Python com a imagem.
6. A API de classificação retorna a categoria correspondente baseada no modelo mais atualizado.
7. O backend salva a categoria da imagem no MongoDB.
8. O backend gera variações da imagem (rotação e coloração) e as armazena em outro bucket no MinIO.
9. Um processo de treinamento em Python e TensorFlow consome essas imagens para gerar um modelo de classificação.
10. O modelo treinado pode ser utilizado pelo backend ou outro serviço para classificação automática de novas imagens enviadas.


## Conclusão
O **OColecionador** fornece um pipeline completo para captura, armazenamento, processamento, treinamento e classificação de imagens. Com a automação da geração de variações das imagens, garantimos um conjunto de dados mais robusto para o treinamento do modelo de classificação. Além disso, a integração com a API de classificação permite que cada nova imagem enviada seja automaticamente categorizada com base no modelo mais atualizado.


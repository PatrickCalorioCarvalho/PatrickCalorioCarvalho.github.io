---
title:  "DroneAutoCuts"
subtitle: "Highlights automáticos de filmagens de drone com visão computacional"
image: "img/DroneAutoCuts.svg"
date: 2026-09-15
---

## Descrição
O **DroneAutoCuts** resolve o problema de editar manualmente horas de filmagem de drone para tirar dali só os melhores momentos. É um pipeline totalmente automatizado: os vídeos são normalizados e concatenados com ffmpeg, o corte em cenas é feito com detecção de conteúdo (PySceneDetect), e cada cena recebe uma pontuação combinando nitidez, brilho, presença de pessoas (YOLOv8) e a qualidade do movimento de câmera (analisado via optical flow) — descartando cenas tremidas e valorizando sobrevoos estáveis. As 20% cenas com maior pontuação são selecionadas, cortadas, aceleradas quando a câmera está parada, e recebem uma LUT cinematográfica de color grading antes de virar um highlight pronto tanto em formato horizontal quanto vertical (9:16) para redes sociais.

## Tecnologias Utilizadas
- **Linguagem**: Python
- **Visão computacional**: OpenCV (nitidez via Laplaciano, brilho, optical flow denso), Ultralytics YOLOv8 (detecção de pessoas), PyTorch
- **Detecção de cena**: PySceneDetect (ContentDetector)
- **Processamento de vídeo**: FFmpeg (normalização, corte, aceleração, LUT 3D, exportação vertical)
- **Infra**: Docker + Docker Compose, imagem baseada em CUDA com fallback para CPU (`USE_GPU`)

## Desafios de Desenvolvimento
- Rodar em CPU no ambiente de desenvolvimento e em GPU em produção sem quebrar nada — todo o pipeline foi desenhado para alternar entre `libx264` e `h264_nvenc` conforme a variável `USE_GPU`.
- Analisar cada cena (nitidez + brilho + inferência de YOLO + optical flow por frame) é computacionalmente pesado, exigindo paralelizar a análise das cenas com um pool de threads e permitir ajustar a taxa de amostragem de frames.
- A parte mais delicada foi separar "movimento de câmera intencional" (sobrevoo suave) de "tremedeira indesejada" usando optical flow — cenas muito instáveis são descartadas, e cenas com movimento suave e moderado ganham bônus na pontuação.

## Repositório
[github.com/PatrickCalorioCarvalho/DroneAutoCuts](https://github.com/PatrickCalorioCarvalho/DroneAutoCuts)

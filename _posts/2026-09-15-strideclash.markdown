---
title:  "StrideClash"
subtitle: "Conquiste território real caminhando, com GPS e PostGIS"
image: "img/StrideClash.svg"
date: 2026-09-15
---

## Descrição
O **StrideClash** transforma caminhada real em um jogo de conquista de território: o jogador caminha com o app aberto, o GPS registra o trajeto, e ao fechar o caminho perto do ponto de partida um polígono geográfico real é criado e sua área é contabilizada como território capturado. A ideia central é competir por área de verdade, e não por uma pontuação abstrata — se a caminhada de um jogador se sobrepõe a um território já capturado por outro, o servidor recorta a fatia disputada do polígono mais antigo, com uma regra de desempate simples: quem sincroniza por último com o servidor fica com a área em disputa. Campeonatos têm período e região definidos, com ranking pela área total capturada.

## Tecnologias Utilizadas
- **Mobile**: Flutter/Dart, gRPC + Protobuf, Geolocator (GPS), Google Sign-In
- **Backend**: Go, gRPC como única API, arquitetura em camadas (repository → service → gRPC)
- **Geoespacial**: PostgreSQL + PostGIS para cálculo de área e sobreposição de polígonos
- **Cache**: Redis (ranking)
- **Infra**: Docker Compose, ngrok para expor o backend publicamente
- **CI/CD**: GitHub Actions gerando o APK a cada push

## Desafios de Desenvolvimento
- Resolver sobreposição de território com geometria real: quando uma nova caminhada invade um polígono já capturado, o backend usa operações de diferença geométrica do PostGIS para recortar apenas a fatia disputada e recalcular a área.
- Trajetos que cruzam o próprio caminho geram polígonos geometricamente inválidos — foi necessário validar/corrigir a geometria antes de qualquer cálculo de área, ou o banco geoespacial simplesmente recusava a operação.
- A keystore de build gerada automaticamente pelo CI mudava a cada execução, o que quebrava o login social (vinculado à assinatura do app) — resolvido fixando uma keystore de release nos segredos do pipeline.
- Expor o backend gRPC publicamente por um túnel gratuito exigiu usar HTTP/2 em texto plano (com TLS terminado na borda do túnel), já que o gRPC já fala esse protocolo nativamente.

## Acesso
Build de teste para Android disponível para download direto (fora da Play Store) em [github.com/PatrickCalorioCarvalho/StrideClash/releases](https://github.com/PatrickCalorioCarvalho/StrideClash/releases/latest/download/StrideClash.apk).

## Repositório
[github.com/PatrickCalorioCarvalho/StrideClash](https://github.com/PatrickCalorioCarvalho/StrideClash)

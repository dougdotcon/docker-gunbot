# Docker Gunbot

![GitHub stars](https://img.shields.io/github/stars/magicdude4eva/docker-gunbot?style=social)
![GitHub forks](https://img.shields.io/github/forks/magicdude4eva/docker-gunbot?style=social)
![GitHub issues](https://img.shields.io/github/issues/magicdude4eva/docker-gunbot)
![Docker Pulls](https://img.shields.io/docker/pulls/magicdude4eva/gunbot-colorised)
![Docker Stars](https://img.shields.io/docker/stars/magicdude4eva/gunbot-colorised)
[![GitHub last commit](https://img.shields.io/github/last-commit/magicdude4eva/docker-gunbot.svg)](https://github.com/magicdude4eva/docker-gunbot/commits/master)

## Visão Geral

Este projeto fornece um container Docker para executar o Gunbot, um robô de trading automatizado de criptomoedas. Ele é otimizado para Synology NAS (DSM 6.0 e 7.0), mas é compatível com qualquer ambiente Docker padrão. A imagem é construída sobre uma base mínima Glibc e inclui saída colorida para melhor legibilidade dos logs.

**Versão Suportada:** Gunbot v29.3.6

## ⚠️ Aviso Legal

O trading de criptomoedas envolve riscos significativos e pode resultar em grandes perdas financeiras. O software é fornecido "no estado em que se encontra" sem garantia de qualquer tipo. **Você é o único responsável por suas decisões de trading e por seus fundos.** Não arrisque dinheiro que não pode perder. O autor não é um consultor financeiro e não fornece aconselhamento financeiro.

## Características

*   **Otimizado para Synology:** Configuração pronta para uso em NAS Synology.
*   **Saída Colorida:** Melhora nos logs do console para melhor monitoramento.
*   **Imagem Base Mínima:** Eficiente e leve.
*   **Suporte a Autoconfig:** Inclui uma configuração de exemplo para iniciar rapidamente (use com cautela).

## Início Rápido

### 1. Estrutura de Diretórios

Crie um diretório em sua máquina host para armazenar configurações e logs:

bash
mkdir -p /caminho/para/gunbot/config
cd /caminho/para/gunbot/config


### 2. Configuração

Coloque seus arquivos de configuração do Gunbot no diretório `config`. Se você estiver usando a autoconfig fornecida, leia as instruções com atenção antes de prosseguir.

### 3. Executando o Container

Use o Docker Compose para uma melhor experiência:

yaml
version: '3'

services:
  gunbot:
    image: magicdude4eva/gunbot-colorised:latest
    container_name: gunbot
    restart: unless-stopped
    volumes:
      - ./config:/app/config
    environment:
      - PUID=1024
      - PGID=100
      - TZ=UTC


Alternativamente, execute com `docker run`:

bash
docker run -d \
  --name gunbot \
  --restart unless-stopped \
  -v /caminho/para/gunbot/config:/app/config \
  -e PUID=1024 \
  -e PGID=100 \
  -e TZ=UTC \
  magicdude4eva/gunbot-colorised:latest


*   Ajuste `PUID` e `PGID` para corresponder aos IDs de usuário/grupo do seu host (use `id seuusuario` para encontrá-los).
*   Ajuste `/caminho/para/gunbot/config` para o seu caminho real.

## Documentação

Para detalhes sobre o uso e configuração do Gunbot, consulte a documentação oficial:
[https://wiki.gunthy.org/](https://wiki.gunthy.org/)

## Suporte

Se você encontrar problemas, verifique a página de [issues do repositório GitHub](https://github.com/magicdude4eva/docker-gunbot).

# Docker Gunbot

![GitHub stars](https://img.shields.io/github/stars/magicdude4eva/docker-gunbot?style=social)
![GitHub forks](https://img.shields.io/github/forks/magicdude4eva/docker-gunbot?style=social)
![GitHub issues](https://img.shields.io/github/issues/magicdude4eva/docker-gunbot)
![Docker Pulls](https://img.shields.io/docker/pulls/magicdude4eva/gunbot-colorised)
![Docker Stars](https://img.shields.io/docker/stars/magicdude4eva/gunbot-colorised)
[![GitHub last commit](https://img.shields.io/github/last-commit/magicdude4eva/docker-gunbot.svg)](https://github.com/magicdude4eva/docker-gunbot/commits/master)
[![Build and Push Docker image](https://github.com/magicdude4eva/docker-gunbot/actions/workflows/docker-build.yml/badge.svg)](https://github.com/magicdude4eva/docker-gunbot/actions/workflows/docker-build.yml)

## Overview

This project provides a Docker container for running Gunbot, a automated cryptocurrency trading bot. It is specifically optimized for Synology NAS (DSM 6.0 and 7.0) but is compatible with any standard Docker environment. The image is built on a minimal Glibc base and includes colorized output for better log readability.

**Supported Version:** Gunbot v29.3.6

## ⚠️ Disclaimer

Trading cryptocurrencies involves significant risk and can result in substantial financial loss. The software is provided "as is" without any warranty. **You are solely responsible for your trading decisions and funds.** Do not risk money you cannot afford to lose. The author is not a financial advisor and does not provide financial advice.

## Features

*   **Optimized for Synology:** Ready-to-use configuration for Synology NAS.
*   **Colorized Output:** Enhanced console logs for better monitoring.
*   **Minimal Base Image:** Efficient and lightweight.
*   **Autoconfig Support:** Includes a sample configuration to get started quickly (use with caution).

## Quick Start

### 1. Directory Structure

Create a directory on your host machine to store configuration and logs:

bash
mkdir -p /path/to/gunbot/config
cd /path/to/gunbot/config


### 2. Configuration

Place your Gunbot configuration files in the `config` directory. If you are using the provided autoconfig, read the instructions carefully before proceeding.

### 3. Running the Container

Use Docker Compose for the best experience:

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


Alternatively, run with `docker run`:

bash
docker run -d \
  --name gunbot \
  --restart unless-stopped \
  -v /path/to/gunbot/config:/app/config \
  -e PUID=1024 \
  -e PGID=100 \
  -e TZ=UTC \
  magicdude4eva/gunbot-colorised:latest


*   Adjust `PUID` and `PGID` to match your host user/group IDs (use `id youruser` to find them).
*   Adjust `/path/to/gunbot/config` to your actual path.

## Documentation

For detailed Gunbot usage and configuration options, please refer to the official documentation:
[https://wiki.gunthy.org/](https://wiki.gunthy.org/)

## Support

If you encounter issues, please check the [GitHub repository issues](https://github.com/magicdude4eva/docker-gunbot) page.

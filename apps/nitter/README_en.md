# Nitter Introduction

## Overview

Nitter is a free and open-source, privacy-focused alternative Twitter/X front-end. It does not rely on JavaScript, shows no ads, performs no tracking, and has no paywalls. You can browse tweets, timelines and search results without logging in, making it ideal for anonymous self-hosted access to Twitter/X.

This app also bundles a Redis service for caching, so it works out of the box without installing Redis separately in 1Panel.

## Key Features

- **Privacy-friendly**: No login, no tracking, no ads, no JavaScript
- **Lightweight & fast**: Minimal pages, less bandwidth when browsing tweets and media
- **RSS support**: Built-in RSS feeds for users, lists and search keywords
- **Multiple themes**: Several interface themes, customizable link replacement and preferences
- **Bundled Redis cache**: Better performance, fewer repeated requests to Twitter/X
- **Multi-architecture**: Image supports both amd64 and arm64

## Usage

1. After installation, visit `http://server-ip:port`.
2. Most configuration lives in `nitter.conf`, under the `data/` folder of the app directory:
   - Set `hostname` under `[Server]` to your domain or IP so links are generated correctly.
   - Set `hmacKey` under `[Config]` to a random value (e.g. `openssl rand -hex 32`) to sign media URLs.
   - For HTTPS, use a reverse proxy (e.g. a 1Panel website) and keep `https` set to `false`.
3. Restart the app after changing the configuration.
4. Redis data is stored in `data/redis`; the cache can be safely cleared without affecting usage.

## Notes

- `nitter.conf` must exist; do not delete it or turn it into a directory.
- For optional cookie sessions, place a `sessions.jsonl` under `data/` and mount it into the container following the official docs.

## Links

- [Nitter repository](https://github.com/zedeus/nitter)
- [Nitter documentation](https://github.com/zedeus/nitter/blob/master/README.md)

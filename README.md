# My Home

A household budget for one or more people: income, bills, savings goals and the money flow
between your accounts. It runs on your own server (a NAS or a PC with Docker), keeps your data
at home, and works on your phone, even offline.

**How it looks and how to install it, in English and Dutch:
<https://codingstukka.github.io/my-home/>**

## In short

```sh
mkdir my-home && cd my-home
curl -fsSLO https://raw.githubusercontent.com/CodingStukka/my-home/main/compose.yaml
curl -fsSL -o .env https://raw.githubusercontent.com/CodingStukka/my-home/main/.env.example
# In .env: POSTGRES_PASSWORD and APP_SECRET, each from `openssl rand -hex 32`
docker compose up -d
```

Then open `http://<server>:9090/admin/setup` and create the first account: it's the admin.
Phones install the app only over https, through a reverse proxy: the site explains how.

## What's here

- [`compose.yaml`](compose.yaml): the app, its database, a nightly backup into `./backups`
  and an optional updater (Watchtower, every night at 04:00).
- [`.env.example`](.env.example): the settings, with how to make the two secrets.
- The site, shown at the address above.

The app itself is the image `ghcr.io/codingstukka/my-home` (`latest`, or a day like
`2026.10.29`). To update by hand: `docker compose pull && docker compose up -d`.

# Volunteer Photo Hours

Turns phone photos into volunteer hours and a volunteer report.

## Run it

```
docker compose up -d
```

Open http://volunteers.localhost:8088/

Firefox and Chrome send any `*.localhost` address to your own computer automatically.
If it doesn't load, add this line to `/etc/hosts`:

```
127.0.0.1 volunteers.localhost
```

To use a different port, copy `.env.example` to `.env` and change `NGINX_PORT`.

## Your data

Everything you enter is saved to `data/volunteer-data.json`, with one dated copy
per day in `data/backups/`. It's also kept in the browser as a second copy.
Back up the `data/` folder along with your photos.

The files in `data/` are owned by the container's nginx user, so use `sudo` to
delete or move them.

## Update the app (hot reload)

The app is split in two:

- `public/index.html` is a small loader that holds your loaded photos in browser memory.
- `public/app.html` is the app itself.

Replace or edit `public/app.html` and the open page picks it up within a couple of
seconds, keeping the photos you've already loaded. It waits while you're typing,
reading photos, or have the viewer or report open. Nothing is uploaded or copied.

Only a change to `index.html` itself needs a normal page refresh.

## Stop it

```
docker compose down
```
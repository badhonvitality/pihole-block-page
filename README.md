# Blocker - Pi-hole Block Page

A custom "Access Blocked" landing page built for Pi-hole and other DNS sinkhole
setups. It ships as a single static page with animated terminal UI, matrix
background, and optional audio cues.

## Why this exists

Pi-hole users often want a clear, attention-grabbing block page. This page is
designed to look like a security gateway, while keeping everything in one
portable `index.html` file plus audio assets.

## Features

- Animated loader terminal with progress and typing effect
- Matrix background, scanlines, and CRT glow
- Fullscreen kiosk button
- Hidden scrollbars with smooth scroll support
- Optional audio: typing during loader, siren on main screen
- Responsive layout for mobile and desktop

## Files

- `index.html` - the full UI and logic
- `typing.mp3` - loader typing sound (looped)
- `siren.mp3` - main screen siren (looped)

## Quick start

Open `index.html` in a browser and click once to enable audio if your browser
blocks autoplay.

## Pi-hole integration (lighttpd default)

Paths vary by install, but the default Pi-hole web root is usually
`/var/www/html/pihole/`. A common approach is to point the 404 handler to this
page so blocked domains show it.

1) Copy files to your Pi-hole web root:

```bash
sudo cp index.html typing.mp3 siren.mp3 /var/www/html/pihole/
```

2) Edit the Pi-hole blocking config:

```bash
sudo nano /etc/lighttpd/conf-enabled/15-pihole-blocking.conf
```

3) Set the 404 handler to this page (example):

```
server.error-handler-404 = "/pihole/index.html"
```

4) Restart lighttpd:

```bash
sudo systemctl restart lighttpd
```

If your setup uses a different web server or a custom path, adjust accordingly.

## Customization

- Text and labels: update headings and list items in `index.html`.
- Colors: edit CSS variables under `:root`.
- Audio: swap the `*.mp3` files with your own or adjust volumes in the script.

## SEO keywords

Pi-hole block page, pihole, dns sinkhole, custom block page, access blocked,
security gateway, captive portal, blocked site page

## License

MIT. See `LICENSE`.

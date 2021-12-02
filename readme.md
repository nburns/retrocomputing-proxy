# About
This is an nginx config for allowing computers with limited/old/no https support to browse the internet

# Install & Setup
- You'll need:
    - nginx installed with the subs_filter module
    - an older computer
    - a newer computer
- Test it out
```fish
nginx -c debug.conf -p (pwd)
```

- add a HTTP Web Proxy system wide or in your browser's settings to point to the host and port running the proxy
<img width="500rem" src="https://raw.githubusercontent.com/wiki/nburns/retrocomputing-proxy/images/proxy-setup.png" alt="Setup Example on macOS">

- `http-proxy.conf` can be symlinked to `/etc/nginx/sites-enabled/http-proxy.conf` on ubuntu/debian

# Bugs
- Currently this will naively replace all instances of `https` with `http` in the body which could break things
- Headers other than `Location` ie application specific headers may not be modified to http in the response to the client

# Contributing
- PR's are welcome

## Features
- a more correct https proxy for clients that support https but may not have
support for current cipher suites

# Inspiration
The original implementation here had a few issues, this config adds support for:
- modifying `Location` headers
- HTTPS SNI
- more "complete" munging of https to http

https://retrocomputing.stackexchange.com/questions/17680/how-can-i-visit-https-websites-in-old-web-browsers




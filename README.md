# notbadholdings.it

Redirects **notbadholdings.it** to <https://notbadholdings.com/>. No content of its own.

GitHub Pages only serves static files, so there is no server-side 301. The
redirect is done in `index.html` three ways at once:

| mechanism | who it serves |
| --- | --- |
| `<link rel="canonical">` | search engines — consolidates ranking onto the target |
| `<meta http-equiv="refresh">` | browsers with JavaScript disabled |
| `location.replace()` | everyone else; no extra browser-history entry |

`404.html` is a copy of `index.html`, so *any* path on this domain
redirects rather than showing the GitHub 404 page.

## DNS

Point the apex at GitHub Pages:

```
A     @   185.199.108.153
A     @   185.199.109.153
A     @   185.199.110.153
A     @   185.199.111.153
AAAA  @   2606:50c0:8000::153
AAAA  @   2606:50c0:8001::153
AAAA  @   2606:50c0:8002::153
AAAA  @   2606:50c0:8003::153
```

The TLS certificate is issued automatically once those resolve; until then
the domain works over HTTP only. Enable "Enforce HTTPS" in Settings → Pages
after the certificate appears.

## Changing the target

The destination is hardcoded in `index.html` and `404.html` — change it in
both, or regenerate them.

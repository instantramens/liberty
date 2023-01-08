You can explore other options for deployment [here](https://github.com/titaniumnetwork-dev/Ultraviolet-App#deployment).

## Static Hosting

Many static website solutions will compile websites using a dedicated container/VM, however they will run into errors such as not being able to find the public directory because this repository is configured to serve the static files in conjunction with proxies and databases.

---

Known services that Ultraviolet-App can't be deployed to:

### Vercel

Vercel cannot start Ultraviolet-App because Vercel is a [static host](#static-hosting).

### Cloudflare Pages

Cloudflare Pages cannot start Ultraviolet-App because Cloudflare Pages is a [static host](#static-hosting).

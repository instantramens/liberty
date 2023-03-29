# Configure SSL

If you came here from [[Deploy via terminal]], you may have encountered an error such as:

- When using Ultraviolet: `HTTPS must be enabled to use this proxy`

This guide assumes the following:

- You have a server
- You have a domain

> If you don't have any of the above, **THIS WILL NOT WORK**.

## Approach #1: Cloudflare

This approach assumes the following:

- **You have configured Ultraviolet-App to listen on port 80.**

> If you don't have any of the above, **THIS WILL NOT WORK without modifications**.

This is by the easiest method, which involves letting Cloudflare handle SSL for you.

Instructions:

1. Add your domain to Cloudflare and follow their instructions to change your nameservers
2. Wait for the nameserver change to complete
3. Add a DNS record to your domain so Cloudflare can reach your server

   | Type | Name        | Content                 | Proxied status             | TTL  |
   | ---- | ----------- | ----------------------- | -------------------------- | ---- |
   | A    | example.com | your.servers.ip.address | :white_check_mark: Proxied | auto |

4. Enter your domain name into your browser. If you see an error about something SSL, you may need to wait for Cloudflare to issue your SSL certificate. This can take up to 1-2 hours.

## Approach #2: Reverse Proxy (NGINX)

This approach assumes the following:

- **You have configured Ultraviolet-App to listen on port 8080.**

> If you don't have any of the above, **THIS WILL NOT WORK without modifications**.

This approach is more advanced.

This tutorial assumes your domain (eg. example.com) has an A record similar to the one above. As long as it points to your server.

Instructions:

1. Install NGINX on your server.
2. Setup some directives

   `/etc/nginx/sites-enabled/proxy.conf`

   ```nginx
   upstream Ultraviolet-App {
      server 127.0.0.1:8080;
   }

   server {
      server_name www.example.com example.com;
      listen 80;

         # Redirect users on www.example.com to example.com
         # (www to apex record)
         if ($http_host ~ ^www\.(?<domain>.+)$ ) {
            return 301 https://$domain$request_uri;
         }

         location / {
            # Generic configuration for proxy:
            # Upgrade WebSockets
            proxy_set_header Upgrade $http_upgrade;
            proxy_set_header Connection 'Upgrade';
            # Increase header buffer
            proxy_connect_timeout 10;
            proxy_send_timeout 90;
            proxy_read_timeout 90;
            proxy_buffer_size 128k;
            proxy_buffers 4 256k;
            proxy_busy_buffers_size 256k;
            proxy_temp_file_write_size 256k;

            # show Ultraviolet-App:
            proxy_pass http://Ultraviolet-App;
         }
    }
   ```

3. Test your config

```sh
nginx -t
```

You should see:

```
nginx: the configuration file /etc/nginx/nginx.conf syntax is ok
nginx: configuration file /etc/nginx/nginx.conf test is successful
```

4. Restart NGINX

```sh
service nginx restart
```

5. Enter your domain name into your browser. You should see the same error, except now you access it via port 80.

6. Set Certbot: https://certbot.eff.org/instructions

7. Test your config

```sh
nginx -t
```

You should see:

```
nginx: the configuration file /etc/nginx/nginx.conf syntax is ok
nginx: configuration file /etc/nginx/nginx.conf test is successful
```

8. Restart NGINX

```sh
service nginx restart
```

9. You should be able to enter your domain name into your browser, get redirected to the HTTPS: version, and see no errors.

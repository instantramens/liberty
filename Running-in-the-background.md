# Running in the background

> This will not work for Replit. You need a server that isn't a little Replit box.

## PM2

You can run Ultraviolet-App via PM2 by doing the following:

1. Install PM2 globally

   ```sh
   npm i -g pm2
   ```

2. Start Ultraviolet-App inside PM2 under the name "Ultraviolet-App"

   > Make sure to run this inside the Ultraviolet-App directory

   ```sh
   pm2 start "npm start" --name "Ultraviolet-App"
   ```

This should now start it in the background. You may want to enable PM2 at startup:

```sh
pm2 startup
```

Make sure to run any systemctl commands that `pm2 startup` outputs.

If you want to restore anything in PM2 after a reboot, run `pm2 resurrect`

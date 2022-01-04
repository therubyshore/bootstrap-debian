## Requirements

- Debian 10
- The default Debian admin user is used, and admin is in sudo group.
  Some Debian 10 images, like Digital Oceean's, do not use this user,
  and it must be created to match the upstream Debian 10 configuration.
- A fully-qualified DNS hostname already exists and points to
  the box's IP (otherwise, an SSL cert cannot be requested)

## Usage

```
git clone https://github.com/therubyshore/bootstrap-debian-10.git
cd bootstrap-debian-10
./start some-hostname.somesite.com
```
You can specify multiple hostnames, e.g. "somesite.com www.somesite.com". The first one specified will be considered the primary hostname/fqdn.
Be sure they all currently point to the server when you run the script, or certbot will fail to get its cert from letsencrypt.

Review the start script and comment out anything this server doesn't need (e.g. don't run the script to set up docker if you won't be using it)

You can change the template files yourself and safely re-run the script again each time you make a change, and it will update the configuration.

Then, set up your upstream web application to listen to HTTP traffic on port 3000.
Nginx is configured to act as a reverse proxy, handling requests from the internet
and forwarding them to your web app, and handling HTTPS & SSL/TLS for you.

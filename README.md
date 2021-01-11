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

Then, set up your upstream web application to listen to HTTP traffic on port 3000.
Nginx is configured to act as a reverse proxy, handling requests from the internet
and forwarding them to your web app, and handling HTTPS & SSL/TLS for you.

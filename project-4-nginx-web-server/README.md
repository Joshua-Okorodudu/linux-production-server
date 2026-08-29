# Project 04 – Nginx Web Server

## Objective
Deploy and configure Nginx on Ubuntu Server as a web server.

## Environment
- Ubuntu Server
- Nginx
- systemd
- HTTP Port 80

## Tasks Completed
- Installed Nginx
- Enabled Nginx to start automatically
- Started and verified the Nginx service
- Tested HTTP with curl
- Created a custom web page
- Validated Nginx configuration with nginx -t
- Verified Nginx is listening on port 80

## Verification

```bash
sudo systemctl status nginx
curl http://localhost
sudo nginx -t
sudo ss -tulpn | grep :80

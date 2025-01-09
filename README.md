# Docker

## Usage

Run this command:

docker run -p 8080:80 -it -d ghcr.io/ldapaccountmanager/lam:stable

Then access LAM at http://localhost:8080/

You can change the port 8080 if needed.

Configuration files are stored in:

    /var/lib/ldap-account-manager

See possible environment variables here: https://github.com/LDAPAccountManager/lam/blob/develop/lam-packaging/docker/.env

## Mount Configuration Files from Outside

docker run -p 8080:80 -it -d --volume /data/lam/config:/var/lib/ldap-account-manager/config --env LAM_SKIP_PRECONFIGURE=true ghcr.io/ldapaccountmanager/lam:stable

In case you need to provision from scratch please download the tar.bz2 file first. Then use the content of its config folder for the config volume.

## Proxy with nginx

Example for publishing LAM via e.g. jwilder/nginx-proxy proxy.

docker run --name lam.example.com --hostname lam.example.com --env VIRTUAL_HOST=lam.example.com --env VIRTUAL_PORT=80 --expose 80 ghcr.io/ldapaccountmanager/lam:stable

## LAM Pro

Please request access at support for Azure.

docker login lampro.azurecr.io

docker pull lampro.azurecr.io/lampro

docker run -p 8080:80 -it -d lampro.azurecr.io/lampro:stable

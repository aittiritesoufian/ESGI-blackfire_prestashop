# Prestashop on Docker (with Blackfire support)

## How to

Copy `.env.dist` file to `.env` file.

### Configure Blackfire

In `.env` file, complete these fields:

* `BLACKFIRE_CLIENT_ID`
* `BLACKFIRE_CLIENT_TOKEN`
* `BLACKFIRE_SERVER_ID`
* `BLACKFIRE_SERVER_TOKEN`

by your [Blackfire credentials](https://blackfire.io/my/settings/credentials) (you need to log in).


* Clone this repository.
* Move to web directory and execute "make up" in the terminal.
* Now to start prestashop with Blackfire, Execute:
```
docker-compose up
```
* Access to "http://ps.docker.localhost" and process to prestashop installation

### Blackfire curl

=> Once Prestashop Web installation process is done, trigger a build for "http://ps.docker.localhost/?p=1"

```
make blackfire "curl nginx/?p=1"
```

On Mac

```
docker-compose run blackfire blackfire curl "nginx/?p=1"
```

=> trigger a build for "http://ps.docker.localhost/?p=1"

> In case of double quotes issue, rely on docker-compose binary: ``docker-compose run blackfire blackfire curl '<your-curl-request>'``

### Domains

On Google Chrome, should works else add the virtual host:

Add 
```
127.0.0.1 ps.docker.localhost
```

to your `/etc/hosts` (for linux, mac?) or `C:\Windows\System32\drivers\etc\hosts`

### Database interface

You can access to *Adminer* interface to access to your database by this url:
"http://ps.docker.localhost/adminer.php"

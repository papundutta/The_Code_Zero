# The_Code_Zero

A (cursed) Chrome-extension implant that turns victim Chrome browsers into fully-functional HTTP proxies. By using the proxies this tool creates you can browse the web authenticated as your victim for all of their websites.

# Why make it?

More and more companies are moving toward the "BeyondCorp" model (e.g. no flat internal network, zero trust everything). This is usually implemented via a reverse proxy/OAuth wall gating access to services, eliminating the need for a VPN. As access and tooling move towards being strictly available via the web browser, having a way to easily hijack and use victim's web sessions becomes an ever increasing necessity.

This is also especially useful for locked down orgs that make use of Chrome OS where traditional malware can't be used at all. It's also steathy, as all requests will have the appropriate source-IP, cookies, client-certificates, etc since it's being proxying directly through the victim's browser.

# Requirements

* [`docker`](https://docs.docker.com/get-docker/) and [`docker-compose`](https://docs.docker.com/compose/install/)

* Chrome web browser


# Setting Up the Backend

The backend is entirely dockerized and can be setup by running the following commands:

```

cd The_Code_Zero/

# Start up redis and Postgres containers in the background

docker-compose up -d redis db

# Start The_Code_Zero backend

docker-compose up The_Code_Zero

```

Once you start up the backend you'll see an admin username and password printed to the console. You can log into the admin panel at `http://localhost:8118` using these credentials (you will be prompted to change your password upon logging in since the one printed to the console is likely logged). 

## Installing the The_Code_Zero CA for Proxying HTTPS

Once you have the backend setup, log in to the admin panel at `http://localhost:8118` (see above) and click the `Download HTTPS Proxy CA Certificate` button. This will download the generated CA file which is required in order to proxy HTTPS requests.






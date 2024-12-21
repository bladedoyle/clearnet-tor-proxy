# Clearnet to Tor Hidden Service Proxy

This project creates 3 containers:
1. nginx: Listens on http://localhost:8888 for ingress connections
2. socat: Translates from nginx http to socks4 tor daemon
3. tor: tor daemon

All 3 conatiners are created on a bridge and port 8888 is exposed on 127.0.0.1

This simple proxy works on a single page, or on a self-contained site with only relative links.
One example of a website like that is the "MIM Exchange" - a Cryptocurrency Instant Exchange Hidden Service Example: https://github.com/bladedoyle/mim-exchange


## Use

* Install docker and docker-compose: 
https://docs.docker.com/engine/install/
https://docs.docker.com/compose/install/

* Clone this project and change directories

* Notice that the default configuration is to proxy "The Hidden Wiki".  This is set in the docker compose .env file:
`cat .env`

* Build the project
`docker compose build`

* Run the project
`docker compose run`

* Verify:
Open https://localhost:8888 in your clearnet web browser.
You shold see that your localhost service is a proxy for "The Hidden Wiki" on tor
(note that the links in the wiki will not work through the proxy - see comments above)

* Clean up docker resources
`docker compose down`

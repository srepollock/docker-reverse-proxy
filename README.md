# Docker Reverse Proxy

A Docker reverse proxy setup. This is a simple template to build out into larger examples.

[![Open Source Love](https://badges.frapsoft.com/os/v2/open-source.svg?v=103)](https://github.com/ellerbrock/open-source-badges/)

## Setup

### Prerequisits

- docker
- git
- curl

### Steps

1. Clone the repo
2. Run `docker-compose up -d`
3. Check that it's working with either: `curl docker

The meat of the project is in [`docker-compose.yml`](docker-compose.yml). This creates the nginx-proxy from jwilder's image, that will automatically build the service and the nginx config to use based on the rest of the containers. The next two services are the web applications. The first is an nginx instance, the second is an apache instance. This is just to display that the project is working. If you're running on a local machine, check it out by going to the respective domains (`VIRTUAL_HOST`'s in the docker-compose).

If you're having issues connecting, check out the [Notes](#Notes) for some troubleshooting and other notes on the project.

## Notes

- To get this working on remote machines (as I was running an AWS EC2 instance for Docker testing) you have to be sure to set in the hosts file the web addresses. `/etc/hosts`
	```
	172.0.0.1 a-site.domain.com
	172.0.0.1 b-site.domain.com
	```
	> Change `172.0.0.1` to your host (ex: EC2 machine) machines local IP address.
	This routes the site to localhost with the correct domain in the url to be updated by the local Nginx DNS.

## Built with

- [jwilder reverse proxy][jwilder reverse proxy]
- [docker](https://docker.com)

## Authors

- [Spencer Pollock](@srepollock)

## License

This project is licensed under the MIT License - see [LICENSE](LICENSE) file for details

## Resources
[jwilder reverse proxy]: https://github.com/jwilder/nginx-proxy
[jwilder automate nginx proxy]: http://jasonwilder.com/blog/2014/03/25/automated-nginx-reverse-proxy-for-docker/
[dockerfile best practices]: https://docs.docker.com/develop/develop-images/dockerfile_best-practices/
[docker compose files]: https://docs.docker.com/compose/
[docker container networking]: https://docs.docker.com/config/containers/container-networking/

> Created by [Spencer Pollock](@srepollock)
> [Contact me](https://spollock.ca)

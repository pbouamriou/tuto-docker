CUR_DIR = $(CURDIR)

.PHONY: help

help: ## This help.
	@awk 'BEGIN {FS = ":.*?## "} /^[a-zA-Z_-]+:.*?## / {printf "\033[36m%-30s\033[0m %s\n", $$1, $$2}' $(MAKEFILE_LIST)

all: build-perso ## Build images (lighttpd and perso)

clean: ## clean
	@docker rmi lighttpd lighttpd-perso 2>/dev/null || true

build-lighttpd: Dockerfile.lighttpd lighttpd.conf index.html ## build docker image
	docker build -t lighttpd -f Dockerfile.lighttpd .

build-perso: build-lighttpd Dockerfile.perso www/index.html ## build docker image
	docker build -t lighttpd-perso -f Dockerfile.perso .

run: build-perso ## run docker (lighttpd-perso)
	docker run -t -i -p 8080:80 --rm --name lighttpd-perso-container lighttpd-perso

run-volume: build-perso ## run docker (lighttpd-perso)
	docker run -t -i -p 8080:80 --rm -v "$(CUR_DIR)/www-v2":/var/lighttpd/www --name lighttpd-perso-container lighttpd-perso

run-lighttpd: build-lighttpd ## run docker (lighttpd)
	docker run -t -i -p 8080:80 --rm --name lighttpd-container lighttpd

rund: build-perso ## run docker as deamon (lighttpd-perso)
	docker run -d -p 8080:80 --rm --name lighttpd-perso-container lighttpd-perso

status:
	docker inspect lighttpd-perso-container --format "{{.State.Health.Status}}"

shell:
	docker exec -ti lighttpd-perso-container /bin/bash

.PHONY: help

help: ## This help.
	@awk 'BEGIN {FS = ":.*?## "} /^[a-zA-Z_-]+:.*?## / {printf "\033[36m%-30s\033[0m %s\n", $$1, $$2}' $(MAKEFILE_LIST)

all: build-nginx ## Build images

clean: ## clean
	@docker rmi hello 2>/dev/null || true

build-nginx: Dockerfile lighttpd.conf index.html ## build docker image
	docker build -t nginx .

run: all ## run docker
	docker run -t -i -p 8080:80 --rm --name nginx-container nginx

rund: all ## run docker as deamon
	docker run -d -p 8080:80 --rm --name nginx-container nginx

status:
	docker inspect nginx-container --format "{{.State.Health.Status}}"

shell:
	docker exec -ti nginx-container /bin/bash

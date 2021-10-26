.PHONY: help

help: ## This help.
	@awk 'BEGIN {FS = ":.*?## "} /^[a-zA-Z_-]+:.*?## / {printf "\033[36m%-30s\033[0m %s\n", $$1, $$2}' $(MAKEFILE_LIST)

all: build ## Build images

clean: ## clean
	@docker rmi hello 2>/dev/null || true

build: Dockerfile lighttpd.conf index.html ## build docker image
	docker build -t nginx .

build-nc: hello Dockerfile ## build docker image (no cache)
	docker build -t hello --no-cache .

run: all ## run docker
	docker run -t -i -p 8080:80 --rm nginx

shell:
	docker exec -ti nginx /bin/bash

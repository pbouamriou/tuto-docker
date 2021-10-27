.PHONY: help

help: ## This help.
	@awk 'BEGIN {FS = ":.*?## "} /^[a-zA-Z_-]+:.*?## / {printf "\033[36m%-30s\033[0m %s\n", $$1, $$2}' $(MAKEFILE_LIST)

all: build ## Build images

clean: ## clean
	@docker rmi top 2>/dev/null || true

build: Dockerfile ## build docker image
	docker build -t top .

build-nc: Dockerfile ## build docker image (no cache)
	docker build -t top --no-cache .

run: all ## run docker
	docker run -t -i --name top --rm top

run-n: all ## run docker
	docker run -t -i --rm --name top top -c -n 5

shell:
	docker exec -ti top /bin/bash

inspect: build
	docker inspect --format='' top

labels: build
	docker inspect --format='{{json .Config.Labels}}' top

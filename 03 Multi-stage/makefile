.PHONY: help

help: ## This help.
	@awk 'BEGIN {FS = ":.*?## "} /^[a-zA-Z_-]+:.*?## / {printf "\033[36m%-30s\033[0m %s\n", $$1, $$2}' $(MAKEFILE_LIST)

all: build ## Build images

clean: ## clean
	@docker rmi hello 2>/dev/null || true

build: hello.c Dockerfile ## build docker image
	docker build -t hello .

build-nc: hello.c Dockerfile ## build docker image (no cache)
	docker build -t hello --no-cache .

run: all ## run docker
	docker run -t -i --rm hello

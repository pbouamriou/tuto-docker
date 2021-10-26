.PHONY: help

help: ## This help.
	@awk 'BEGIN {FS = ":.*?## "} /^[a-zA-Z_-]+:.*?## / {printf "\033[36m%-30s\033[0m %s\n", $$1, $$2}' $(MAKEFILE_LIST)

all: build ## Build images

clean: ## clean
	@rm -f hello
	@docker rmi hello 2>/dev/null || true

build: hello Dockerfile ## build docker image
	docker build -t hello .

build-nc: hello Dockerfile ## build docker image (no cache)
	docker build -t hello --no-cache .

hello: hello.c
	@gcc -o hello hello.c -static

run: all ## run docker
	docker run -t -i --rm hello

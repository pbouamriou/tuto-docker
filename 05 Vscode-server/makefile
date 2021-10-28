.PHONY: help

help: ## This help.
	@awk 'BEGIN {FS = ":.*?## "} /^[a-zA-Z_-]+:.*?## / {printf "\033[36m%-30s\033[0m %s\n", $$1, $$2}' $(MAKEFILE_LIST)

all: build ## Build images

clean: ## clean
	@sudo rm -rf config-vscode
	@docker rmi 05vscode-server_vscode-server 2>/dev/null || true

build:  ## build image
	@[ -d config-vscode ] || mkdir -p config-vscode
	docker-compose build

run: ## run services
	docker-compose up -d

stop: ## stop services
	docker-compose down

shell: ## start a shell in code-server service
	docker-compose exec vscode-server /bin/zsh

volume-ls: ## list all volumes
	docker volume ls | grep 05vscode-server


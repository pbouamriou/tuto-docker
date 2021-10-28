.PHONY: help

help: ## This help.
	@awk 'BEGIN {FS = ":.*?## "} /^[a-zA-Z_-]+:.*?## / {printf "\033[36m%-30s\033[0m %s\n", $$1, $$2}' $(MAKEFILE_LIST)

all: build ## Build images

clean: ## clean
	@docker rmi 05vscode-server_vscode-server 2>/dev/null || true

build:  ## build image
	docker-compose build

run: run-5 ## run services

run-0: ## stop services
	docker-compose up --scale top=0 -d

run-1: ## run 1 top service
	docker-compose up --scale top=1 -d

run-2: ## run 2 top services
	docker-compose up --scale top=2 -d

run-3: ## run 3 top services
	docker-compose up --scale top=3 -d

run-4: ## run 4 top services
	docker-compose up --scale top=4 -d

run-5: ## run 5 top services
	docker-compose up --scale top=5 -d

stop: ## stop services
	docker-compose down

shell: ## start a shell in top service
	docker-compose exec top /bin/bash



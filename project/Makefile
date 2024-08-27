BROKER_BINARY=brokerApp
AUTH_BINARY=authApp
LOGGER_BINARY=loggerServiceApp
MAIL_BINARY=mailerApp
LISTENER_BINARY=listenerApp

## up: starts all containers in the background without forcing build
up:
	@echo "Starting Docker Images..."
	docker-compose up -d
	@echo "Docker images started!"

## up_build: stops docker-compose (if running), builds all projects and starts docker-compose
up_build: build_broker build_auth build_logger build_mail build_listener
	@echo "Stopping docker containers (if running...)"
	docker-compose down
	@echo "Building (when required) and starting docker images..."
	docker-compose up --build -d
	@echo "Docker images build and started!"

## down: stop docker compose
down:
	@echo "Stopping docker-compose ..."
	docker-compose down
	@echo "Done!"

## build_broker: builds the broker binary as linux executable
build_broker:
	@echo "Building broker binary..."
	cd ../broker && env GOOS=linux CGO_ENABLES=0 go build -o ${BROKER_BINARY} ./cmd/api
	@echo "Done!"

## build_auth: builds the auth binary as linux executable
build_auth:
	@echo "Building auth binary..."
	cd ../authentication-service && env GOOS=linux CGO_ENABLES=0 go build -o ${AUTH_BINARY} ./cmd/api
	@echo "Done!"

## build_logger: builds the logger binary as linux executable
build_logger:
	@echo "Building logger binary..."
	cd ../logger-service && env GOOS=linux CGO_ENABLES=0 go build -o ${LOGGER_BINARY} ./cmd/api
	@echo "Done!"

## build_mail: builds the mail binary as linux executable
build_mail:
	@echo "Building mail binary..."
	cd ../mail-service && env GOOS=linux CGO_ENABLES=0 go build -o ${MAIL_BINARY} ./cmd/api
	@echo "Done!"

## build_listener: builds the listener binary as linux executable
build_listener:
	@echo "Building listener binary..."
	cd ../listener-service && env GOOS=linux CGO_ENABLES=0 go build -o ${LISTENER_BINARY} .
	@echo "Done!"
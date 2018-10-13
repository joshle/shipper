build:
	CGO_ENABLED=0 GOOS=linux go build -a -installsuffix cgo .
	docker build -t consignment-cli .
	rm -f consignment-cli

run:
	docker run -e MICRO_REGISTRY=mdns consignment-cli

dev:
	MICRO_REGISTRY=mdns go run cli.go
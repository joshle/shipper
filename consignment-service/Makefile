build:
	protoc -I. --proto_path=${GOPATH}/src:. --micro_out=. --go_out=. proto/consignment/consignment.proto
	http_proxy=localhost:8123 dep ensure
	# GOOS=linux GOARCH=amd64 go build
	docker build -t consignment-service .
	rm -rf vendor

run:
	docker run -p 50051:50051 \
		-e MICRO_SERVER_ADDRESS=:50051 \
		-e MICRO_REGISTRY=mdns \
		consignment-service
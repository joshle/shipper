build:
	protoc -I. --proto_path=${GOPATH}/src:. --micro_out=. --go_out=. proto/user/user.proto
	# http_proxy=localhost:8123 dep ensure
	# docker build -t user-service .
	# rm -rf vendor

run:
	docker run -p 50051:50051 \
		-e MICRO_SERVER_ADDRESS=:50051 \
		-e MICRO_REGISTRY=mdns \
		user-service

dev:
	MICRO_SERVER_ADDRESS=:50053 \
	MICRO_REGISTRY=mdns  \
	DB_NAME="shippy"  \
	DB_HOST="localhost"  \
	DB_PORT="3306"  \
	DB_USER="root"  \
	DB_PASSWORD=""  \
	MICRO_BROKER=nats \
	MICRO_BROKER_ADDRESS=0.0.0.0:4222 \
	go run main.go datastore.go handler.go repository.go token_service.go
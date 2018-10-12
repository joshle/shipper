build:
	# protoc -I. --go_out=plugins=micro:$(GOPATH)/src/github.com/joshle/shippy/vessel-service proto/vessel/vessel.proto
	protoc -I. --proto_path=${GOPATH}/src:. --micro_out=. --go_out=. proto/vessel/vessel.proto
	http_proxy=localhost:8123 dep ensure
	docker build -t vessel-service .
	# rm -rf vendor

run:
	docker run -p 50052:50051 -e MICRO_SERVER_ADDRESS=:50051 -e MICRO_REGISTRY=mdns vessel-service

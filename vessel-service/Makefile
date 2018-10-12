build:
	protoc -I. --go_out=plugins=micro:$(GOPATH)/src/github.com/joshle/shippy/vessel-service \
    	proto/vessel/vessel.proto
	godep save
	docker build -t vessel-service .
	rm -rf Godeps vendor

run:
	docker run -p 50052:50051 -e MICRO_SERVER_ADDRESS=:50051 -e MICRO_REGISTRY=mdns vessel-service

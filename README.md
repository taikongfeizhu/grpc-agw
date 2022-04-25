<div align="center">
<img src="assets/helloworld-grpc-gateway.svg" height="auto" width="400" />
<br />
<h1>Hello World gRPC-Gateway</h1>
<p>
Simple hello world program which uses gRPC-Gateway
</p>
<a href="https://github.com/iamrajiv/helloworld-grpc-gateway/network/members"><img src="https://img.shields.io/github/forks/iamrajiv/helloworld-grpc-gateway?color=0969da&style=for-the-badge" height="auto" width="auto" /></a>
<a href="https://github.com/iamrajiv/helloworld-grpc-gateway/stargazers"><img src="https://img.shields.io/github/stars/iamrajiv/helloworld-grpc-gateway?color=0969da&style=for-the-badge" height="auto" width="auto" /></a>
<a href="https://github.com/iamrajiv/helloworld-grpc-gateway/blob/main/LICENSE"><img src="https://img.shields.io/github/license/iamrajiv/helloworld-grpc-gateway?color=0969da&style=for-the-badge" height="auto" width="auto" /></a>
</div>

## About

It is a simple hello world program that uses gRPC-Gateway. This project was created when I participated in [Google Season of Docs 2020](https://github.com/iamrajiv/GSoD-2020) with [gRPC-Gateway](https://github.com/grpc-ecosystem/grpc-gateway). The reason for making this project is to make people familiarize themselves with gRPC-Gateway.

I have added all the tutorials related to Hello World gRPC-Gateway to the [gRPC-Gateway documentation website](https://grpc-ecosystem.github.io/grpc-gateway/docs/tutorials/).

To get more references about gRPC-Gateway check out [Basic Arithmetic gRPC Server](https://github.com/iamrajiv/basic-arithmetic-grpc-server).

It is a Basic Arithmetic gRPC server that uses gRPC-Gateway and reads protobuf service definitions and generates a reverse-proxy server. It performs four basic operations Addition, Division, Multiplication, and Subtraction between two given integers.

#### Folder structure:

```shell
.
├── LICENSE
├── Makefile
├── README.md
├── assets
│   └── grpc-gateway-release.svg
├── buf.gen.yaml
├── buf.yaml
├── go.mod
├── go.sum
├── main.go
└── proto
    ├── google
    │   └── api
    │       ├── annotations.proto
    │       └── http.proto
    └── helloworld
        ├── hello_world.pb.go
        ├── hello_world.pb.gw.go
        ├── hello_world.proto
        ├── hello_world.swagger.json
        └── hello_world_grpc.pb.go
```

## Usage

Before running this project install all the required Go packages by running the command `make install`. Also, we can generate the stubs using the command `make generate` and delete the stubs using the command `make clean`.

Start the server using the command:

```shell
go run main.go
go run client/client.go
```

Then use cURL to send HTTP requests:

```shell
curl -X POST -k http://localhost:8090/api/v1/sayHello -d '{"name": "hello"}'
```

```shell
{"message":"hello world"}
```

## Swagger UI

Link: [https://app.swaggerhub.com/apis/iamrajiv/Hello_World_gRPC-Gateway/2](https://app.swaggerhub.com/apis/iamrajiv/Hello_World_gRPC-Gateway/2)

https://github.com/grpc-ecosystem/grpc-gateway/blob/master/README.md
https://grpc-ecosystem.github.io/grpc-gateway/docs/tutorials/introduction/

## License

```shel
protoc -I ./proto \
  --go_out ./proto --go_opt paths=source_relative \
  --go-grpc_out ./proto --go-grpc_opt paths=source_relative \
  --grpc-gateway_out ./proto --grpc-gateway_opt paths=source_relative \
  ./proto/helloworld/hello_world.proto
```

[MIT](https://github.com/iamrajiv/helloworld-grpc-gateway/blob/main/LICENSE)

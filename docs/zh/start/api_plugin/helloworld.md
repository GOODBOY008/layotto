# API plugin: register your own API
This is a demo to show you how to register your own API.

Layotto has the api-plugin feature to let you add your own API based on your need.


## step 1. start Layotto with a helloworld API-Plugin
Build and run Layotto :

```shell
# change directory 
cd ${projectpath}/cmd/layotto_multiple_api
# build it
go build -o layotto
# run it
./layotto start -c ../../configs/config_in_memory.json
```

Q: What happened?

Check the code in [`main.go`](https://github.com/mosn/layotto/blob/d74ff0e8940e0eb9c73b1d3275a17d29be36bd5c/cmd/layotto_multiple_api/main.go#L203) and you will find a new API was registered during startup:

```go
		// register your grpc API here
        runtime.WithGrpcAPI(
            // default grpc API
            default_api.NewGrpcAPI,
            // a demo to show how to register your own API
            helloworld_api.NewHelloWorldAPI,
        ),
```

## step 2. invoke the helloworld API
```shell
# change directory 
cd ${projectpath}/cmd/layotto_multiple_api
# run demo client
go run client/main.go
```

The result will be:

```shell
Greeting: Hello world
```

This message is the response of the helloworld API you just registered in step 1.

## Next
You can refer to the demo code to implement your own API.
Have a try !

For more details,you can refer to the [design doc](zh/design/api_plugin/design.md)
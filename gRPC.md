gRPC - 
* google Remote procedure call
* call from one server to another
* helps in load balancing
* you can do authentication
* its open source
![gRPC](https://innersource.flutter.com/assets/blog/grpc/rpc.png)

* In this communication happens with Protocol Buffer (ProtoBuf) - IDL (Interface Definition Language)
* The entire communication happens in ProtoBuf not JSON
Wherever also in REST JSON is not sent directly stringified of serialised version data is sent
* Similarly, serialisation is  used
* Single long live connection
* Bidirectional Streaming - In single network bidirectional packet transfer is done
https://cdn.thenewstack.io/media/2021/08/9ce32b9e-image2.png

### Protocol Buffer
![](https://developer.token.io/token_tpp_sdk_doc/content/resources/images/grpc-proto_concept.png)
* provides serialisation and deserialisation provided by this mechanism itself
* the data is binary format data due to this transfer happens fast
*  .proto (proto) -in which you write your proto buf
Benefits
1. less CPU resources
2. mobiles
3. faster
*              protoBuf
* Client gRPC < = > Server gRPC
*      |       gRPC
* REST | 
* Browser

gRPC -
* Performance (10x faster) compared to REST
* Streaming mechanism is used
* Code Generation
* Language Agnostic
* Security Discovery
* Security

Disadvantages->
* Non-human readable format
* Limited browser support
* No edge caching-because of post method
* Steeper learning curve



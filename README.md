# C#におけるprotol buffer自動生成用コンテナ
grpc/idlディレクトリ以下に，GRPCのIDFを設置し，コンテナで自動生成するツールを書いてみました．
![demo](https://github.com/tozastation/Protocol-Builder-Csharp/blob/master/demo/Protocol-Builder.gif)
## 手順
### コンテナの実行
- CONTAINER_ID=｀docker run -v $PWD/grpc:/tmp/grpc -itd protocol-builder｀
### プロトコルファイルを元にコンパイル
- docker exec -i $CONTAINER_ID bash -c 'protoc -I $PROTO_PATH --csharp_out=$CSHARP_OUT_PATH --grpc_out=$GRPC_OUT_PATH --plugin=protoc-gen-grpc=$GRPC_PLUGIN_PATH $PROTO_PATH*.proto'
### ローカルにコピー
- docker cp $CONTAINER_ID:/tmp/grpc_model .
- docker cp $CONTAINER_ID:/tmp/grpc_logic .

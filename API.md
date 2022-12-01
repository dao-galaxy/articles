


#### 1) 获取某个 owner 拥有的 DID 列表

```shell
curl https://goerli.diddao.io/api/didNode/getDidNodeListByAddress/0xf07149221a4c85c26fecc560c5970ec1415f6735

{
    "status":200,
    "message":"SUCCESS",
    "data":[
        {
            "owner":"0xf07149221a4c85c26fecc560c5970ec1415f6735",
            "node":"0x8fdbedec4e9ea7c8743ba6af3b8242bf7b3fbb47b8cb9dc27b0433eea62925e7",
            "id":12,
            "parentNode":"0x8a74fc6994ef0554dd9cc95c3391f9cd66152031a0c1feacb835e3890805af5f",
            "expire":-1,
            "ttl":0,
            "transfer":1669180128,
            "name":"danoky",
            "defaultDidNode":true
        },
        {
            "owner":"0xf07149221a4c85c26fecc560c5970ec1415f6735",
            "node":"0xef71356707b86d41459d55baf7385bfbbb5b5e5322f8e8f9148665ae4a13e740",
            "id":14,
            "parentNode":"0x8a74fc6994ef0554dd9cc95c3391f9cd66152031a0c1feacb835e3890805af5f",
            "expire":-1,
            "ttl":0,
            "transfer":1669193904,
            "name":"danok21",
            "defaultDidNode":false
        },
        {
            "owner":"0xf07149221a4c85c26fecc560c5970ec1415f6735",
            "node":"0x6650ec5c32f3d1d68d1c05ecc732118de4e82f027fcd7d6672df13c12de656da",
            "id":16,
            "parentNode":"0xb5f2bbf81da581299d4ff7af60560c0ac854196f5227328d2d0c2bb0df33e553",
            "expire":-1,
            "ttl":0,
            "transfer":1669287840,
            "name":"danoky",
            "defaultDidNode":false
        },
        {
            "owner":"0xf07149221a4c85c26fecc560c5970ec1415f6735",
            "node":"0x8b21efeb25303dcc086f181c72e9988c28d9feec7aefa2d1e8b99f68db6b2987",
            "id":39,
            "parentNode":"0x8a74fc6994ef0554dd9cc95c3391f9cd66152031a0c1feacb835e3890805af5f",
            "expire":-1,
            "ttl":0,
            "transfer":1669621740,
            "name":"aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
            "defaultDidNode":false
        }
    ]
}
 
```

#### 2) 获取某个 DID 当前可领取的分红额度

```shell
curl http://8.136.211.11/didNode/getLatestDivident --request POST --header "Content-Type: application/json" --data '{
    "signature":"0x4a3e1c9108720e8c7c6c5d824ffe5b7c544a6e017300511c597aab2f113610e37494e5908e364bde235dc28f902d1ce86c767cb13291aa13adcb930b5296a5f11c", 
    "node":"0x4e772f62035453f381d9e8495f65ea4d5c90168c61878c755d8b2c9170e259d2"
}'
```

#### 3) 某个 DID 登陆并打卡

```shell
curl http://8.136.211.11/didNode/userCheckIn --request POST --header "Content-Type: application/json" --data '{
"signature":"0x4a3e1c9108720e8c7c6c5d824ffe5b7c544a6e017300511c597aab2f113610e37494e5908e364bde235dc28f902d1ce86c767cb13291aa13adcb930b5296a5f11c", 
"node":"0x4e772f62035453f381d9e8495f65ea4d5c90168c61878c755d8b2c9170e259d2"
}'
```

#### 4) 获取某个 DID 历史打卡信息

```shell
curl 'http://8.136.211.11:10020/getDividentInfo?node=0x033549da90d902eebcededec7286e6a5f4e7b23484d4b06c20bd6ed60e05d4ef&timestamp=2022-11-19'
```

timestamp 为 2022-11-19 的格式，返回JSON 

```shell
{
 "timestamp" : 1668826514, //node 在 2022-11-19 那一天第一次打卡成功时的，系统记录下的时间戳；
 "gasBalance" : "10000000000000000", // node 在 2022-11-19 那一天第一次打卡成功时的，系统记录下的Gas权重值
 "dividentAmount" : "6666666666666", // node 在 2022-11-19 那一天分到的钱数量；
 "platformIncome" : "2000000000000000" // 2022-11-19 那一天的平台收入
 "totalCheckin" : 6 // 2022-11-19 那一天打卡的人数（DidNode数）
}
```

#### 4) 获取某个 DID 的 JSON Metadata

```shell
curl https://goerli.diddao.io/api/metadata/goerli/did/89918177947327675033248180240231135487841825057814170914789717826776595528464

{
  "name" : "buffalo.did",
  "symbol" : "GalaxyDID",
  "description" : "It is a did nft",
  "image" : "https://www.larvalabs.com/public/images/cryptopunks/punk7804.png",
  "externalUrl" : "https://diddao.io",
  "properties" : null,
  "attributes" : null,
  "collection" : null
}
```



#### a) eth_call

```shell
curl https://eth-goerli.g.alchemy.com/v2/-s1zkDpkEmnjF4wIk8pLsiJBuxWelYV0 --request POST --header "Content-Type: application/json" --data '{
    "jsonrpc":"2.0",
    "method":"eth_call",
    "params":[
        {
            "to":"0x966a31ff3eb02144369887d4bd3a9238a7ff925c",
            "data":"0xd56aae550000000000000000000000000000000000000000000000000000000000000008"
        }
    ],
    "id":1
}'
```





#### 1) 获取某个 owner 拥有的 DID 列表

```shell
curl https://goerli.diddao.io/api/didNode/getDidNodeListByAddress/0xf07149221a4c85c26fecc560c5970ec1415f6735

返回值

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
        ...
        ...
	...
    ]
}
 
```

#### 2) 获取某个 DID 当前可领取的分红额度

```shell
curl https://goerli.diddao.io/api/didNode/getLatestDivident --request POST --header "Content-Type: application/json" --data \
'
{
    "node":"0xc6cbe29b02227ba1bb49c0da438c639867e06abe8377a4e69e75a8b705b17b10",
    "signature":"0xad9cf1328fb80a97117cec172e65288161ac9d9f966e5092cc5c42022fbf65f461d80f92b75278c14bdc85b8d2e3d9afa11d3f99c4930d02fff4bd3d1c84f01c1b"
}
'

返回值

{
    "status":200,
    "message":"SUCCESS",
    "data":{
        "owner":"0x429ebd9365061dabb853de89c134f9b79468a952",
        "node":"0xc6cbe29b02227ba1bb49c0da438c639867e06abe8377a4e69e75a8b705b17b10",
        "time":19328,
        "signature":"0x8ee94d8e7874708abbfcf0f588290399a6928b6f7ce9f548ae3296c52d1269121065970830f0e1559782242273d10e1c73047f99ad51af1bb62c19913ed3c6db1b",
        "gasBalance":"100000000000000000000",
        "dividend":"0"
    }
}
```

#### 3) 某个 DID 登陆并打卡

```shell
curl https://goerli.diddao.io/api/didNode/userCheckin --request POST --header "Content-Type: application/json" --data \
'
{
    "signature":"0x5efa28045b3ee5a5c977a1357d647f53f62ef7a4d0995ddb7f7807942fc4cdf927ba9b41d327afa90b8af519084be6e23525968f6348fe034f78e8e87346ebe21b", 
    "node":"0xc6cbe29b02227ba1bb49c0da438c639867e06abe8377a4e69e75a8b705b17b10"
}
'

返回值

{"status":10000004,"message":"已签到,请勿重复签到","data":null}
```

#### 4) 获取某个 DID 历史打卡信息

```shell
// curl 'https://goerli.diddao.io/api/getDividentInfo?node=0x033549da90d902eebcededec7286e6a5f4e7b23484d4b06c20bd6ed60e05d4ef&timestamp=2022-11-19'

curl https://goerli.diddao.io/api/api/getDividentInfo --request POST --header "Content-Type: application/json" --data \
'
{
    "node":"0xc6cbe29b02227ba1bb49c0da438c639867e06abe8377a4e69e75a8b705b17b10",
    "timeStamp":"2022-11-19"
}
'

返回值

{"status":10000007,"message":"当日无打卡记录","data":null}

{
 "timestamp" : 1668826514, //node 在 2022-11-19 那一天第一次打卡成功时的，系统记录下的时间戳；
 "gasBalance" : "10000000000000000", // node 在 2022-11-19 那一天第一次打卡成功时的，系统记录下的Gas权重值
 "dividentAmount" : "6666666666666", // node 在 2022-11-19 那一天分到的钱数量；
 "platformIncome" : "2000000000000000" // 2022-11-19 那一天的平台收入
 "totalCheckin" : 6 // 2022-11-19 那一天打卡的人数（DidNode数）
}
```

#### 5) 获取某个 DID 的 JSON Metadata

```shell
curl https://goerli.diddao.io/api/metadata/goerli/did/89918177947327675033248180240231135487841825057814170914789717826776595528464

返回值

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

#### 6) 挂单售卖 DID-NFT

```shell
curl https://goerli.diddao.io/api/order/createOrder --request POST --header "Content-Type: application/json" --data \
'
{
    "orderType":"fixedPrice",
    "maker":"0x12345",
    "taker":"0x00000",
    "startTime":"1670394431",
    "endTime":"1670394431",
    "makerNonce":"63",
    "tokenId":"0xc6cbe29b02227ba1bb49c0da438c639867e06abe8377a4e69e75a8b705b17b10",
    "ethPrice":"1000000000000000000", // 1 ETH
    "sell":true / false,
    "signature":"0x5efa28045b3ee5a5c977a1357d647f53f62ef7a4d0995ddb7f7807942fc4cdf927ba9b41d327afa90b8af519084be6e23525968f6348fe034f78e8e87346ebe21b"
}
'

返回值

{"status":200,"message":"","data":true}

{"status":10000007,"message":"签名验证失败","data":null}

```


#### 7) 获取指定 DID-NFT 的订单信息 

```shell
curl https://goerli.diddao.io/api/order/getOrderInfo?tokenId=0xc6cbe29b02227ba1bb49c0da438c639867e06abe8377a4e69e75a8b705b17b10 --request GET 

返回值

{
  "status": 200,
  "message": "SUCCESS",
  "data": {
      {
        "id": 1,
        "maker": "0xb6B78b6F7C461d9D33d5D8c9f9366215C416AeB7",
        "taker": "0xb6B78b6F7C461d9D33d5D8c9f9366215C416AeB7",
	 "name": "js",
        "startTime": 1670371622,
        "endTime": 1670371623,
        "makerNonce": "123",
        "tokenId": "0xc6cbe29b02227ba1bb49c0da438c639867e06abe8377a4e69e75a8b705b17b10",
        "ethPrice": "1000000000000000000",
        "sell": 1,
        "signature": "我是签名",
        "orderStatus": 1,
        "didType": "did",
        "imageUrl": "https://goerli.diddao.io/img/logo_galaxy_white.1fd71fd1.png" // 后续统一处理一下，现在不做处理。
      }
  }
}

{
  "status": 200,
  "message": "SUCCESS",
  "data": null
}

```


#### 8)获取did订单列表

```shell
curl https://goerli.diddao.io/api/order/orderList --request POST --header "Content-Type: application/json" --data \
'
{
    "orderType":"fixedPrice",
    "sortField":"start_time" // 排序字段 时间： start_time, 价格：eth_price,
    "sortRule":"asc" // 排序规则,asc -> 正序，desc -> 倒叙,
    "pageSize":20, // 每一页 60 个
    "pageNum":3, // 第 3 页（第一页从1开始）
    "didType":"did" // did类型：did、dao,
    "searchName":"alibaba" // 搜索包含hello的did挂单
}
'

返回值

{
  "status": 200,
  "message": "SUCCESS",
  "data": {
    "records": [
      {
        "id": 1,
        "maker": "0xb6B78b6F7C461d9D33d5D8c9f9366215C416AeB7",
        "taker": "0xb6B78b6F7C461d9D33d5D8c9f9366215C416AeB7",
	 "name": "js",
        "startTime": 1670371622,
        "endTime": 1670371623,
        "makerNonce": "123",
        "tokenId": "0xc6cbe29b02227ba1bb49c0da438c639867e06abe8377a4e69e75a8b705b17b10",
        "ethPrice": "1000000000000000000",
        "sell": 1,
        "signature": "我是签名",
        "orderStatus": 1,
        "didType": "did",
        "imageUrl": "https://goerli.diddao.io/img/logo_galaxy_white.1fd71fd1.png"
      },
      ...
      ...
      ...
    ],
    "total": 4,
    "size": 20,
    "current": 1, // 后端代码库生成的，无法重命名为pageNum
    "orders": [   // 前端不要理会这个字段，后端代码库生成的
      
    ],
    "optimizeCountSql": true, // 前端不要理会这个字段，后端代码库生成的
    "searchCount": true, // 前端不要理会这个字段，后端代码库生成的
    "countId": null, // 前端不要理会这个字段，后端代码库生成的
    "maxLimit": null, // 前端不要理会这个字段，后端代码库生成的
    "pages": 1 // 前端不要理会这个字段，后端代码库生成的
  }
}
```


#### a) eth_call

```shell
curl https://eth-goerli.g.alchemy.com/v2/-s1zkDpkEmnjF4wIk8pLsiJBuxWelYV0 --request POST --header "Content-Type: application/json" --data \
'
{
    "jsonrpc":"2.0",
    "method":"eth_call",
    "params":[
        {
            "to":"0x966a31ff3eb02144369887d4bd3a9238a7ff925c",
            "data":"0xd56aae550000000000000000000000000000000000000000000000000000000000000008"
        }
    ],
    "id":1
}
'
```


```shell
curl https://eth-goerli.g.alchemy.com/v2/-s1zkDpkEmnjF4wIk8pLsiJBuxWelYV0 --request POST --header "Content-Type: application/json" --data 
'
{
    "jsonrpc":"2.0",
    "method":"eth_getLogs",
    "params":[
        {
            "fromBlock":"0x7C8760",
            "toBlock":"0x7C8770",
            "address":[
                "0xBbeaF5f51fDfAaEc9Af54135Ec6FcaB3c9ec8d6e",
                "0x2319b4a9d8097F58e517830E3329b7040B635415"
            ]
        }
    ],
    "id":74
}
'
```

https://goerli.etherscan.io/address/0xbbeaf5f51fdfaaec9af54135ec6fcab3c9ec8d6e#events


```JSON
{
    "jsonrpc":"2.0",
    "id":74,
    "result":[
        {
            "address":"0xbbeaf5f51fdfaaec9af54135ec6fcab3c9ec8d6e",
            "blockHash":"0x5c19e0ae6429b5fcffbcafe19701d91532d17eafedd135386cef9dbeaa7eabbb",
            "blockNumber":"0x7c8764",
            "data":"0x",
            "logIndex":"0x82",
            "removed":false,
            "topics":[
                "0x8c5be1e5ebec7d5bd14f71427d1e84f3dd0314c0f7b2291e5b200ac8c7c3b925",
                "0x000000000000000000000000bdafc1b001965e1a45ecf960589e4c46cf81c423",
                "0x0000000000000000000000000000000000000000000000000000000000000000",
                "0xbedcd1027afa1c5ddb27af17e4050526ec800ec78979f891b1e0f3e987fd3c8c"
            ],
            "transactionHash":"0x6a5bac15c85b38292dbabe6c7d14688e24efe2a4e1f3bb4fa91c9f193ca0cbc9",
            "transactionIndex":"0x36"
        },
        {
            "address":"0xbbeaf5f51fdfaaec9af54135ec6fcab3c9ec8d6e",
            "blockHash":"0x5c19e0ae6429b5fcffbcafe19701d91532d17eafedd135386cef9dbeaa7eabbb",
            "blockNumber":"0x7c8764",
            "data":"0x",
            "logIndex":"0x86",
            "removed":false,
            "topics":[
                "0xddf252ad1be2c89b69c2b068fc378daa952ba7f163c4a11628f55a4df523b3ef",
                "0x000000000000000000000000bdafc1b001965e1a45ecf960589e4c46cf81c423",
                "0x000000000000000000000000779a6b3f54e50228ca121529422cbdbd8bc2822b",
                "0xbedcd1027afa1c5ddb27af17e4050526ec800ec78979f891b1e0f3e987fd3c8c"
            ],
            "transactionHash":"0x6a5bac15c85b38292dbabe6c7d14688e24efe2a4e1f3bb4fa91c9f193ca0cbc9",
            "transactionIndex":"0x36"
        }
    ]
}
```
![image](https://user-images.githubusercontent.com/32976079/208379376-f5f052c3-7e82-4208-8527-d01262fc7709.png)







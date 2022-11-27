


#### 1) 获取某个 owner 拥有的 DID 列表

```shell
curl 'http://8.136.211.11/didNode/getDidNodeListByAddress?owner=0x6dcd82959e68f41b3a365c40f57b9a54cdd230e1'
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


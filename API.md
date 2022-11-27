


#### 1) 获取某个 owner 拥有的 DID 列表

curl 'http://8.136.211.11/didNode/getDidNodeListByAddress?owner=0x6dcd82959e68f41b3a365c40f57b9a54cdd230e1'


#### 1) 获取某个 DID 当前可领取的分红额度

```shell
curl http://8.136.211.11/didNode/getLatestDivident --request POST --header "Content-Type: application/json" --data 
'{
"signature":"0x4a3e1c9108720e8c7c6c5d824ffe5b7c544a6e017300511c597aab2f113610e37494e5908e364bde235dc28f902d1ce86c767cb13291aa13adcb930b5296a5f11c", 
"node":"0x4e772f62035453f381d9e8495f65ea4d5c90168c61878c755d8b2c9170e259d2"
}'
```




# DID Swap--用于交易DID的简化版NFT-DEX

## v 0.1

![image](https://user-images.githubusercontent.com/32976079/205847335-58c490da-ee3c-4450-9ede-b8413007bf43.png)

第 0 步骤在理论上可以省略。因为 DID-Swap 合约是一个配套合约，可以默认具备 Transfer DID-NFT 的能力。但考虑到 DID-NFT 价值较高，若用户不小心被钓鱼、被误导签署一个低价订单信息，则会被骗取 DID-NFT。因此用户在挂单的时候，最好还是加一个 Approve 操作（让用户发送亲自发送 Approve-Tx 上链，允许 DID-Swap 可以 Transfer DID-NFT），以提醒用户。


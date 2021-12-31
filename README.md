# KSX-airdrop

## The airdrop distribution of KSX:
### (1) PCX holders(>= 1 pcx)

snapshot1(`ss1`) on the block `2761158` of `ChainX2.0`, 
snapshot2(`ss2`) on the block `2004141` of `ChainX3.0`,
 
 ```txt
 if ss1 - ss2 >= 1 pcx:
    if ss2 != 0:
        genesis: 10% of ss2 is free, 90% of ss2 to vesting(from block 1296000, end block 3888000)
    transfer: 100% of (ss1 - ss2) to vesting(from block 3888000, end block 9072000)
 else:
    genesis: 10% of ss1 is free, 90% of ss1 to vesting(from block 1296000, end block 3888000)
 ```
- the origin snapshot files(decimal=8):
  - [chainx_snapshot1](./origin_chainx_snapshot1_non_dust_7418_10500000000000000000000000_on_2761158.json)
  - [chainx_snapshot2](./origin_chainx_snapshot2_non_dust_22295_11985224700000000000000000_on_2004141.json)
- the genesis balance file(decimal=18):
  - [genesis_balance_chainx](./genesis_balances_chainx_snapshot_7418_7868415220855310000000000.json)
- the genesis vesting file(decimal=18):
  - [genesis_vesting](./genesis_vesting_342138_894151599020746000000000.json)
- the transfer vesting file(decimal=18):
  - [transfer_vesting](./transfer_vesting_1990_2631584779144690000000000.json)

### (2) ComingChat miners(>= 1 ksx)
```txt
genesis: 10% is free, 90% for vesting(from block 1296000, end block 3888000)
```
- the origin snapshot file(decimal=8):
  - [origin_comingchat](./origin_comingchat_miners_334721_214074281900000_decimal_8.json)
- the genesis balance file(decimal=18):
  - [genesis_balance_comingchat](./genesis_balances_comingchat_miners_334721_2140742819000000000000000.json)
- the genesis vesting file(decimal=18):
  - [genesis_vesting](./genesis_vesting_342138_894151599020746000000000.json)

### (3) SherpaX contributors(on kusama)
```txt
genesis: 100% is free
```
- the origin file(Kusama address, ss58 prefix:2, decimal=8):
  - [origin_sherpax_contributors](./origin_sherpax_contributors_1873_9404698487265_decimal_8.json)
- the genesis balance file(SherpaX address, ss58 prefix:44, decimal=18):
  - [genesis_sherpax_contributors](./genesis_balances_sherpax_contributors_1873_94046984872650000000000.json)


## Generate the snapshot on ChainX

```bash
# Compile the binary
$ git clone https://github.com/chainx-org/chainx-cli
$ cd chainx-cli
$ cargo build --release --bin snapshot_balances

1. ChainX 2.0 snapshot1 on block 2761158, min-balance=100000000

```bash
$ ./target/release/snapshot_balances --block-number=2761158 --url=ws://47.99.179.60:18087 --min-balance=100000000
On ChainX(decimals=8)  
        Total issuance: 1050000000000000
        Total accounts: 18165
     Non-dust accounts: 7418
Minim balance for dust: 100000000
         Dust accounts: 10747
   Total dust balances: 82628223512
      Treasury balance: 94591231912999
 X-association balance: 12090344828274
==========================
  On SherpaX(decimals=18)
     Total airdrop ksx: 10500000000000000000000000
        Total accounts: 18165
     Non-dust accounts: 7418
Minim balance for dust: 1000000000000000000
         Dust accounts: 0
   Total dust balances: 0
      Treasury balance: 1067642049647850000000000
 X-association balance: 0
Total non-dust balance: 10500000000000000000000000

```

2. ChainX 3.0 snapshot2 on block 2004141, min-balance=1
```bash
$ ./target/release/snapshot_balances  --block-number=2004141 --url=ws://47.99.179.60:8087 --min-balance=1
   On ChainX(decimals=8)  
        Total issuance: 1198522470000000
        Total accounts: 22424
     Non-dust accounts: 22295
Minim balance for dust: 1
         Dust accounts: 129
   Total dust balances: 0
      Treasury balance: 118654859286008
 X-association balance: 1526137095776
==========================
  On SherpaX(decimals=18) 
     Total airdrop ksx: 11985224700000000000000000
        Total accounts: 22424
     Non-dust accounts: 22295
Minim balance for dust: 10000000000
         Dust accounts: 0
   Total dust balances: 0
      Treasury balance: 1201809963817840000000000
 X-association balance: 0
Total non-dust balance: 11985224700000000000000000
```

## Generate genesis files from origin files
```bash
$ cargo build --release --bin generate_airdrop 
```

```bash
# Compile the binary
$ git clone https://github.com/chainx-org/chainx-cli
$ cd chainx-cli
$ cargo build --release --bin generate_airdrop

$ ./target/release/generate_airdrop 
treasury balance: 1067642049647850000000000
total genesis balances: 10103205024727960000000000
total genesis accounts: 344012

```


## License

MIT

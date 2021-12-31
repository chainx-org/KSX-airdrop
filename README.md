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
  - [genesis_vesting](./genesis_vesting_342133_894769078020746000000000.json)
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
  - [genesis_vesting](./genesis_vesting_342133_894769078020746000000000.json)

### (3) SherpaX contributors(on kusama)
```txt
genesis: 100% is free
```
- the origin file(Kusama address, ss58 prefix:2, decimal=8):
  - [origin_sherpax_contributors](./origin_sherpax_contributors_1873_9404698487265_decimal_8.json)
- the genesis balance file(SherpaX address, ss58 prefix:44, decimal=18):
  - [genesis_sherpax_contributors](./genesis_balances_sherpax_contributors_1873_94046984872650000000000.json)

### (4) Duplicate contributors for vesting
- [duplicate_contributors](./handle_duplicate_contributors_in_genesis_vesting_35_617479000000000000000.json)

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
duplicate account = 20b734b5180f6433f2989259cf3a5df633dea6b46ba6bb6630b4bab06cbc3937 (5QNvL6E6...)
duplicate account = 6800fb64dc5123dff9b6e59a9a49f0fca600acf404aa43935f279cba433f5765 (5RzPeQuq...)
duplicate account = c8b8efce57e41578ca0d00a33880f5d46f793c46c2ac2ec3798d5c8d82de9806 (5UBCtW2x...)
duplicate account = ba84803fe10c358afa418b34a77b99486458e0f021edbef0e02a80c2abef526f (5TraeAv7...)
duplicate account = 9a36dc0100f79de40ed7cd32ee5d419ba7993e786ec12d1a5eeb698db59c6b7a (5T8E3Zgv...)
duplicate account = 86893e603e3d539aad64c7628ba32d3956b05c15e696e3eba8f6d7dc28898a44 (5SgRZTyt...)
duplicate account = 5446c059c4c78c9ead43f0694ab1eda254de55c5db245c4f8e45d95fc62def47 (5RYXQxvK...)
duplicate account = 62c794178f7db53ae8b5c51e7f8b9549dc4db6ec9b4ebdc4ea08ca7011378655 (5RsYMVBx...)
duplicate account = 8a9336fa6586b4f169faafd82b2e4606b84754cc9c6601be0c83ebe1a6baa17e (5SmiiNcC...)
duplicate account = 086b3cff28537011ee3cdb33556a85d93cb1d836c7bb2c8e9a000a339d887136 (5Pq4cYVZ...)
duplicate account = 9aaca335cc3dce64d9ed58100cafbefb2bb2973985671676c7d645936a5d172b (5T8q2qN7...)
duplicate account = b0abc016de3de48fab82aa64f39bdb564f88fe8895fbfc21784ce8178f60c833 (5Tdfpeda...)
duplicate account = 6c827b4eccd5064ff0e86f45feee38fb250a50a972e011f1878bf2c7e7dd154b (5S6JJkRr...)
duplicate account = eaaacd9cbf6259cc66762b5a3ed80aac119b5a6a08a5702af742d0c6d3266b63 (5UwiKQyz...)
duplicate account = 288590b23f917d0267e236709e712ce75d6b3ba05ff32b131644ee40e5949035 (5QZ9y29c...)
duplicate account = badace46a7289c1a649b7ae47a6b27c0a0fb08256d5930781b94bf6c58991831 (5Ts2HAjn...)
duplicate account = 08b5720788f324eff6434d3335e91489e094bb56d0c2f646ca61244df4fee227 (5PqSf6x1...)
duplicate account = 4838584231c994555b350282ec59becc7333342a01300edb04b5ac0c643a5428 (5RGiZR9J...)
duplicate account = 86543cac853c46ee4548d2e6d8c053bacf313a644b4081f3ca7641c3cc17823a (5Sg9pBYu...)
duplicate account = 846c6071b7979fb16985aed1d99298dfa3769bd2638cbcc617818fdef44de94b (5SdetYch...)
duplicate account = aa48a9775be7af0521acefce054dc7e9e461814dc167a5cabf52aef8534d8249 (5TVJ6jTa...)
duplicate account = acfadc62166b06e66b861fdb0af2edbb6b581da41bcd218ecbd18335fff09c03 (5TYq8amH...)
duplicate account = e8ab719d5be4839e7bf10eceb7ecdf37b24b6560aa64eb8879e2158df19b4678 (5Uu6Qu1d...)
duplicate account = 5a86d52adf719a0208d30854e5f9b6c5300cde5fa59c731a8cf9cc4f5382ed78 (5RgijixQ...)
duplicate account = 7c8bd2e760fbf79db9ef22e7728b94f5cd91cb09a111b50f3fe04116482f081c (5STKr9Zg...)
duplicate account = e62321ed84ec54791122f2ec72e9e36d3cb336ed358d6848a65b8410b405650a (5Uqmpkhj...)
duplicate account = eed1f0f53dd77141b7e14c986f47952c83bceaa85330bbb79bd5049c02c6002d (5V3A8reV...)
duplicate account = 745de9aab104325eefcea15e558099ac7db40f48ac342e0863562e1ed1fc293b (5SGbpuBJ...)
duplicate account = a2aa924f5b2b259458b89afeca1c426baed615c77f224e82ae1c6f59f7472851 (5TKJoTS6...)
duplicate account = 067cdfcf99f0307a91d975ccd3a1068d2743292de108360b1d8c1347a3332058 (5PnXkrGW...)
duplicate account = 54314f63f3d6ac30a8c0cc97e6942692c220fa2e7cdf0fe230225bb25e322749 (5RYR3YKU...)
duplicate account = b433a9f040db8c1cd7c8b6200cb787c70bb008cd79cc3d165f9f514388378c4b (5TiJLiVW...)
duplicate account = f2d72be858b916dc908862b10d4c1ff7dc0644d78475041968b14e41b9972f1d (5V8Rt5gX...)
duplicate account = d8072e920d26e8f338ba937e6fb4a4da98e1b646e83331431b50ba34789cbe75 (5UXGrJ1S...)
duplicate account = 02f94cd1f7f92e67faec8b396849d8cb9ba3c9a7cf0289d8b72553af6167a44c (5PhvXYjU...)
duplicate account = a0fa4b3c53ee1c88c6296a0bffed20638d366f3693f0cd0d41454a68f3ad766e (5TH6PVAC...)
duplicate account = 6e753aa0bf6a3699bf1820cd8cb87cd1fd7c88d0c3e9c194a5055bbf6d338047 (5S8rTxzm...)
duplicate account = e63a2982dec29f65797285327bac0f0cd3db6988439aa8f9b729c6768eae7606 (5UqtfYbC...)
duplicate account = f2c948ac572ac7224de65019e2d91e11ada26ff6c10fa63873c59562c50ca451 (5V8MkoY5...)
duplicate account = 1024d5c7c359048f593fac90652e61b58cf9cfceab4f2828ab77743735bc9611 (5Q1C5k5g...)
Need manual process duplicate account balance.(ignore if handled)

treasury balance: 1067642049647850000000000
total genesis balances: 10103205024727960000000000
total genesis accounts: 344012
total genesis vesting: 8942133469207460000000000

```


## License

MIT

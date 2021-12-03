# ChainX CLI 2.0

[![CI](https://github.com/chainx-org/ChainX/workflows/ci/badge.svg)](https://github.com/chainx-org/ChainX/actions?workflow=ci)

Rust Command Line Interface for [ChainX 2.0](https://github.com/chainx-org/ChainX/tree/develop-2.0) based on [substrate-subxt](https://github.com/paritytech/substrate-subxt).

## Build

```bash
$ git clone https://github.com/chainx-org/chainx-cli
$ cd chainx-cli

# There are multiple binaries in this repo.
# You might be solely interested in chainx-cli, then
# simply running `make` or using the following command
# directly will do and no other binaries will be compiled.
$ cargo build --release --bin chainx-cli

# This will compile all the binaries.
$ cargo build --release
```

## Usage

```bash
$ ./target/release/chainx-cli --help
```

```bash
$ git checkout on_sherpax
$ cargo build --release --bin snapshot_balance
$ ./target/release/snapshot_balances --url ws://127.0.0.1:8087 --block-number 2761158
   On ChainX(decimals=8)  
        Total issuance: 1050000000000000
        Total accounts: 18165
          KSX accounts: 7418
 Dust accounts(< 1PCX): 10747
   Total dust balances: 82628223512
      Treasury balance: 94591231912999
 X-association balance: 12090344828274
==========================
  On SherpaX(decimals=18) 
       Total issuance:  10500000000000000000000000
       Total accounts:  18165
 Dust accounts(< 1KCX): 10747
    Total dust balance: 826282235120000000000
     Non-dust accounts: 7418
Total non-dust balance: 10499173717764880000000000
         Vest accounts: 7417
        Vesting liquid: 943235795035215000000000
    Total vest balance: 9432357950352150000000000
      Treasury balance: 1066815767412730000000000
 X-association balance: 0
```
## License

[GPL v3](./LICENSE)

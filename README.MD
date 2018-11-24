# Freeze

### Description

Freeze transfer of EOS tokens with a balance greater than 10

List of test steps:

```sh
$ eosio-cpp -o freeze.wasm freeze.cpp
$ cleos set contract freeze $CONTRACTDIR/freeze --abi freeze.abi -p freeze@active
$ $ cleos create account eosio bob YOUR_PUBLIC_KEY 
$ cleos create account eosio alice YOUR_PUBLIC_KEY
$ cleos create account eosio freeze  EOS6MRyAjQq8ud7hVNYcfnVPJqcVpscN5So8BhtHuGYqET5GDW5CV
$ cleos push action freeze create '[ "eosio", "10000000.0000 EOS"]' -p freeze@active
$ cleos push action freeze create '[ "eosio", "10000000.0000 QWE"]' -p freeze@active
$ cleos push action freeze issue '[ "alice", "50.0000 QWE", "memo" ]' -p eosio@active
$ cleos push action freeze transfer '[ "alice", "bob", "5.0000 QWE", "m" ]' -p alice@active
$ cleos push action freeze issue '[ "alice", "9.0000 EOS", "memo" ]' -p eosio@active
$ cleos push action freeze transfer '[ "alice", "bob", "5.0000 EOS", "m" ]' -p alice@active
$ cleos push action freeze issue '[ "alice", "20.0000 EOS", "memo" ]' -p eosio@active
$ cleos push action freeze transfer '[ "alice", "bob", "5.0000 EOS", "m" ]' -p alice@active
$ cleos get currency balance freeze alice EOS
$ cleos get actions alice
```
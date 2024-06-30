# OP-Challenger

The `op-challenger` is a modular **op-stack** challenge agent written in
golang for dispute games including, but not limited to, attestation games,
fault games, and validity games.

DISPUTE_GAME_FACTORY=$(jq -r .DisputeGameFactoryProxy addresses.json)
./op-challenger/bin/op-challenger \
  --trace-type cannon \
  --l1-eth-rpc http://localhost:8545 \
  --rollup-rpc http://localhost:9546 \
  --game-factory-address $DISPUTE_GAME_FACTORY \
  --datadir temp/challenger-data \
  --cannon-rollup-config .devnet/rollup.json  \
  --cannon-l2-genesis .devnet/genesis-l2.json \
  --cannon-bin ./cannon/bin/cannon \
  --cannon-server ./op-program/bin/op-program \
  --cannon-prestate ./op-program/bin/prestate.json \
  --l2-eth-rpc http://localhost:9545 \
  --mnemonic "$MNEMONIC" \
  --hd-path "m/44'/60'/0'/0/8" \
  --num-confirmations 1

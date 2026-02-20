# octra_ref_client
a fast python TUI client for prototyping and references for octra network, with full HFHE (PVAC ver.) support out of the box (will include test variations and demo examples for quick feature exploration)

to build and run, you will need a precompiled pvac-hfhe library with support for SIMD instructions (will come right here with specific rules for assembly and testing)

**this cli version won't work with the mainnet yet, because we haven't done the merge and haven't formed the merge protocol (this will be done in about a week), but for now you can carefully test it**


**PS: if you've built this, go to the faucet and get devnet coins https://faucet-devnet.octra.com (you can test all the features)**

## pvac-hfhe (setup, build and run)

```bash
git clone https://github.com/octra-labs/octra_ref_client.git
cd octra_ref_client
chmod +x setup.sh
./setup.sh
```

then setup.sh will:
1. check that `g++` and `python3` are installed
2. build `libpvac` (PVAC-HFHE) from C++ src
3. create a python venv and install
4. print the run command

### macOS
```bash
xcode-select --install
```

### ubuntu or debian
```bash
sudo apt update && sudo apt install -y g++ make python3 python3-venv python3-pip
```

## сreate a wallet for octra or use an existing wallet.json (all mainnet priv keys are 100% compatible with devnet)

```bash
./venv/bin/python3 cli.py
```

## requirements

- **g++** with C++17 support
- **python 3.10+**
- **make**

## links

- devnet RPC: https://devnet.octra.com (USE http://165.227.225.79:8080"!!!!)
- scan: https://scan.octra.com 
- faucet: https://faucet-devnet.octra.com (10 OCT every day)

## config

wallet.json contains your priv key, address, and RPC endpoint (dont lose it and DONOT publish anywhere)
```json
{
  "priv": "...",
  "addr": "oct...",
  "rpc": "http://165.227.225.79:8080""
}
```
to change RPC endpoint edit `wallet.json` directly
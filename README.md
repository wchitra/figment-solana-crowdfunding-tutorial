# Solana Learnings

This project was a tutorial from Figment, https://learn.figment.io/tutorials/crowdfunding-with-solana

## Launching the application

Refer to https://docs.solana.com/cli to configure the Solana CLI & generate keypair

## Solana (Rust program side)

## Local Testnet

1. Navigate to the Rust program directory.
```bash
cd program
```
2. Compile the program
```bash
cargo build-bpf --manifest-path=Cargo.toml --bpf-out-dir=dist/program
```
3. In a seperate terminal, start the local cluster
```bash
solana-test-validator
```
4. In another seperate terminal, listen to the logs
```bash
solana logs
```
5. Deploy the program
```bash
solana deploy --keypair <path_to_keypair_json> dist/program/program.so --url http://127.0.0.1:8899
```
6. After successful deployment, take the Program ID displayed in the terminal and set it as the program id for the front-end, `../src/solana/index.js`
```bash
const programId = new PublicKey(<program id>);
```


## DEVNET

1. Execute steps 1, 2.
2. Replace step 5 with
```bash
solana deploy --keypair <path_to_keypair_json> dist/program/program.so --url https://api.devnet.solana.com
```
3. Execute step 6.

## Front-end
1. Download dependencies
```bash
yarn
```

2. Run local node server
```bash
yarn run
```



3. Have the Phantom wallet browser extension installed to sign transaction. Also, be sure to have it set the right cluster.

## Debugging Lessons Learn

1. In the program, msg!() is my friend.
2. When there is an error, the msg!() message can be seen in the browser terminal. Super helpful, since the messages won't display in the solana logs when there is a error (or a panic).
3. In programs, serializing is like saving data... OK()
4. Seems to be a lot of checking to see if the account owner is the program id
5. Error messages are cryptic, so have to navigate to the source code to figure out what the actual error is.



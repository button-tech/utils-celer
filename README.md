# Celer specific setup for [hackathon-eth-denver]("https://github.com/button-tech/hackathon-eth-denver") 

For the purpose of the [Etheregram]("https://github.com/button-tech/hackathon-eth-denver")  project, we run two celar, clients and hardcode their public address in the bot.
We expect that in some day it will be possible for a user to sign the transaction and send it to celar network without running own instance of celar client that.

For now we launch two celar nodes and hardcode account public keys it the app. 

In order to launch the project with your own celer clients and `keystore ` accounts you will need:
1) Clone [Celer client](https://github.com/celer-network/celer-client)
2) Generate two `keystore` using geth, save it as `key-A.json` and `key-B.json`. Remember password, you will need it further to launch `celer_client`
3) Deposit [test ether](https://faucet.ropsten.be/)( ropsten) to accounts from `keystore`
4) Launch two instances of celer client
    ```
    ./celer_client_mac -keystore key-A.json -config profile.json -port 30000
    ./celer_client_mac -keystore key-B.json -config profile.json -port 30001
    ```
5) Update [frontend](https://github.com/button-tech/hackathon-eth-denver/blob/master/frontend/src/js/celer/index.js#L4) file, instead of
    ```
    window.eth2celerhost = {
        "149960814b05d5560bba5000f6c9852c250611bd": "https://ethergram.tk/c0",
        "f6cdf7cdc1d804765c481d03ce0e545d073219d9": "https://ethergram.tk/c1"
    };
    ```

    Put
    ```
    window.eth2celerhost = {
        "you-public-address-from-key-A.json": "http://localhost:30000",
        "you-public-address-from-key-B.json": "http://localhost:30001"
    };
    ```

## Integration with celer in demo project
TODO: Sequence diagram

## Possible Setup for the bot that doesn't store user private keys
TODO: Sequence diagram

## Possible Setup for the bot that stores private keys
TODO: Sequence diagram

Usage
=====

.. _installation:

How to Prepare 🥘
------------

Clone this repository

.. code-block:: console

   git clone https://github.com/Joshua-Oladeji/GingerBread.git

Creating recipes
----------------

- run ``npm install`` from the root directory to install dependencies

- Fill the ``.env.example`` file with the appropriate data and rename the file to ``.env``
- ``PRIVATE_KEY``: private key of the contract deployer address (metamask)
- ``GANACHE_PRIVATE_KEY`` private key of the deployer address from Ganache
- ``GANACHE_ADDR1_PRIVATE_KEY`` private key of another address from Ganache. This is only needed if you want to run the unit tests.
- ``C_CHAIN_NODE``: a link that connects you to an avalanche C-chain node. you can get a 'speedy-node' from `moral.io <https://moralis.io/>`_.
- ``TELEGRAM_BOT_TOKEN``: an authorization token from Telegram's Bot father. it's pretty easy to `get one <https://core.telegram.org/bots#6-botfather>`_.
- ``SERVER_URL``: base url of your server. it's for configuring a webhook for your telegram bot. if you're running on localhost, you will need to expose your server via a public url. check out `ngrok <https://ngrok.com/>`_.
- ``FLASH_SWAP_ADDRESS``: contract address of the bot you'll deploy

- compile the contract using the following command:
```
npx hardhat compile
```

- deploy the contract to your preferred network. available networks can be found in `hardhat.config.js`. default network is **Ganache**, so make sure to spin up a local blockchain using ganache before running this command.
```
npx hardhat run scripts/deploy.js --network <network-name>
```

- run the ``server.js`` file, relax and wait to be served.
|

Methods ⚡
-------
You might want to know the purpose of each method if you want to tweak some things in the recipe.

**constructor(token0, token1)** 🔥
- a new GingerBread is initialized with 2 parameters which represents the tokens that constitute a pair.
- each parameter is an object containing the 'symbol', 'address' and 'volume' keys.... like so:

.. code-block:: javascript

    {
      symbol: 'WAVAX',
      address: '0xB31f66AA3C1e785363F0875A1B74E27b85FD66c7',
      volume: 1000
    }

- **volume** represents the amount of a particular tokens to be borrowed during the arbitrage.
- bake() 👩‍🍳
-------
- this method runs the bot by listening to every new block and executing arbitrage opportunities if they exist.
taste() 🍰
------
- logs the prices of the tokens on the `pangolin <https://pangolin.exchange/>`_ and `traderjoe <https://traderjoexyz.com/home#/>`_ DEXes.
- logs the potential profit/loss realized if an arbitrage is attempted based on the current tokens prices.
.. image:: https://user-images.githubusercontent.com/53357470/160957408-bfa8c628-baa0-45a8-bd82-d1f5be163d03.png
serve() 🍽
------
- adds listeners for all events on the FlashSwapper contract. info from every event is then emitted to be logged to telegram.
flourRemaining()
_______________
- returns the balance of AVAX remaining (gas fees) in the FlashSwapper contract.
|
|
|

Written originally as a submission for `@cryptofishx <https://twitter.com/cryptofishx/status/1491621931866599426?s=20&t=LnQLaVok2Aww0-gCxqYQdQ>`_




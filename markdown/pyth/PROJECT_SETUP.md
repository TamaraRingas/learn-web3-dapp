{% hint style="tip" %}
We recommend completing both the [Solana 101 pathway](https://learn.figment.io/protocols/solana) and [Build a Solana Wallet](https://learn.figment.io/pathways/solana-wallet) before continuing. A working knowledge of [React hooks](https://reactjs.org/docs/hooks-intro.html) and [TypeScript/JavaScript](https://www.typescriptlang.org/) is also recommended.
{% endhint %}

# 🦺 Important information for your safety

During this Pathway, we will provide you with an opportunity to use the Solana [mainnet-beta cluster](https://docs.solana.com/clusters#mainnet-beta) (hereafter referred to as "mainnet") to perform token swaps with [Jupiter](https://jup.ag), a liquidity aggregator for Solana - which means that **actual funds may be used**.

This is **not** a requirement for completing the Pathway & we have made sure to _clearly mark the difference_ between using the **devnet cluster** and the **mainnet cluster**. Be aware that during step 4 of the Pathway ("Wallet implementation"), we will explain how to use the private keys of Solana keypairs. You will be instructed to input the private key of a **devnet only** wallet, which we will walk you through setting up. Solana keypairs can be created using the Solana CLI, or with the JavaScript API, or even by using a browser extension wallet such as [Phantom](https://phantom.app).

You should **never** share your private keys with anyone. The simplest and most secure approach to this issue is to create an account entirely for the purpose of the following tutorials. Before proceeding, it is extremely important for you to understand that **if you provide the private key of a Solana account containing mainnet SOL to the wallet component in the Pathway, you are _potentially_ risking the full amount of SOL in that account**.

There is a wallet component used in several steps of the Pathway which has a toggle switch between "mock" and "live". When the toggle is set to "live", you will be able to provide a [private key](https://solana-labs.github.io/solana-web3.js/classes/Keypair.html). This private key is then stored in the local storage of your web browser, so that you do not need to enter it multiple times. If you are not already familiar with it, read more about [web browser local storage](https://blog.logrocket.com/localstorage-javascript-complete-guide/) to understand where and how this data is kept.

Note that in order to perform _any_ swaps on Solana mainnet using this project, you must:

- Own a funded account on mainnet containing an amount of SOL and the USDC SPL token
- Be on Step 6, "Token swaps on a DEX" or Step 7, "Liquidation bot implementation"
- Toggle the wallet component from "mock" to "live", then switch it from devnet to mainnet which will present you with an alert warning you that you're going live on mainnet with real economic exposure
- Copy and paste the private key of your funded account into the textinput of the **live** wallet component

If this doesn't make sense yet, don't worry. This is just a heads up. It will make more sense in the context of the Pathway implementation 😁

---

# 🧑‍💻 Install the Pyth client

In order to use Pyth, you will need to install the TypeScript/JavaScript library for off-chain applications. It provides the tools to do things like displaying the Pyth price on a website. Whether you're using Gitpod or a local clone of the repo, the installation procedure is the same. Run the terminal command below inside the root directory of the project (`learn-web3-dapp/`) :

```text
yarn add @pythnetwork/client
```

This Pathway will only cover use of `@pythnetwork/client`. There are also Rust- Python- and EVM-based clients. Refer to the [list of available client libraries](https://docs.pyth.network/consumers/client-libraries) in the Pyth documentation for more.

---

# 👻 Install the Phantom wallet extension

Turn your favorite browser into a Web 3 enabled crypto wallet!

Go to <https://phantom.app> and click on the "Add to ..." button which will auto-detect your browser and redirect you to the appropriate extension page:

- Firefox: https://addons.mozilla.org/en-US/firefox/addon/phantom-app/
- Chrome / Brave / Edge: https://chrome.google.com/webstore/detail/phantom/bfnaelmomeimhlpmgjnjophhpkkoljpa?hl=en

Optionally, check out <https://phantom.app/security> to learn more about the security features of Phantom.

---

# 🧩 DataHub API keys

If you wish to make use of the Pathway content using DataHub, you will need a DataHub account and a valid API key to access Solana via DataHub's infrastructure. [Sign up for a DataHub account](https://datahub.figment.io/sign_up) and verify your email address.

To use your API key, you should copy the contents of the `.env.example` file located in the project root directory (`/learn-web3-dapp/.env.example`) into a new file named `.env.local` (`/learn-web3-dapp/.env.local`).

{% hint style="info" %}
Easily duplicate the file with the terminal command `cp .env.example .env.local`!
{% endhint %}

Find your unique API key on the [**DataHub Services Dashboard**](https://datahub.figment.io/). Click on the **Solana** icon in the list of available protocols, then copy your key as shown below:

![](https://raw.githubusercontent.com/figment-networks/learn-web3-dapp/main/markdown/__images__/solana/solana-setup-00.gif?raw=true)

You can then paste your unique API key into `.env.local`, as the value for the environment variable `DATAHUB_SOLANA_API_KEY`. This will authenticate you and enable you to make JSON-RPC requests to Solana via DataHub:

```yaml
# DataHub API keys
DATAHUB_AVALANCHE_API_KEY=
DATAHUB_CELO_API_KEY=
DATAHUB_NEAR_API_KEY=
DATAHUB_POLKADOT_API_KEY=
DATAHUB_POLYGON_API_KEY=
DATAHUB_SECRET_API_KEY=
DATAHUB_SOLANA_API_KEY=81436edcf907b0fbb8493d281cdff5af
DATAHUB_TEZOS_API_KEY=
```

{% hint style="tip" %}
The API key shown above is only an example and cannot be used to access DataHub.
{% endhint %}

---

# 👣 Next Steps

Once you have your Solana API key saved in `/learn-web3-dapp/.env.local`, you're ready to begin.
Click on the **Next: Connect to Pyth on Solana** button below.
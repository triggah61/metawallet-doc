Note: This documentation version is aimed at dApp developers who would like to connect to Metawallet. The code snippets are included for their benefit. Tutorial links were added for beginners who may be interested to use Metawallet for their future dApps.

&nbsp;
# Osiris Metawallet Documentation: Developers&#39; Section
&nbsp;
The Osiris Metawallet is the native multi-crypto wallet of Decenternet which is tightly integrated to Decenternet&#39;s Osiris browser, a secure, blockchain-based web 3.0 browser with dApp rendering capabilities and multi-crypto wallet integration. Metawallet features multi-blockchain support and allows users to transact crypto through its user interface (UI) supporting wallet transactions such as send, receive, and view wallet balance.

This API aims to simplify the process of transacting and authorizing crypto financial transactions for web-based decentralized Apps (dApps).

The sections below detail Ethereum dApp development and interaction with the Ethereum blockchain. More blockchains and dApp capabilities will be integrated into Metawallet and documented here in the future.
&nbsp;
## Web dApp Development

### **Basic Website Interactions**

When you install and run Metawallet, Metawallet creates &quot;window.ethereum&quot; object in the browser tabs which you can see in the developer console. This object allows websites to interact with Metawallet.

 * ***Verifying If Metawallet is installed***

With the &quot;window.ethereum&quot; object, you can verify whether the Metawallet is installed with the following Javascript snippet:
```
if (typeof window.ethereum !== 'undefined') {
  // Metawallet is installed, add your logic here
} else {
  // Metawallet is not installed, add your logic here to inform user to install Metawallet.
}

```
* ***Connecting to Metawallet***

Your website can interact with Metawallet by connecting to it. This will give your website access to the Metawallet of the browser user with the user confirming transactions and actions to his Ethereum accounts via Metawallet.

We recommend that you provide a button to connect to Metawallet with the following sample snippets:

**HTML:**
```
<button class="metawalletButton">Connect to Metawallet</button>
```
**Javascript:**
```
const metaButton = document.querySelector('.metawalletButton');

metaButton.addEventListener('click', () => {
  //Will activate Metawallet
  ethereum.request({ method: 'eth_requestAccounts' });
});

```
You can try this snippet in JSfiddle ([https://jsfiddle.net/decenternet/Lad9q27p/4/](https://jsfiddle.net/decenternet/Lad9q27p/4/))

Here are some recommendations when connecting with Metawallet:

- Initiate a connection request in response to direct user action, such as clicking a button.
- Always disable the &quot;connect&quot; button while the connection request is pending
- Never initiate a connection request on page load.

* ***Displaying Metawallet Account***

Once you are connected to Metawallet, the API method &quot;eth\_requestAccounts&quot; will return a promise which will resolve to an array of Ethereum addresses once connected toMetawallet. The array&#39;s first entry is the active Ethereum account connected, which can be used as the reference account when sending transactions and processing actions.

The following snippets show how to get the active Ethereum account connected:

HTML
```
<button class="metawalletButton">Connect to Metawallet</button>
<h2>Account: <span class="showAccount"></span></h2>
```
Javascript
```
const metaButton = document.querySelector('.metawalletButton');
const showAccount = document.querySelector('.showAccount');

metaButton.addEventListener('click', () => {
  getAccount();
});

async function getAccount() {
  const accounts = await ethereum.request({ method: 'eth_requestAccounts' });
  const account = accounts[0];
  showAccount.innerHTML = account;
}
```
You can try this in this snippet in JSfiddle ([https://jsfiddle.net/decenternet/3qjor1bL/6/](https://jsfiddle.net/decenternet/3qjor1bL/6/))

### **Web3 API**

The Ethereum blockchain provides low-level [JSON-RPC APIs](https://eth.wiki/json-rpc/API) for dApps to communicate with it. There are Ethereum libraries that simplify creation/formatting of these low-level API messages into simpler and easier APIs. Some of these well-known libraries and frameworks are web3.js, ethers, truffle and embark. The most commonly used library is the web3.js.

Multi Wallet is compatible with the web3 APIs that are being used for metamask. You can use these APIs to create Ethereum web3 dApps.

See the [official Web3 API documentation](https://web3js.readthedocs.io/en/v1.3.4/) for a detailed usage of web3.js APis.
&nbsp;
## Sample dApps using Web3 API

* ***Uniswap***

Uniswap is a decentralized finance (DeFi) protocol that is used to facilitate the exchange of cryptocurrency tokens in the Ethereum blockchain.

Visit: [Uniswap](https://uniswap.org/)

* ***CryptoKitties***

CryptoKitties is a dApp game that allows players to collect, breed, and trade (buy and sell) NFT cats.

Visit: [CryptoKitties](https://www.cryptokitties.co/)
&nbsp;
## Learn how to build a Web3 API dApp for Metawallet

New to dApps? Start learning using any of the tutorials below:

- ***Create A Simple Dapp***

[https://docs.metamask.io/guide/create-dapp.html#project-setup](https://docs.metamask.io/guide/create-dapp.html#project-setup)

- ***The Ultimate Ethereum Dapp Tutorial*** (How to Build a Full Stack Decentralized Application Step-By-Step)

[https://www.dappuniversity.com/articles/the-ultimate-ethereum-dapp-tutorial](https://www.dappuniversity.com/articles/the-ultimate-ethereum-dapp-tutorial)

- ***Tutorial for building an Ethereum DApp with Integrated Web3 Monitoring***

[https://www.moesif.com/blog/blockchain/ethereum/Tutorial-for-building-Ethereum-Dapp-with-Integrated-Error-Monitoring/](https://www.moesif.com/blog/blockchain/ethereum/Tutorial-for-building-Ethereum-Dapp-with-Integrated-Error-Monitoring/)

- ***Building a Decentralized Application (DApp) on the Ethereum Blockchain With JavaScript and Solidity***

[https://medium.com/swlh/building-a-decentralized-application-dapp-on-the-ethereum-blockchain-with-javascript-and-solidity-503065ccc23b](https://medium.com/swlh/building-a-decentralized-application-dapp-on-the-ethereum-blockchain-with-javascript-and-solidity-503065ccc23b)



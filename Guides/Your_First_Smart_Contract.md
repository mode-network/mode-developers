
# Deploy your First Smart Contract on Mode

![Mode Smart Contract](https://cdn.hashnode.com/res/hashnode/image/upload/v1706553766780/vwGp1rOt0.jpg "Mode Smart Contract")

Deploy your first smart contract on Mode in less than 10 minutes. 

First of all, you will need to add [Mode network to your preferred wallet](https://docs.mode.network/mode-developer-mainnet/using-mode-mainnet) in order to be able to see tokens and deploy smart contracts to Mode. 

Here’s the information for Testnet and Mainnet:


<div style="text-align: center;">
  <table>
    <tr>
      <th colspan="2">Mode Mainnet Info</th>
    </tr>
    <tr>
      <td >Name</td>
      <td >Value</td>
    </tr>
    <tr>
        <td>Network Name</td>
        <td>Mode Mainnet</td>
    </tr>
    <tr>
        <td>RPC Endpoint</td>
        <td>https://mainnet.mode.network/</td>
    </tr>
    <tr>
        <td>Chain ID</td>
        <td>34443</td>
    </tr>
    <tr>
        <td>Currency Symbol</td>
        <td>ETH</td>
    </tr>
    <tr>
        <td>Block Explorer</td>
        <td>https://explorer.mode.network/</td>
    </tr>
  </table>
</div>

<br/>

<div style="text-align: center;">
  <table>
    <tr>
      <th colspan="2">Mode Testnet Info</th>
    </tr>
    <tr>
      <td >Name</td>
      <td >Value</td>
    </tr>
    <tr>
        <td>Network Name</td>
        <td>Mode Testnet</td>
    </tr>
    <tr>
        <td>RPC Endpoint</td>
        <td>https://sepolia.mode.network/</td>
    </tr>
    <tr>
        <td>Chain ID</td>
        <td>919</td>
    </tr>
    <tr>
        <td>Currency Symbol</td>
        <td>ETH</td>
    </tr>
    <tr>
        <td>Block Explorer</td>
        <td>https://sepolia.explorer.mode.network/</td>
    </tr>
    <tr>
        <td>Bridge URL</td>
        <td>https://bridge.mode.network/</td>
    </tr>
  </table>
</div>

<br/>

Now, you will need to get [Sepolia ETH](https://docs.mode.network/tools/testnet-faucets) for testnet from a faucet to pay the fees for the deployment. 

We are ready to get started!

For simplicity, we will be using [Remix](https://docs.mode.network/build-on-mode/deploying-a-smart-contract/using-remix), an online IDE that is easy to get started with, allowing a simple deployment process, debugging, interacting with smart contracts, and more.

![Remix IDE](https://cdn.hashnode.com/res/hashnode/image/upload/v1706551770268/OEHDn1Cp_.png "Remix IDE")


Here is sample code that comes as default on Remix, you can paste this in any `.sol` file:

    // SPDX-License-Identifier: GPL-3.0

        pragma solidity >=0.8.2 <0.9.0;

        contract Storage {

        uint256 number;
        
        function store(uint256 num) public {
            number = num;
        }

        function retrieve() public view returns (uint256){
            return number;
        }
    }
    

> Make sure to open the advanced configurations and set the EVM version to London. This is to avoid an issue with the PUSH0 opcode. You can read more on the issue with all the Optimism chains [here](https://community.optimism.io/docs/developers/build/differences/#opcode-differences).

<br/>

![Solidity Compiler IDE](https://cdn.hashnode.com/res/hashnode/image/upload/v1706551886961/1vWR1s6oV.png?auto=format "Solidity Compiler IDE")

Once the smart contract is compiled successfully, switch to the `Deploy & Run Transactions` tab.

In the `Environment` dropdown menu, select "Injected Provider - MetaMask"; this will connect your MetaMask to Remix and allow you to make transactions from that connected wallet. In your wallet select Mode as the network before deploying.

![Deploy and run transactions](https://cdn.hashnode.com/res/hashnode/image/upload/v1706551941302/1X7JUaUJy.png?auto=format "Deploy and run transactions")

Select the compiled contract you want to deploy and click `Deploy`.

Now, MetaMask should pop up and ask you to confirm the transaction with super low fees.

![Contract deployment](https://cdn.hashnode.com/res/hashnode/image/upload/v1706551970198/jLsnnEktZ.png "Contract deployment")

<strong>Congrats, you just deployed your first Smart Contract to the Mode Network.</strong>


## Found an issue?

If you have found an issue or bug, please create an [issue](https:/https://github.com/mode-network/mode-developers).

If it's a quick fix, such as a misspelled word or a broken link, feel free to skip creating an issue. You can create a [pull request](https://github.com/mode-network/mode-developers/pulls) directly.

## Have feedback for us?

Feel free to create an [issue](https://github.com/mode-network/mode-developers/issues) with the **feedback** label. Our team will take a look and get back to you as soon as we can!

## Reach out for help

You can discuss ideas, ask questions, and meet other members from the Mode community in our [Discord](https://discord.gg/modenetworkofficial).

If you like, you can also DM us on [X](https://x.com/modenetwork)!

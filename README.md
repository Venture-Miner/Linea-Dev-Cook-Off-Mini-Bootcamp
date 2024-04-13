# Linea Dev Cook-Off Mini-Bootcamp

Material for the Linea Dev Cook-Off Mini-Bootcamp

Join our Academy [Telegram Group](https://t.me/vmineracademy) to participate in our future workshops and bootcamps.

## Part 1: Smart Contract Basics

[![Smart Contract Basics](https://img.youtube.com/vi/lBHHh7HimfA/0.jpg)](https://www.youtube.com/watch?v=lBHHh7HimfA)

Kickstart your blockchain journey with our Linea Dev Cook-Off series!

This tutorial is your gateway to mastering smart contract development using Solidity. Perfect for beginners or as a refresher, we'll guide you through everything from the basics of Solidity syntax to deploying your first ERC20 contract on Linea.

What You'll Learn:

- Solidity fundamentals: syntax, structure, functions, and variables;
- Using Remix for smart contract compilation and deployment;
- Advanced concepts: interfaces, inheritance, tokens, and utilizing the OpenZeppelin library;
- Deploying and interacting with an ERC20 contract in Linea, including Metamask integration.

### Prerequisites

- Basic understanding of blockchain technology;
- A browser with an internet connection;
- A Web3 wallet like Metamask.

### Getting Started

1. Complete the [Setup your Wallet](https://docs.linea.build/use-mainnet/set-up-your-wallet) guide to interact with Linea
2. Follow the [Fund your accounts](https://docs.linea.build/use-mainnet/fund) guide to add some testnet tokens to your wallet
   - Preferably, you can use the [Covalent](https://www.covalenthq.com/faucet/) faucet to get some testnet tokens
   - Alternatively, you can [Bridge Sepolia ETH to Linea Sepolia](https://docs.linea.build/use-mainnet/fund#bridge-sepolia-eth-to-linea-sepolia) if you have some Sepolia ETH available
3. Follow the [Remix](https://docs.linea.build/build-on-linea/quickstart/deploy-smart-contract/remix) guide to deploy your first sample smart contract

### Using Remix

1. Visit the [Documentation](https://remix-ide.readthedocs.io/en/latest/) to learn the main features of Remix for smart contract development
2. Create a new [Workspace](https://remix-ide.readthedocs.io/en/latest/file_explorer.html#workspaces) for this tutorial using the `Remix Default` option
3. Use the [File Explorer](https://remix-ide.readthedocs.io/en/latest/file_explorer.html) to find and open a file named `1_Storage.sol`
4. Use the [Solidity Compiler](https://remix-ide.readthedocs.io/en/latest/compile.html) to compile the smart contract that is open in the editor
   - Make sure the compiler version is set to `0.8.19` for this tutorial, since we are going to deploy the contracts on Linea
   - It's advised to turn on the [Auto compile](https://remix-ide.readthedocs.io/en/latest/compile.html#auto-compile) option to automatically compile the contract whenever you make changes
5. Use the [Deploy & Run Transactions](https://remix-ide.readthedocs.io/en/latest/run.html) tab to deploy the compiled smart contract
   - You can use the default `Virtual Machine` environment to test deploying and interacting with the smart contracts in a quick and practical way, even if you don't have testnet tokens
6. Connect your browser wallet to Remix by selecting the `Injected Web3` environment
   - Make sure the environment is set to `Injected Web3` and the account is connected to your wallet (e.g., Metamask)
   - You can use the `Deploy` button to deploy the contract
     - Differently from the `Virtual Machine` environment, you will need testnet tokens to deploy the contract, and you will be prompted to confirm the transaction on your wallet
7. Interact with the deployed contract using the `Deployed Contracts` section

### Introduction to Solidity in Practice

1. Visit the [Solidity Documentation](https://docs.soliditylang.org/en/v0.8.19/)
2. Using Remix, create a new file named `FrogJump.sol`
3. Put an `SPDX-License-Identifier` at the top of the file and a `pragma` statement to specify the compiler version according to the [Layout of a Solidity Source File](https://docs.soliditylang.org/en/v0.8.19/layout-of-source-files.html) specifications
4. Plan the [Structure](https://docs.soliditylang.org/en/v0.8.19/structure-of-a-contract.html) of the contract
   - The deployer should deploy the contract and set a `name` to the frog
   - Anyone should be able to call a function to get the `name` of the frog
5. Create a `contract` definition for the `FrogJump` contract
6. Add a [State Variable](https://docs.soliditylang.org/en/v0.8.19/structure-of-a-contract.html#state-variables) named `name` of type [string](https://docs.soliditylang.org/en/v0.8.19/types.html#bytes-and-string-as-arrays), and put it as `public` [Visibility](https://docs.soliditylang.org/en/v0.8.19/contracts.html#state-variable-visibility) to allow anyone to easily read it
   - Marking a state variable as `public` automatically creates a [Getter](https://docs.soliditylang.org/en/v0.8.19/contracts.html#getter-functions) function for it
   - Marking a state variable as `public` doesn't allow writing to it directly from outside of this `contract`, like in other OOP languages
7. Create a [Constructor](https://docs.soliditylang.org/en/v0.8.19/contracts.html#constructors) function to set the `name` of the frog
   - The constructor should receive a `string` parameter and set the `name` state variable
   - Solidity requires us to pick a `data location` for passing strings as parameters, and we should use `memory` for this case
     - You can read more about it [here](https://docs.soliditylang.org/en/v0.8.19/introduction-to-smart-contracts.html#storage-memory-and-the-stack) and [here](https://docs.soliditylang.org/en/v0.8.19/types.html#data-location)
   - Your code should look like this:

     ```solidity
     // SPDX-License-Identifier: MIT
     pragma solidity 0.8.19;
     
     contract FrogJump {
         string public name;
     
         constructor(string memory name_) {
             name = name_;
         }
     }
     ```

8. Compile the contract using Remix
9. Deploy to a `Virtual Machine` environment and test the contract
10. Append the contract to add a `jumps` state variable
    - The `jumps` state variable should be an [Unsigned Integer](https://docs.soliditylang.org/en/v0.8.19/types.html#integers) (`uint256`) type and of `public` visibility
11. Append the contract to add a `jump` [function](https://docs.soliditylang.org/en/v0.8.19/structure-of-a-contract.html#functions)
    - To declare a [Function](https://docs.soliditylang.org/en/v0.8.19/contracts.html#functions), even before implementing the actual code, you must set the [Visibility](https://docs.soliditylang.org/en/v0.8.19/contracts.html#visibility-and-getters), [State Mutability](https://docs.soliditylang.org/en/v0.8.19/contracts.html#state-mutability) and [Function Parameters and Return Variables](https://docs.soliditylang.org/en/v0.8.19/contracts.html#function-parameters-return-variables) (if any)
      - You can visualize all this rules and flows at the [Language Grammar](https://docs.soliditylang.org/en/v0.8.19/grammar.html)
12. Implement the `jump` function
    - The `jump` function should increment the `jumps` state variable by one every time it is called
    - Your code should look like this:

     ```solidity
     // SPDX-License-Identifier: MIT
     pragma solidity 0.8.19;
     
     contract FrogJump {
         string public name;
         uint public jumps;
     
         constructor(string memory name_) {
             name = name_;
         }
     
         function jump() public {
             jumps++;
         }
     }
     ```

### Solidity Advanced Concepts

1. Creating an [Interface](https://docs.soliditylang.org/en/v0.8.19/contracts.html#interfaces) for `IFrog` and `IJumper`

   ```solidity
   // SPDX-License-Identifier: MIT
   pragma solidity 0.8.19;
   
   interface IFrog {
       function name() external view returns (string memory);
       function jumps() external view returns (uint256);
   }
   
   interface IJumper {
       function jump() external; 
   }
   
   contract FrogJump is IFrog, IJumper {
       string public name;
       uint256 public jumps;
   
       constructor(string memory _name) {
           name = _name;
       }
   
       function jump() public {
           jumps++;
       }
   }
   ```

2. Create another contract named `PayFrogJump` that inherits from `IFrog` and `IJumper`
3. Create a [Constant](https://docs.soliditylang.org/en/v0.8.19/contracts.html#constant) named `PRICE` of type `uint256` and set it to `1000000000000000000`
   - Alternatively, you can use the `1 ether` [unit](https://docs.soliditylang.org/en/v0.8.19/units-and-global-variables.html#ether-units) to set the value in a more readable way
4. Make the `jump` function [Payable](https://docs.soliditylang.org/en/v0.8.19/contracts.html#payable-functions)
5. Create an `IPayableJumper` interface similar to `IJumper` but sets the `jump` function as `payable`
6. Modify the `jumps` increment to be a function of the amount of Ether sent **to the function**
   - You can use the `msg.value` [transaction property](https://docs.soliditylang.org/en/v0.8.19/units-and-global-variables.html#block-and-transaction-properties) to get the amount of Ether sent
     - The best practice is to use a [Requirement](https://docs.soliditylang.org/en/v0.8.19/control-structures.html#error-handling-assert-require-revert-and-exceptions) (`require`) statement to check if the amount of Ether sent is equal to the `PRICE` constant, or an exact multiple of it
   - Use a division to calculate the number of jumps based on the amount of Ether sent
     - This is not a good practice since the division may result in a remainder, that will be [rounded towards zero](https://docs.soliditylang.org/en/v0.8.19/types.html#division)
     - We are doing this way to visualize the problem in practice

   ```solidity
   interface IPayableJumper {
       function jump() external payable; 
   }
   
   contract PayFrogJump is IFrog, IPayableJumper {
       string public name;
       uint256 public jumps;
       uint256 public constant PRICE = 1 ether;
   
       constructor(string memory _name) {
           name = _name;
       }
   
       function jump() public payable {
           jumps += msg.value / PRICE;
       }
   }
   ```

7. Compile and deploy the `PayFrogJump` contract using Remix
8. Test the contract in a `Virtual Machine` environment by sending some Ether to the `jump` function
   - Remember to choose the right contract in the `Contract` dropdown before deploying
   - Input a number of Ether that is a multiple of the `PRICE` constant in the `Value` field and select `Ether` in the unit dropdown before clicking in the red `jump` button
     - You should notice the `jumps` value increasing by the amount of Ether sent divided by the `PRICE` constant
   - If you send an amount of Ether that is not a multiple of the `PRICE` constant, the division will result in a remainder that will be rounded towards zero
     - For example, if you send `1.5 ether` (`1500000000000000000 wei` ), the division will result in `1`, and the `jumps` value will increase by `1`
     - Another extreme example, if you send `999999999999999999 wei`, the division will result in `0`, and the `jumps` value will not increase, even though you sent almost `1 ether` to the contract

### Deploying on Linea

1. Change the `PRICE` constant to `0.001 ether` or lower in the `PayFrogJump` contract
   - Since we haven't coded an `withdraw` function, we will not be able to get the Ether back from the contract, so it's better to use a lower value for testing and avoid running out of testnet tokens
2. Compile the `PayFrogJump` contract using Remix
3. Deploy the contract to Linea using the `Injected Web3` environment
   - Confirm that you are connected to the `Linea Sepolia` testnet
     - You should see `Custom (59141) network` under the `Environment` dropdown in Remix
   - Make sure you have some testnet tokens in your wallet
   - Confirm the transactions on your wallet when prompted
4. You can view the status of your transaction on the [Linea Sepolia Explorer](https://sepolia.lineascan.build/)
   - Example [PayFrogJump](https://sepolia.lineascan.build/address/0x96D29A1160f2c4BD80118AB17E0636d8D7F65471) named `Crazy Frog`

### Using Tokens

1. Get to know the [Ethereum Improvement Proposals](https://eips.ethereum.org/) and the [Application-level standards and conventions](https://eips.ethereum.org/erc) for Ethereum
2. Check the [ERC-20: Token Standard](https://eips.ethereum.org/EIPS/eip-20)
3. Create a new `ERC20` compliant contract named `FrogToken`
   - Instead of creating a new contract from scratch, we will use the [OpenZeppelin Contracts](https://docs.openzeppelin.com/contracts/5.x/erc20) library to create an ERC20 token
   - Remix has a tool for creating workspaces with contract templates for OpenZeppelin Contracts
   - When creating a new workspace, select the `ERC20` option under the `OpenZeppelin` section, and then leave all options as default
4. Rename the `MyToken.sol` contract to `FrogToken.sol`
5. Change the code of the `FrogToken` contract to set the `name` and `symbol` as `FrogToken` and `FROG`, respectively
6. Implement a `premint` feature in contract to set the _initial supply_
   - You can use the [Contracts Wizard](https://docs.openzeppelin.com/contracts/5.x/wizard) to quickly generate the code for this smart contract

   ```solidity
   // SPDX-License-Identifier: MIT
   pragma solidity ^0.8.19;
   
   import "@openzeppelin/contracts/token/ERC20/ERC20.sol";
   import "@openzeppelin/contracts/token/ERC20/extensions/ERC20Permit.sol";
   
   contract FrogToken is ERC20, ERC20Permit {
       constructor() ERC20("FrogToken", "FROG") ERC20Permit("FrogToken") {
           _mint(msg.sender, 1000 * 10 ** decimals());
       }
   }
   ```

7. Compile the `FrogToken` contract using Remix
8. Deploy the contract to Linea using the `Injected Web3` environment
9. Add the `FrogToken` contract to your wallet
   - You can use the `+ Import Tokens` feature in Metamask to add the `FrogToken` contract to your wallet
   - You will need the `Token Address` to add the token to your wallet
     - You can find the `Token Address` in the `Deployed Contracts` section in Remix, and also in your past transactions on the Linea Sepolia Explorer
10. Interact with the token by sending to other wallets, checking the balance, and approving transactions

## Part 2: Build an E2E Dapp with ScaffoldETH

[![Build an E2E Dapp with ScaffoldETH](https://img.youtube.com/vi/yNo87FGwXJM/0.jpg)](https://www.youtube.com/watch?v=yNo87FGwXJM)

Unlock the potential of dApp development for the Linea Dev Cook-Off with Scaffold ETH!

This tutorial covers everything from blockchain interaction and Linea integration to deploying smart contracts and crafting user interfaces.

What You'll Learn:

- Effective testing with a local blockchain;
- Deploying and debugging contracts easily with Scaffold ETH;
- Creating engaging UIs with React and NextJS;
- Exploring Viem and Wagmi libraries;
- Practical tips for developing user-friendly dApps.

### Prerequisites for ScaffoldETH

1. Install [Git CLI](https://git-scm.com/book/en/v2/Getting-Started-The-Command-Line)

2. Install [Yarn](https://yarnpkg.com/getting-started) and learn [how to use it](https://yarnpkg.com/getting-started/usage)

3. Install [VSCode](https://code.visualstudio.com/docs/setup/setup-overview) and learn [how to use it](https://code.visualstudio.com/docs)

### Setting up our development environment

>Recommendation:
>Before starting, make sure that you have the correct version of Node installed in your system.
>>You can check your current version by running node -v in your terminal.

- Use [Node Version Manager](https://github.com/nvm-sh/nvm) to install and use Node `v20 LTS` version to avoid problems

```bash
# For Linux/MacOS
nvm install --lts
...
nvm use --lts
...
node -v
v20.11.1
```

>Suggestion: use `nvm-windows` from [Corey Butler's community package](https://github.com/coreybutler/nvm-windows) for Windows.

```bash
# For windows
nvm install lts
...
nvm use lts
...
node -v
v20.11.1
```

### Getting Started with ScaffoldETH-2

1. Clone the [ScaffoldETH](https://github.com/scaffold-eth/scaffold-eth-2) repository

   ```bash
   git clone https://github.com/scaffold-eth/scaffold-eth-2.git
   cd scaffold-eth-2
   ```

2. Install the dependencies

   ```bash
   yarn install
   ```

3. Start the local blockchain

   ```bash
   yarn chain
   ```

4. Deploy the contracts

   >Suggestion: since your terminal is busy running the local blockchain, you can open a new terminal tab or window to run the next commands

   ```bash
   yarn deploy
   ```

5. Start the frontend

   ```bash
   yarn start
   ```

   - You should see the frontend running at `http://localhost:3000/`

### Using ScaffoldETH-2 for dApp Development

1. Import your contracts to the ScaffoldETH project

   - Create a new file in the `packages/hardhat/contracts` directory and paste the `FrogJump.sol` contract code from previous lesson in it

2. Create a deployment script for your contract

   - Create a new file named `01_deploy_frog.ts` in the `packages/hardhat/deploy` directory and paste the following code in it

   ```typescript
    const deployFrogJump: DeployFunction = async function (hre: HardhatRuntimeEnvironment) {
     const { deployer } = await hre.getNamedAccounts();
     const { deploy } = hre.deployments;
     await deploy("FrogJump", {
       from: deployer,
       args: ["Froggy"],
       log: true,
       autoMine: true,
     });
   };
   
   export default deployFrogJump;
   ```

3. Change the `version` settings for the `solidity` compiler in the `hardhat.config.ts` to be `0.8.19` (line `24`)

   - You can find this file in the `packages/hardhat` directory

4. Deploy the `FrogJump` contract and interact with it in the frontend using the `debugger` page

### Building a dApp with ScaffoldETH-2

1. Visit [Speedrun Ethereum](https://speedrunethereum.com/)
2. Follow the [Challenge #0: 🎟 Simple NFT Example](https://speedrunethereum.com/challenge/simple-nft-example)
3. Replace the `nftsMetadata.ts` file under `packages/nextjs/utils/simpleNFT` with the [file in this repository](./nftsMetadata.ts)
   - Credits to the [Efrogs](https://linktr.ee/efrogs) maintainers for the NFT Collection and [Element](https://element.market/collections/ethereum-frogs) Market for hosting the images
   - You may want to edit the `NFTCard.tsx` component under `packages/nextjs/components/simpleNFT` folder to display the frog images correctly
     - For example, you can change the `className` of the `NFT Image` to display a squared box by using `className="h-60 w-60"` (read more about this in the [Tailwind docs](https://tailwindcss.com/docs/width))
4. Complete the challenge and deploy your dApp to Linea Sepolia testnet
5. Verify your contract
6. View your collection in [Testnets Opensea](https://testnets.opensea.io/)
7. (Optional) Deploy your dApp to a hosting service like Vercel or similar

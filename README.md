#forge-template

![Github Actions](https://github.com/foundry-rs/forge-template/workflows/CI/badge.svg)

Template repository for getting started quickly with Foundry projects. 

Forked from [Foundry's original repo](https://github.com/foundry-rs/forge-template/) with extra code to save you time.

<!-- ![Foundry Tests](https://github.com/pollum-io/forge-template/workflows/Foundry Tests/badge.svg)

![Slither Lints](https://github.com/pollum-io/forge-template/workflows/Lints/badge.svg) -->

<p align="center">
  <img src="./img/forge-template.png" />
</p>

## Getting Started

Click "Use this template" on [GitHub](https://github.com/pollum-io/forge-template) to create a new repository with this repo as the initial state.

## Writing your first test

All you need is to `import forge-std/Test.sol` and then inherit it from your test contract. Forge-std's Test contract comes with a pre-instatiated [cheatcodes environment](https://book.getfoundry.sh/cheatcodes/), the `vm`. It also has support for [ds-test](https://book.getfoundry.sh/reference/ds-test.html)-style logs and assertions. Finally, it supports Hardhat's [console.log](https://github.com/brockelmore/forge-std/blob/master/src/console.sol). The logging functionalities require `-vvvv`.

```solidity
pragma solidity 0.8.10;

import "forge-std/Test.sol";

contract ContractTest is Test {
    function testExample() public {
        vm.roll(100);
        console.log(1);
        emit log("hi");
        assertTrue(true);
    }
}
```

### Addresses
#### Goerli
- Contract1: https://goerli.etherscan.io/address/
- Contract2: https://goerli.etherscan.io/address/
- Contract3: https://goerli.etherscan.io/address/
#### Mainnet
- Contract1: https://etherscan.io/address/
- Contract2: https://etherscan.io/address/
- Contract3: https://etherscan.io/address/

## Development

This project uses [Foundry](https://getfoundry.sh). See the [book](https://book.getfoundry.sh/getting-started/installation.html) for instructions on how to 
install and use Foundry.

## Deploying

You can either deploy individual contracts or the whole system at once, depending on which script you run.

For individual contracts, run:
```bash
cp .env.example .env
## insert RPC, Etherscan & priv key
source .env
forge script script/DeployContractTestnet.s.sol:Deploy --rpc-url $GOERLI_RPC_URL --broadcast --verify -vvvv
```

To deploy the whole system + setup, run:
```bash
forge script script/DeploySystemTestnet.s.sol:Deploy --rpc-url $GOERLI_RPC_URL --broadcast --verify -vvvv
```

It's recommended to delete your broadcast/ folder when switching back and forth from single and full deployment scripts, as there are instances where Foundry may interprit legacy hardcoded parameters from single script contracts to the complete flow.

### Docs
Auto-generate docs via `forge doc`.
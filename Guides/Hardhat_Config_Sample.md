# Configuring Hardhat for development at Mode

This article delves into configuring Hardhat, a leading Ethereum development framework, specifically tailored for development within the Mode ecosystem. It offers a comprehensive overview of the configuration file, encompassing network setup, Solidity compiler settings, gas usage reporting, Sourcify integration, and Etherscan integration. Each configuration aspect is elaborated upon, providing developers with the necessary insights to optimize their development environment for Mode-specific projects.

```ts
import { HardhatUserConfig } from 'hardhat/config'
import '@nomicfoundation/hardhat-toolbox'
require('hardhat-deploy')
import * as dotenv from 'dotenv'
dotenv.config()

// Load environment variables
const { DEPLOYER_PRIVATE_KEY, ETHERSCAN_API_KEY } = process.env
const providerApiKey = process.env.ALCHEMY_API_KEY

// Configuration object for Hardhat
const config: HardhatUserConfig = {
  networks: {
    // Configuration for local development network
    hardhat: {
      forking: {
        // URL for forking mainnet
        url: `https://eth-mainnet.alchemyapi.io/v2/${providerApiKey}`,
        // Enable forking if MAINNET_FORKING_ENABLED is 'true'
        enabled: process.env.MAINNET_FORKING_ENABLED === 'true',
      },
    },
    // Configuration for ModeTest network
    modetest: {
      // URL for ModeTest network
      url: 'https://sepolia.mode.network',
      // Chain ID for ModeTest network
      chainId: 919,
      // Account(s) to use for deployments on ModeTest network
      accounts: [DEPLOYER_PRIVATE_KEY as string],
      // Gas price for transactions on ModeTest network
      gasPrice: 10000,
    },
    // Configuration for Mode network
    mode: {
      // URL for Mode network
      url: 'https://mainnet.mode.network',
      // Chain ID for Mode network
      chainId: 34443,
      // Account(s) to use for deployments on Mode network
      accounts: [DEPLOYER_PRIVATE_KEY as string],
    },
  },
  // Solidity compiler configuration
  solidity: {
    // Version of Solidity compiler to use
    version: '0.8.20',
    settings: {
      // EVM version
      evmVersion: 'london',
    },
  },
  // Configuration for gas reporting
  gasReporter: {
    // Enable gas reporting if REPORT_GAS is defined
    enabled: process.env.REPORT_GAS !== undefined,
    // Set currency for gas reporting
    currency: 'USD',
  },
  // Configuration for Sourcify
  sourcify: {
    // Enable Sourcify
    enabled: true,
  },
  // Configuration for Etherscan integration
  etherscan: {
    // API key for Etherscan
    apiKey: {
      mode: ETHERSCAN_API_KEY as string,
    },
    // Custom chains configuration for Etherscan
    customChains: [
      // Configuration for ModeTest network in Etherscan
      {
        network: 'modetest',
        chainId: 919,
        urls: {
          // API URL for ModeTest network explorer
          apiURL: 'https://sepolia.explorer.mode.network/api',
          // Browser URL for ModeTest network explorer
          browserURL: 'https://sepolia.explorer.mode.network/',
        },
      },
      // Configuration for Mode network in Etherscan
      {
        network: 'mode',
        chainId: 34443,
        urls: {
          // API URL for Mode network explorer
          apiURL: 'https://explorer.mode.network/api',
          // Browser URL for Mode network explorer
          browserURL: 'https://explorer.mode.network/',
        },
      },
    ],
  },
}

export default config
```

| Property    | Description                                                                       |
| ----------- | --------------------------------------------------------------------------------- |
| networks    | Configuration for different Ethereum networks.                                    |
| - hardhat   | Configuration for local Hardhat network for development and testing.              |
| - modetest  | Configuration for ModeTest network.                                               |
| - mode      | Configuration for Mode network.                                                   |
| solidity    | Configuration for Solidity compiler.                                              |
| gasReporter | Configuration for gas usage reporting during tests.                               |
| sourcify    | Configuration for Sourcify to verify contract source.                             |
| etherscan   | Configuration for Etherscan integration, including API key and custom chain URLs. |

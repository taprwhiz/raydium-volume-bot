# Raydium Volume Bot V3

This upgraded version automates the distribution of SOL across multiple wallets and executes simultaneous buy and sell swap transactions on the Raydium platform. 

## 🔧 Version Improvements

### **Prev Version Limitations**
- **Repetitive Buy and Sell on a Single Wallet**: The prev iteration used fixed wallets, causing repetitive buy and sell actions that were seen on DexScreener.
- **Limited Maker Expansion**: The bot did not increase the number of market makers, only the trading volume.
- **Inefficient Token Gathering**: Tokens were gathered into the main wallet without being sold first, resulting in unnecessary token accumulation.
- **Unbalanced Buy and Sell Actions**: The one-time buy and sell actions led to excess sell pressure, as every buy was matched with a single sell, creating a consistent imbalance.

### **Enhancements**
- **Automated Wallet Rotation**: After completing a set of buy and sell transactions, SOL is transferred to a newly created wallet, ensuring continued activity and minimizing traceability.
- **Dynamic Maker Expansion**: New wallets are automatically created after each transaction cycle, increasing the number of market makers and further distributing trading volume.
- **Token Sell Before Gather**: Before gathering SOL, any remaining tokens are sold to prevent token accumulation in the wallet, ensuring more efficient use of funds.
- **Buy Pressure Optimization**: The bot performs two buys for each sell, maintaining a healthier buy-to-sell ratio and creating more buy pressure.

## 🚀 Features
- **Automated SOL Distribution**: Distributes SOL to new wallets for consistent trading volume across multiple addresses.
- **Simultaneous Buy and Sell Operations**: Performs endless buy and sell swaps to maximize volume and market presence.
- **Jupiter V6 Swap Integration**: Leverages the Jupiter V6 swap aggregator for optimized token swaps.
- **Highly Configurable**: Allows customization of various parameters, such as buy amounts, intervals, distribution settings, and slippage.

## 📋 Environment Variables

The bot requires the following environment variables to function. Copy the `.env.copy` file to `.env` and configure the necessary values:

```env
PRIVATE_KEY=                # Private key for the main wallet
RPC_ENDPOINT=               # RPC endpoint for Solana network
RPC_WEBSOCKET_ENDPOINT=     # RPC WebSocket endpoint for Solana network

####### BUY SETTINGS #######
BUY_UPPER_PERCENT=          # Upper percentage of SOL to use for buys
BUY_LOWER_PERCENT=          # Lower percentage of SOL to use for buys (e.g., 30 means using >30% of SOL)
BUY_INTERVAL_MAX=           # Maximum wait time (in seconds) before second buy
BUY_INTERVAL_MIN=           # Minimum wait time (in seconds) before second buy

####### SELL SETTINGS #######
SELL_INTERVAL_MAX=          # Maximum wait time (in seconds) before selling
SELL_INTERVAL_MIN=          # Minimum wait time (in seconds) before transferring SOL after sell

####### WALLET DISTRIBUTION #######
DISTRIBUTE_WALLET_NUM=      # Number of parallel wallets for volume generation (max: 20)

SLIPPAGE=                   # Maximum slippage allowed (in percentage)

TOKEN_MINT=                 # Token mint address to increase trading volume
```
# Data Notes

## Files
- historical_data.csv: trade-level history from Hyperliquid
- fear_greed_index.csv: daily Bitcoin Fear and Greed index

## historical_data.csv columns
- Account: anonymized account identifier
- Coin: traded asset symbol
- Execution Price: execution price for the trade
- Size Tokens: size in native token units
- Size USD: notional trade size in USD
- Side: buy or sell
- Timestamp IST: timestamp string in IST (as provided)
- Start Position: position size before the trade
- Direction: trade direction or liquidation label
- Closed PnL: realized PnL for the trade (USD)
- Transaction Hash: on-chain transaction hash
- Order ID: order identifier
- Crossed: whether the order crossed the book
- Fee: trade fee (USD)
- Trade ID: trade identifier
- Timestamp: epoch milliseconds

## fear_greed_index.csv columns
- timestamp: epoch seconds
- value: index value (0-100)
- classification: sentiment bucket (Fear/Greed/Extreme)
- date: YYYY-MM-DD

## Preprocessing summary
- Converted trade Timestamp (ms) to datetime and derived date.
- Parsed sentiment date to datetime and merged on date.
- Dropped trades with missing sentiment (gaps after May 2025).
- Engineered Win flag, ROI, hour, day_name, and size_category.

# Report: Bitcoin Sentiment and Trader Behavior

## Problem Statement
Understand how Bitcoin Fear and Greed sentiment aligns with trader behavior and profitability on Hyperliquid.

## Dataset Overview
- Hyperliquid trade history (trade-level, timestamped)
- Fear and Greed index (daily)

## Preprocessing Decisions
- Converted trade timestamps from epoch ms to datetime.
- Merged sentiment on date (daily granularity).
- Dropped rows with missing sentiment labels instead of forward filling.

## Methodology
- Built trade-level features (ROI, Win, hour, day, size category).
- Ran exploratory analysis for PnL skew and sizing patterns.
- Clustered traders using KMeans on average behavior metrics.
- Trained a Random Forest classifier and evaluated with a held-out split.

## Key Insights
- Profitability is strongly skewed; a small share of trades drives most gains.
- Greed regimes show heavier tails in position sizing.
- Sentiment is informative context but not a dominant driver by itself.

## Clustering Analysis
- KMeans was run on standardized trader metrics.
- Elbow plot suggested k=4 as a reasonable trade-off.
- Clusters separate high-frequency accounts from large-size accounts.

## ML Modeling
- Baseline (majority class) accuracy: ~0.58
- Random Forest (no Direction): ~0.82 accuracy
- Precision/recall are balanced around ~0.79

## Leakage Mitigation
- Direction is close to outcome for liquidation-heavy trades.
- Removed Direction from features to avoid leakage.
- Performance dropped to a more realistic range after removal.

## Trading Implications
- Behavior shifts are regime-dependent, especially in size and fee patterns.
- Signals are more behavior-driven than sentiment-driven.

## Limitations
- Sentiment coverage weakens after May 2025.
- No live volatility, funding rates, or order book context.
- Account sample may be biased toward active traders.

## Conclusion
Sentiment is a useful lens for behavior shifts, not a standalone edge. The most stable patterns are in trader sizing and activity under different regimes.

# JoinMarket Fidelity Bond Simulator

## About This Tool
This simulator helps potential JoinMarket makers evaluate their competitive position in the market based on fidelity bonds. In JoinMarket, makers with stronger fidelity bonds are more likely to be selected for coinjoins, potentially earning more fees. For each maker selection, there is a 12.5% chance of random selection and 87.5% chance of selection proportional to bond value. This tool runs multiple simulation trials to give statistically meaningful results with confidence intervals.

This simulator is based on [PulpCattel's jm-scripts JMSim](https://github.com/PulpCattel/jm-scripts#jmsim).

## Data Sources
By default, the orderbook data is fetched from a personal server. This can be easily changed to use a different source by modifying the code. The tool can also be run locally, but due to CORS restrictions, it needs to be served with a local web server (e.g., `python -m http.server` or similar) and the `orderbook.json` path adjusted accordingly.

## Features
- Simulate maker selection probability based on real orderbook data
- Calculate fidelity bond values based on amount and lock time
- Compare different bond strategies
- View statistical confidence intervals for selection probability
- Analyze orderbook data and market competition

## Configuration

| Parameter | Description |
|-----------|-------------|
| Number of makers in coinjoin | The total number of makers that will participate in the coinjoin |
| Bondless allowance | Probability that a maker is selected randomly instead of by bond weight. Default in JoinMarket is 0.125 (12.5%) |
| Absolute fee limit per maker (sats) | Maximum fee in satoshis you're willing to pay per maker |
| Relative fee limit (%) | Maximum fee as a percentage you're willing to pay |
| Coinjoin size (sats) | Size of the coinjoin transaction in satoshis |
| Number of simulation trials | More trials give more accurate results but take longer to calculate |

## Fidelity Bond Calculator
Calculate your fidelity bond value based on amount and lock time:
- Amount to lock (sats)
- Lock time (months)
- Calculated bond value

## Simulation Results
The tool provides detailed results including:
- Total Orderbook Size
- Size-Compatible Offers
- Fee-Compatible Offers
- Offers with Bonds
- Your Selection Probability (with 95% confidence interval)

## How Selection Works in JoinMarket
For each maker selection (repeated for as many makers as needed):
1. There is a 12.5% chance of selecting any maker with equal probability (random selection)
2. There is a 87.5% chance of selecting a maker with probability proportional to their fidelity bond value
3. Once a maker is selected, they are removed from the pool for subsequent selections in the same coinjoin

## Orderbook Analysis
The tool provides detailed orderbook information:
- Filtered Orderbook (Fee and size compatible)
- All Offers
- With Bonds Only
- Without Bonds Only

For each offer, you can see:
- Counterparty
- Min Size
- Max Size
- Fee Type
- Fee
- Fidelity Bond
- Bond Weight
- Estimated Probability

## Bond Value Comparison
Compare how different bond amounts and lock times affect your selection probability by adding different configurations to the comparison chart.

## Simulation Details
- Number of trials
- Coinjoins simulated per trial
- Total coinjoins simulated
- Simulation time

## Getting Started
1. Enter your configuration parameters
2. Calculate your fidelity bond value
3. Run the simulation
4. Analyze the results
5. Compare different bond strategies

## Requirements
- Modern web browser with JavaScript enabled
- Internet connection to fetch orderbook data or a local copy of the orderbook

## Privacy Considerations
This tool runs in your browser and does not send your configuration data to any server.

## License
MIT License

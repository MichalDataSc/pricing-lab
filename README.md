# pricing-lab

Theory and practice of pricing / revenue management data science — built as
a learning project and portfolio, bridging an adtech/RTB-auctions
background into dynamic pricing, revenue management, and price
optimization.

The core idea: setting a price or an odds line under uncertainty, in
response to supply/demand, to capture margin against a counterparty, is the
same decision problem whether it's an RTB bid, a betting line, a
ride-hailing surge multiplier, or an airline fare class. Contextual bandits
for pricing are mechanically the same loop as bid optimization in
real-time-bidding auctions: context → action → observed reward → policy
update.

See [`docs/PLAN.md`](docs/PLAN.md) for the full week-by-week learning plan
(theory reading schedule + hands-on projects, updated as it progresses).

## Structure

```
pricing-lab/
├── docs/PLAN.md               # the learning plan, kept up to date
├── data/                      # datasets (gitignored — see data/README.md)
├── src/
│   ├── elasticity/            # demand/elasticity estimation (log-log, Bayesian)
│   ├── rm_control/            # classic RM control: Littlewood, EMSR-a/b, bid-price
│   ├── causal_pricing/        # diff-in-diff, heterogeneous treatment effects
│   ├── dynamic_pricing/       # bandits (MAB + contextual) for pricing
│   └── capstone/              # forecast -> optimize -> explore -> evaluate pipeline
└── notebooks/                 # exploratory analysis per phase
```

## Datasets used

- Hotel Booking Demand (Antonio, Almeida & Nunes 2019)
- Dominick's / Kilts Center scanner data (Chicago Booth — academic-use terms apply)
- Chicago rideshare trips (City of Chicago open data)

Raw data is not committed — see `data/README.md` in each subfolder for
source links and fetch notes.

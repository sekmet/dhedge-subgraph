# dHEDGE Subgraph - #openDEfiHackathon

## Challenge Description

### Add new data for dHEDGE Pools in the subgraph

At the moment, a Pool's performance (%) on dHEDGE is calculated via our internal backend API. Ideally, this data should be accessible to any developer so the protocol could be adopted in more front-ends/other systems.


#### Git Repository: https://github.com/sekmet/dhedge-subgraph

#### Updated dHEDGE Subgraph: https://thegraph.com/explorer/subgraph/sekmet/dhedge

---

[dHEDGE](https://www.dhedge.org/) is a non-custodial, decentralised asset management and trading protocol on Ethereum, enabling investors to gain exposure to actively-managed and algorithmic investment pools from a Web 3 wallet such as MetaMask. Investors can gain exposure to other pools with a demonstrated history of success, whilst remaining in possession of their assets.

This subgraph dynamically tracks any fund created by the dHEDGE factory. It tracks the current state of dHEDGE Mainnet contracts and contains stats for data such as:

- aggregated data across pool activity
- data on individual pools
- data on assets traded
- data on deposits & exchanges
- data on transfers & withdrawals

## Queries

### List of Pools

```graphql
{
  pools {
    id
    fundAddress
    name
    fundValue
    performance
    performanceFactor
    totalSupply
  }
}
```

### A Pools exchanges, deposits, withdrawals

```graphql
{
  pools(where: { name: "Pool 1" }) {
    id
    fundAddress
    name
    managerName
    manager
    performance
    performanceFactor
    deposits {
      id
      investor
      valueDeposited
      fundTokensReceived
      time
    }
    exchanges {
      id
      sourceKey
      sourceAmount
      destinationKey
      destinationAmount
      time
    }
    withdrawals {
      id
      investor
      valueWithdrawn
      fundTokensWithdrawn
      time
    }
  }
}
```

### Rates

```graphql
{
  rateUpdates(orderBy: block, orderDirection: desc, where: { synth: "sETH" }) {
    block
    synth
    rate
  }
}
```

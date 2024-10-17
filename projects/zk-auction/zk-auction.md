# ZK-Powered Auction by [zkzoomer](https://x.com/zkzoomer)

**Summary:** This project presents a proof of concept to infinitely scale onchain auctions by use of a ZK-powered architecture.

**Team Members:** Sergio [[zkzoomer.io](https://zkzoomer.io)] [[GitHub](https://github.com/zkzoomer)] [[Twitter](https://x.com/zkzoomer)]

**Repo Link:** [github.com/zkzoomer/zkauction](https://github.com/zkzoomer/zkauction)

**Additional Resources:** Find the initial improvement proposal this work is based on [here](https://hackmd.io/@zkzoomer/B1bk2pWAA).

---
## Problem

To say that [fixed-income markets](https://www.investopedia.com/fixed-income-essentials-4689775) are the backbone of the modern economy is not an understatement. Fixed-income products enable institutions and individuals to predict future cash flows and make investments according to their risk appetite. However, such products are currently absent in DeFi, effectively preventing the development of more advanced financial products like forwards, futures, and options.

While Binance recently started offering [Fixed Rate Loans](https://www.binance.com/en/fixedLoan), this centralized approach takes away from the ethos of the ecosystem. Ideally, we should be able to plot Bitcoin's [yield curve](https://www.investopedia.com/terms/y/yieldcurve.asp) by use of decentralized and permissionless smart contracts. But such implementation quickly runs into a scalability problem: executing the logic for an auction is not cheap, and having to do so for *every order that was placed* inevitably grows past the block gas limit.

The motivation behind this work was to implement a **ZK-based, fixed gas-cost model to clear and settle auctions** to i) effectively remove the block gas limit constraint, and ii) increase protocol revenue and lower fees.

## Solution

This proof of concept enables non-custodial, fixed-rate and fixed-term overcollateralized lending onchain. Borrowers submit sealed bids and lenders submit sealed offers that are used to determine an interest rate that clears the market for participants of that auction. Participants who bid more than the clearing rate receive loans and participants willing to lend below the clearing rate make loans, in each case at the market-clearing rate. All other participants see their locked funds returned. Matched borrowers receive loan proceeds and matched lenders receive "bond tokens" that can be redeemed for the principal plus interest at maturity.

By moving most computation offchain, we are able to infinitely scale any auction mechanism: a single proof can be used to settle an arbitrary size auction with a fixed gas cost. Moreover, since orders do not have to be settled onchain, it follows they do not need to be stored onchain either: this further reduces the gas cost associated with placing and revealing orders. Each time an order is placed, we update a [hash chain](https://en.wikipedia.org/wiki/Hash_chain) that commits to the entire order placing history in a single value.

The general outline of the auction proof is as follows:
1. All placed bids/offers are loaded.
2. All revealed prices for placed bids/offers are loaded.
3. The onchain hash chain value is reconstructed.
4. A clearing price that clears the market is computed.
5. Bids and offers are either fully assigned, partially assigned, or left on the table and unlocked.
6. A single cryptographic commitment is computed, encoding the the entire auction results into the root of a [lean incremental Merkle tree](https://zkkit.pse.dev/classes/_zk_kit_lean_imt.LeanIMT.html).

## Performance Metrics

#### Cycle Count

As the auction size and volume can vary greatly, so does the cycle count for verifying it. Here is a very rough estimate:

| **Total Orders** | **Cycle Count** |
|:----------------:|:---------------:|
|        0         | ~20,000 |
|       10         | ~170,000 |
|       100        | ~1,700,000 |
|      1,000       | ~17,500,000 |

This just serves to size the order of magnitude of verifying a given auction, as the actual number of cycles can vary greatly. This is even the case with a fixed number of orders, as these can get either fully filled, partially filled, or be left on the table: each of these outcomes resulting in different cycle counts.

#### Time Constraints

Bids need to be validated by checking that their purchase amount is overcollateralized, else the protocol can incur in bad debt. To this end, we rely on onchain oracles as our price feed, meaning **the current onchain oracle price must be an input to the proof**. This can lead to liveness issues, or even censorship attacks, if the oracle updates **faster than we can generate proofs**. A quick look at Chainlink's [Data Feeds](https://data.chain.link/feeds) shows that price updates are not overly consistent, meaning our proving time should ideally be in the *minutes*.

Since this application does not need frequent proving, maintaining a server to generate these proofs is not ideal. It would therefore rely on third parties like [Succinct's prover network](https://docs.succinct.xyz/generating-proofs/prover-network.html) to generate them. Although proving time on the prover network varies greatly, all tests made have resulted in times **faster than 5 minutes**, which should be acceptable for this use case.

#### Gas Savings

We can clearly see the significant gas cost reductions from this ZK-powered architecture:

| **Action** | **Fully Onchain Cost** | **ZK-Powered Cost** | **Cost Reduction** |
|:----------------:|:---------------:|:----------------:|:---------------:|
| `lockBid` | 460,000 | 45,000 | **10x** |
| `lockOffer` | 260,000 | 45,000 | 5x |
| `revealBid` | 77,000 | 27,000 | 3x |
| `revealOffer` | 77,000 | 27,000 | 3x |
| `settleAuction` | >1,250,000 | ~450,000 | **3-infinite**x

There are two key takeaways from this gas cost breakdown:
1. The gas costs to place and reveal orders are *directly incurred* by users. It is easy to see how this ZK-powered architecture would make interacting with the protocol more attractive to users, just by virtue of lowering their transaction fees.
2. The gas cost for settling the auction is incurred by "the protocol", and so it must be amortized by the accrued fees. Lowering this cost, as well as making it predictable by fixing it, can help reduce overall protocol fees.

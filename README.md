
Plasma staking pool is intended to be a rudimentary version of a casino ecosystem based on OMG's Plasma MVP (https://github.com/omisego/plasma-mvp) and Vitalik Buterin's Eth Research of the same name (https://ethresear.ch/t/minimal-viable-plasma/426).

  

The Plasma channel, and thus the ecosystem will derive from two user stories, as below;

  

## User Stories

**Bettor**

The bettor is a gambler, and intends to take on the staking pool in a simple dice game in an attempt to earn profits.

The bettor does not want to pay gas per-roll, as per some incumbent systems as https://etheroll.com/. The bettor would prefer to deposit into a Plasma sidechain, and then bet continuously with near-instant latency.

The bettor desires the ability to withdraw their profits to the main chain at any time, with the only delay being a pre-determined challenge period whereby others in the chain can oppose a bad actor. This challenge period is still likely to be considerably less than the withdrawal period on incumbent traditional casinos.

  

**Staker**

The staker intends to earn profit based on the dice game's 'edge' (http://www.ukcasinotablegames.info/houseedge.html). Whilst over a short period of time & gameplay there is a possibility that the staking pool in it's totality could lose, over an extended period of time the house edge and simple probability guarantee +EV to the pool.

The staker desires the ability to withdraw 'locked' funds (along with any potential profit) to the main chain at any point in time, with the same limits as the bettor as in the pre-determined challenge period.

  

## Return on stake

Any losses or profits are split exactly and evenly between those who have deposited their tokens to stake. If the 'casino' wins 100 tokens in profit, and has 10 stakers in the sidechain, then each staker has earnt ten extra tokens and a 10% total ROI.

  

## Considerations and Limitations

- Due to the simple nature of the dice game, the 'max win' that a bettor may achieve is limited. With other popular casino games, such as slots, the max win (jackpot) can be proportionally many exponents higher than the initial bet, and thus the contract must check that the staking pool is able to pay out the max win BEFORE accepting a bet. If not the bet MUST be limited.

  

- As per human nature, both the Staker & Bettor have reason to be less than honest about their wins or seek attack vectors within the sidechain. On the main chain this is less of a concern due to the more decentralised nature and the greater number of full nodes - Sybil attacks and 51% attacks become increasingly more difficult as a result.
Therefore, introducing an oracle (or a set of oracles) to generate randomness - although this may come with it's own concerns & considerations such as the oracle itself being compromised - is a potential way to mitigate this.
Another way to mitigate this would be to remove the Staker & Bettor from the RNG completely, and allow for a cryptoeconomic implementation using third-party validators.
This would involve a third user story, a validator node. The validator node(s) would provide the RNG and be paid a fixed percentage regardless of final result. So regardless of a bettor ROI or a staker(s) ROI per round, the validator nodes would be paid as a result of their service to the sidechain. The validator node has no economic incentive to cheat either side, merely to provide a service and be paid consistent returns.
To further secure this sidechain, we would allow any staker or bettor to challenge a result, which would pass verification of the result back to the main chain for finality.
A further consideration would be to not allow any betting to occur on the sidechain until enough validator nodes were active to ensure Byzantine Fault Tolerance. So to tolerate *n* malicious nodes, you therefore need a minimum of (3n + 1) benevolent nodes to ensure BFT.

## Progress

 - [x] Implement Plasma MVP
 - [ ] Plasma Rootchain and Childchain running 
 - [ ] Create local dev server (lite-server or similar)
 - [ ] Truffle & Ganache working with child chain
 - [ ] Ensure deposits reflect on child chain
 - [ ] Create Dice Game contract w/ testing
 - [ ] Implement deposit functionality into staking pool (% ownership based on entire pool) w/ testing
 - [ ] Test withdrawals for both bettor and stakers
## **Punk.Network 抵押的运作方式**
### **Staking**

Punk.Network使用 NPoS(提名权益证明)机制选择验证人，该机制拥有验证人和提名人两种角色，以实现链安全性的最大化。对网络维护感兴趣的参与者可以负责运行验证人节点。在创世区块中，Punk.Network将为验证人提供21个节点，节点数量将逐步增加至 1000 以上。
系统鼓励 PUNK 持有者作为提名人参与。
验证人角色是在 BABE 负责生成区块，验证平行链区块和确保最终性。提名人可以根据验证人抵押量而作选择。
Punk.Network uses NPoS (Nominated Proof-of-Stake) as its mechanism for selecting the validator set. It is designed with the roles of validators and nominators, to maximize chain security. Actors who are interested in maintaining the network can run a validator node. At genesis, Punk.Network will have a limited amount of slots available for these validators, but this number will grow over time to over one thousand.
The system encourages DOT holders to participate as nominators.
Validators assume the role of producing new blocks in BABE, validating parachain blocks, and guaranteeing finality. Nominators can choose to back select validators with their stake.
The staking system pays out rewards equally to all validators regardless of stake. In other words, having more stake on a validator does not influence the block rewards they receive. However, there is a probabilistic component to reward calculation (discussed below), so rewards may not be exactly equal for all validators in a given era.

### **1.确定身份 Identification**
In staking, you can be either a nominator or a validator.
As a nominator, you can nominate one or more validator candidates that you trust to help you earn rewards in PUNK. You can take a look at the nominator guide to understand what you are required to do when the mainnet launches.

### **2.提名期  Nomination Period**

Any potential validators can indicate their intention to be a validator candidate. Their candidacies are made public to all nominators, and a nominator in turn submits a list of any number of candidates that it supports. In the next epoch (lasting several hours), a certain number of validators having the most PUNK backing get elected and become active. There are no particular requirements for a PUNK holder to become a nominator, though we expect each nominator to carefully track the performance and reputation of validators.
Once the nomination period ends, the NPoS election mechanism takes the nominators and their associated votes as input, and outputs a set of validators of the required size, that maximizes the stake backing of any validator, and that makes the stakes backing validators as evenly distributed as possible. The objectives of this election mechanism are to maximize the security of the network, and achieve fair representation of the nominators. If you want to know more about how NPoS works (e.g. election, running time complexity, etc.), please read [here](https://w3f-research.readthedocs.io/en/latest/polkadot/NPoS/index.html).


### **3. 抵押奖励分配 Staking Rewards Distriburion**
To explain how rewards are paid to validators and nominators, we need to consider validator pools, where a validator pool consists of an elected validator together with the nominators backing it. (Note: if a nominator n with stake s backs several elected validators, say k, the NPoS election mechanism will split its stakes into pieces s_1, s_2, …, s_k, so that it backs validator i with stake s_i. In that case, nominator n will be rewarded the same as if there were k nominators in different pools, each backing a single validator i with stake s_i). For each validator pool, we keep a list of nominators with the associated stakes.
The general rule for rewards across validator pools is that two validator pools get paid the same amount of PUNK for equal work, i.e. they are NOT paid proportional to the stakes in each pool. Within a validator pool, a (configurable) part of the reward goes to pay the validator's commission fees and the remainder is paid pro-rata (i.e. proportional to stake) to the nominators and validator. Notice in particular that the validator is rewarded twice: once as commission fees for validating, and once for nominating itself with stake.
To estimate the inflation rate and how many PUNK you can get each month as a nominator or validator, you can use this [tool](https://www.stakingrewards.com/calculator/polkadot) as a reference and play around with it ....by changing some parameters (e.g. how many days you would like to stake with your PUNK, provider fees, compound rewards, etc.) to have a better estimate. Even though it may not be entirely accurate since staking participation is changing dynamically, it works well as an indicator.

### **4. 奖励机制 Reward Mechanism**
We highlight two features of this payment scheme. The first is that since validator pools are paid the same regardless of stake level, pools with less stake will generally pay more to nominators per-PUNK than pools with more stake. We thus give nominators an economic incentive to gradually shift their preferences to lower staked validators that gain a sufficient amount of reputation. The reason for this is that we want the stake across validator pools to be as evenly distributed as possible, to avoid a concentration of power among a few validators. In the long term, we expect all validator pools to have similar levels of stake, with the stake being higher for higher reputation validators (meaning that a nominator that is willing to risk more by backing a validator with a low reputation will get paid more).
The following example should clarify the above. For simplicity, we have the following assumptions:
- These validators do not have a stake of their own.
- They do NOT charge any commission fees.
- Reward amount is 100 PUNK tokens.
- The current minimum amount of PUNK to be a validator is 350.
||A - Validator Pool|||
|:--:|:--:|:--:|:--:|
|Nominator (4)|Stake (600)|Fraction of the Total Stake|Rewards|
|Jin|100|0.167|16.7|
|Sam|50|0.083|8.3|
|Anson|250|0.417|41.7|
|Bobby|200|0.333|33.3|
<br>
||B - Validator Pool|||
|:--:|:--:|:--:|:--:|
|Nominator (4)|Stake (400)|Fraction of the Total Stake|Rewards|
|Alice	|100	|0.25|	25|
|Peter|	100|	0.25|	25|
|John|	150|	0.375|	37.5|
|Kitty|	50|	0.125|	12.5|


Both validator pools A & B have 4 nominators with the total stake 600 and 400 respectively.
Based on the above rewards distribution, nominators in validator pool B get more rewards per PUNK than those in pool A because pool A has more overall stake. Sam has staked 50 PUNK in pool A, but he only gets 8.3 in return, whereas Kitty gets 12.5 with the same amount of stake.
We also remark that when the network slashes a validator slot for a misbehavior (e.g. validator offline, equivocation, etc.) the slashed amount is a fixed percentage (and NOT a fixed amount of PUNK), which means that validator pools with more stake get slashed more PUNK. Again, this is done to provide nominators with an economic incentive to shift their preferences and back less popular validators whom they consider to be trustworthy.
The second point to note is that each validator candidate is free to name their desired commission fee (as a percentage of rewards) to cover operational costs. Since validator pools are paid the same, pools with lower commission fees pay more to nominators than pools with higher fees. Thus, each validator can choose between increasing their fees to earn more PUNK, or decreasing their fees to attract more nominators and increase their chances of being elected. We will let the market regulate itself in this regard. In the long term, we expect that all validators will need to be cost efficient to remain competitive, and that validators with higher reputation will be able to charge slightly higher commission fees (which is fair).
### **账户 Account**
There are two different accounts for managing your funds: Stash and Controller.
![image1.png](1)

- Stash: 
This account holds funds bonded for staking, but delegates some functions to a Controller. As a result, you may actively participate with a Stash key kept in a cold wallet, meaning it stays offline all the time. You can also designate a Proxy account to vote in governance proposals.

- Controller 
This account acts on behalf of the Stash account, signalling decisions about nominating and validating. It set preferences like payout account and commission. If you are a validator, it also sets your session keys. It only needs enough funds to pay transaction fees.

We designed this hierarchy of separate key types so that validator operators and nominators can protect themselves much better than in systems with only one key. As a rule, you lose security anytime you use one key for multiple roles, or even if you use keys related by derivation. You should never use any account key for a "hot" session key in particular.
Controller and Stash account keys can be either sr25519 or ed25519. 


## **验证人和提名人Validators and nominators**
Since validator slots will be limited, most of those who wish to stake their PUNK and contribute economic security to the network will be nominators. Validators do most of the heavy lifting: they produce new block candidates in BABE, vote and come to consensus in GRANDPA, validate the state transition function of parachains, and possibly some other responsibilities regarding data availability and [XCMP](https://w3f-research.readthedocs.io/en/latest/polkadot/XCMP.html) . Nominators, on the other hand, do not need to do anything once they have bonded their PUNK. The experience of the nominator is similar to "set it and forget it," while the validator will be doing active service for the network by performing the critical operations. For this reason, the validator has certain privileges regarding the payout of the staking mechanism and will be able to declare its own allocation before the share is divided to nominators.
![image2.png](2)
Note: while the experience of a nominator is similar to "set it and forget it", in reality there are many reasons to keep an eye on one's validators and keep optimizing the nominations for best returns and reduced risk. We talk more about this on the How to Nominate page.
### **Want to stake PUNK?**
- Nominator Guide（跳转链接：”如何成为提名人”页） - Become a nominator on Punk.Network.
- Validator Guide （跳转链接：”如何成为验证人“页）- Become a validator on Punk.Network.


### **惩罚 Slashing**
Slashing will happen if a validator misbehaves (e.g. goes offline, attacks the network, or runs modified software) in the network. They and their nominators will get slashed by losing a percentage of their bonded/staked PUNK. Any slashed PUNK will be added to the Treasury. The rationale for this (rather than burning or distributing them as rewards) is that slashes may then be reverted by the Council by simply paying out from the Treasury. This would be useful in situations such as a faulty runtime causing slashing or forcing validators offline through no fault of their own. In the case of legitimate slashing, it moves tokens away from malicious validators to those building the ecosystem through the normal Treasury process.
Validator pools with larger total stake backing them will get slashed more harshly than less popular ones, so we encourage nominators to shift their nominations to less popular validators to reduce the possible losses.
Once a validator gets slashed, it goes into the state as an "unapplied slash".  While unapplied, a governance proposal can be made to reverse it during this period (7 days on RocknRoll, 28 days on Punk.Network). After the grace period, the slashes are applied.
The following levels of offence are [defined](https://research.web3.foundation/en/latest/polkadot/slashing/amounts.html) (for specific slash amounts, see the equations in the section below):
- Level 1: isolated unresponsiveness, i.e. being offline for an entire epoch. No slashing, only chilling.
- Level 2: concurrent unresponsiveness or isolated equivocation. Slashes a very small amount of the stake and chills.
- Level 3: misconducts unlikely to be accidental, but which do not harm the network's security to any large extent. Examples include concurrent equivocation or isolated cases of unjustified voting in GRANDPA. Slashes a moderately small amount of the stake and chills.
- Level 4: misconduct that poses a serious security or monetary risk to the system, or mass collusion. Slashes all or most of the stake behind the validator and chills.

Let's look at these offences in a bit more detail.
### **Unresponsiveness**
For every session, validators will send an "I'm Online" heartbeat to indicate they are online. If a validator produces no blocks during an epoch and fails to send the heartbeat, it will be reported as unresponsive. Depending on the repeated offences and how many other validators were unresponsive or offline during the epoch, slashing may occur.
Here is the formula for calculation:
```language
Let x = offenders, n = total no. validators
min((3 * (x - (n / 10 + 1))) / n, 1) * 0.07
```


Note that if less than 10% of all validators are offline, no penalty is enacted.
Validators should have a well-architected network infrastructure to ensure the node is running to reduce the risk of being slashed. A high availability setup is desirable, preferably with backup nodes that kick in **only once the original node is verifiably offline** (to avoid double-signing and being slashed for equivocation - see below), together with [proxy nodes](https://wiki.aochain.io/zh_CN/Staking/maintain-guides-how-to-setup-sentry-node) to avoid being DDoSed when your validator node's IP address is exposed. A comprehensive guide on secure validator setup is available [here](https://wiki.polkadot.network/docs/en/maintain-guides-secure-validator).
### **GRANDPA Equivocation**
A validator signs two or more votes in the same round on different chains.
### **BABE Equivocation**
A validator produces two or more blocks on the Relay Chain in the same time slot.
GRANDPA and BABE equivocation slashing penalty is calculated as below:
```language
Let x = offenders, n = total no. validators
Min( (3 * x / n )^2, 1)
```


Validators may run their nodes on multiple machines to make sure they can still perform validation work in case one of their nodes goes down. It should be noted that if they do not have good coordination to manage signing machines, then equivocation is possible.
If a validator is reported for any one of the offences they will be removed from the validator set ([chilled](https://wiki.aochain.io/zh_CN/Staking/#chilling)) and they will not be paid while they are out. They will be considered inactive immediately and will lose their nominators. They need to re-issue intent to validate and gather support from nominators.
If you want to know more details about slashing, please look at our [research page](https://research.web3.foundation/en/latest/polkadot/slashing/amounts.html).
### **Chilling**
Chilling is the act of removing a validator from the active validator set, also disqualifying them from the set of electable candidates in the next NPoS cycle.
This may be voluntary and validator-initiated, e.g. if there is a planned outage in the validator's surroundings or hosting provider, and the validator wants to exit to protect themselves against slashing. When voluntary, chilling will keep the validator active in the current session, but will move them to the inactive set in the next. The validator will not lose their nominators.
When used as part of a punishment, being chilled carries an implied penalty of being un-nominated. It also disables the validator for the remainder of the current era and removes the offending validator from the next election.
Punk.Network allows some validators to be disabled, but if the number of disabled validators gets too large, Punk.Network will trigger a new validator election to get a full set. Disabled validators will need to resubmit their intention to validate and regarner support from nominators.
### **Slashing Across Eras**
There are 3 main difficulties to account for with slashing in NPoS:
- A nominator can nominate multiple validators and be slashed via any of them.
- Until slashed, stake is reused from era to era. Nominating with N coins for E eras in a row does not mean you have N*E coins to be slashed - you've only ever had N.
- Slashable offences can be found after the fact and out of order.

To balance this, we only slash for the maximum slash a participant can receive in some time period, rather than the sum. This ensures protection from overslashing. Likewise, the time span over which maximum slashes are computed are finite and the validator is chilled with nominations withdrawn after a slashing event, as stated in the previous section. This prevents rage-quit attacks in which, once caught misbehaving, a participant deliberately misbehaves more because their slashing amount is already maxed out.
### **奖励分配Reward Distribution**
Note that RocknRoll runs approximately 4x as fast as Punk.Network, except for block production times. Punk.Network will also produce blocks at approximately six second intervals.
Rewards are recorded per session (approximately one hour on RocknRoll and four hours on Punk.Network) and calculated per era (approximately six hours on RocknRoll and twenty-four hours on Punk.Network). Thus, rewards will be calculated four times per day on RocknRoll and once per day on Punk.Network.
Rewards are calculated based on era points, which have a probabilistic component. In other words, there may be slight differences in your rewards from era to era, and even amongst validators in the active set at the same time. These variations should cancel out over a long enough timeline..
In order to be paid your staking rewards, someone must claim them for each validator that you nominate. Staking rewards are kept available for 84 eras, which is approximately 84 days on Punk.Network and 21 days on RocknRoll. 

**WARNING: ** If nobody claims your staking rewards by this time, then you will not be able to claim them and some of your staking rewards will be lost.
### **领取奖励 Get Rewords**
If you go to the Staking payouts page on PUNK-JS, you will see a list of all validators that you have nominated in the past 84 eras and for which you have not yet received a payout. Each one has the option to trigger the payout for all unclaimed eras. Note that this will pay everyone who was nominating that validator during those eras, and anyone can call it. Therefore, you may not see anything in this tab, yet still received a payout if somebody (generally, but not necessarily, another nominator or the validator operator) has triggered the payout for that validator for that era.
If you wish to check if you received a payout, you will have to check via a block explorer. 
### **奖励分配例子 Example**
```language
    PER_ERA * BLOCK_TIME = **Reward Distribution Time**
    3600 * 6 seconds = 21,600 s = 6 hours
    ***These parameters can be changed by proposing a referendum***
```


Validators can create a cut of the reward that is not shared with the nominators. This cut is a percentage of the block reward, not an absolute value. After the value gets deducted, the remaining portion is based on their staked value and split between the validator and all of the nominators who have voted for this validator.
For example, assume the block reward for a validator is 10 PUNK. A validator may specify validator_payment = 50%, in which case the validator would receive 5 PUNK. The remaining 5 PUNK would then be split between the validator and their nominators based on the proportion of stake each nominator had. Note that validators can put up their own stake, and for this calculation, their stake acts just as if they were another nominator.
Rewards can be directed to the same account (controller), to the stash account (and either increasing the staked value or not increasing the staked value), or to a completely custom account. It is also possible to top-up / withdraw some bonded PUNK without having to un-stake everything.
### **通胀率 Function of Inflation **
PUNK is inflationary; there is no maximum number of PUNK as in Bitcoin. Inflation is designed to be 10% in the first year, with validator rewards being a function of amount staked and the remainder going to treasury.
![image3.png](3)

Source: [esearch - Web3 Foundation](https://research.web3.foundation/en/latest/polkadot/Token Economics.html)

- x-axis: Proportion of PUNK staked
- y-axis: Annually Inflation rate通货膨胀, 年度化百分比
- 蓝线: Inflation rewards to stakers参与抵押者的通涨奖励
- 绿线: Staker rate of return抵押参与者的收益率

For those who are interested in knowing more about the design of inflation model for the network, please see [here]（https://research.web3.foundation/en/latest/polkadot/Token Economics.html）.
### **为什么参与抵押?**
10% inflation/year when the network launches
50% targeted active staking
~20% annual return
### **Why not stake?**
Tokens will be locked for about 28 days on Punk.Network after unbonding, seven days on Rock n Roll.
Punishment in case of validator found to be misbehaving (see #slashing).
You want to use the tokens for a parachain slot.

### **How many validators does Punk.Network have?**
Punk.Network started with 21 open validator positions and has opened more gradually. The top bound on the number of validators has not been determined yet, but should only be limited by the bandwidth strain of the network due to peer-to-peer message passing. The estimate of the number of validators that Punk.Network will have at maturity is around 1000. ROCK N' ROLL, Punk's canary network, currently has over 500 validator slots, and the plan is also to slowly grow this number to approximately 1000.
### **Resources**
- [How Nominated Proof of Stake will work in Polkadot](https://medium.com/web3foundation/how-nominated-proof-of-stake-will-work-in-polkadot-377d70c6bd43) - Blog post by Web3 Foundation researcher Alfonso Cevallos covering NPoS in Polkadot.
- [Secure validator setup](https://wiki.polkadot.network/docs/en/maintain-guides-secure-validator)

---
# 网络术语整理
---
## **Active Nomination 活跃提名**
在当前 era 中，提名人正在活跃地验证的一个或多个验证人。提名人将自己的 stake 放在这个 era 的验证人的手中，并有可能因此获得利益的回报。
## **Alexander 亚历山大**
Polkadot 的第四个（现已失效）概念验证（PoC-4) 测试网。
## **Attestation 证明**
在 Polkadot 验证系统中，attestation是验证人广播的一种消息，表明他们认为平行链候选区块有效还是无效。
## **Authority**
Authority 是能够参与共识机制的区块链中角色的通用术语。在 GRANDPA 中，authority 要对他们认为是最终确认的链进行投票。在 BABE 中，authority 是出块者。Authority sets 可以通过像 Polkadot 的 NPoS 算法之类的机制来选出。
## **BABE**
全称 Blind Assignment of Block Extension，它是 Polkadot 的出块机制。
## **Block 区块**
诸如交易之类的数据集，共同表明了区块链的状态转换。
Block explorer 区块浏览器
一个允许用户浏览区块链上不同区块的应用程序。
## BLS
Boneh-Lynn-Shacham（BLS）签名的签名速度慢，验证速度则极其慢，需要缓慢且安全性低得多的配对友好曲线，并且往往具有危险的延展性。但是，BLS 允许多种多样的签名聚合选项阵列，远远超过任何其他已知的签名方案，这使 BLS 成为共识算法中投票和阈值签名的首选方案。
## **Bonding 绑定**
可以 “冻结” 代币以换取其他收益的过程。例如，staking 是一种绑定形式，你可以为网络提供安全性以换取报酬。你也可以绑定代币来换取平行链插槽。
## **Bridge 转接桥**
充当 Polkadot 中继链和外部链之间的中介的平行链，让中继链觉得该外部链是一条平行链（即满足 Polkadot 宿主对平行链的要求）。转接桥能让中继链与其他本身不兼容波卡的区块链之间进行交互，例如以太坊和比特币。
## **Byzantine Fault Tolerance 拜占庭容错**
可以承受拜占庭式故障的系统的属性。也就是说，一个系统不仅单个子系统可能会发生故障，而且可能连特定子系统是否发生故障也不清楚。也就是说，系统上的不同观察者可能不会就系统是否发生故障达成共识。确保拜占庭容错能力是开发任何分布式系统的重要组成部分。
## **Collator 收集人**
通过收集平行链交易并为验证人生成状态转换证明来维护平行链的节点。
## **Consensus 共识**
一组实体就特定数据值达成一致的过程（例如对区块链上区块的排序和组成）。有多种用于确定共识的算法。Polkadot 使用的共识算法是 GRANDPA。
## **Dapps 去中心化应用**
去中心化应用程序的通用术语，即作为分布式网络的一部分而不是在特定系统或一组系统上运行的应用程序。
## **DOT**
Polkadot 的本地代币。DOT 具有以下三个目的：网络治理（允许 DOT 对网络升级和其他特殊事件进行投票）、常规运行（奖励好行为者和惩罚坏行为者）以及绑定（通过在连接中继器时“冻结” DOT 来添加新的平行链）。
## **Duty Roster 值勤表**
一种查找表，该表指定了特定验证人需要执行的工作（即证明特定平行链的有效性）。值勤表通常将验证人集合按每个平行链随机分成不同的子集。
## **Epoch**
一个 Epoch 是 BABE 协议中的持续时间，分为几个较小的时隙。每个时隙都有至少一个有权提出封禁的时隙负责人。在 Kusama 中，它的持续时间与一个 session 相同。
## **Era**
等于一定数量的 Session（整数个），即重新计算验证人集（以及每个验证人的活跃提名人集）并支付奖励的时间段。
## **Equivocation 重复签名**
向网络提供冲突的信息。BABE 的重复签名包括在同一插槽中创建多个区块。GRANDPA 的重复签名包括签署多个冲突链。
## **Extrinsic 外部信息**
来自外部世界的状态更改，即它们不是系统本身的一部分。Extrinsics可以采取两种形式，即 “inherents[1]” 和 “transactions[2]”。
## **Finality 终结**
区块的不可逆性。通常，创建的区块要到将来某个时候才能终结，而在 “概率最终性” 的情况下可能永远不会终结。Polkadot 中继链使用称为 GRANDPA 的确定性终结工具。
## **Finality Gadget终结工具**
确定终结性的机制。
## **Fisherman 钓鱼人**
监视网络的节点，以揪出行为不当的验证人或收集人。钓鱼人必须投入少量的 DOT，但是如果发现不良行为，则可以得到巨大的回报。
## **FRAME**
Substrate 提供的 pallet 的集合（Substrate Runtime Modules）。
## **Genesis 创世区块/创世期**
区块链的起源，也称为区块 0。它也可以用于表示区块链在初始时的初始状态。
“ 示例：“在创世期，张三、李四和王五分别拥有 30 个代币。”
## **Governance 治理**
确定哪些对网络的更改应该通过的过程，例如对代码的更改或资金的流动。Polkadot 的治理系统是链上的，并且基于利益相关者的投票。
## **Governance Council 治理理事会**
一个由多个链上帐户组成的链上实体（最初是 6 个席位，最终增加到 24 个席位)。理事会可以充当 “被动”（未投票）利益相关者的代表。理事会成员有两项主要任务：为全体利益相关者团体投票进行全民公投，并取消恶意的全民公投。
## **GRANDPA Finality Gadget - GRANDPA 终结工具**
即 GHOST-based Recursive ANcestor Deriving Prefix Agreement。这是 Polkadot 的终结工具，它允许对区块链进行异步、负责和安全的终结。有关 GRANDPA 的概述，请参见以下 Medium 文章：<a href="https://medium.com/polkadot-network/polkadot-proof-of-concept-3-a-better-consensus-algorithm-e81c380a2372" >https://medium.com/polkadot-network/polkadot-proof-of-concept-3-a-better-consensus-algorithm-e81c380a2372</a>[3]。
## **Hard Fork 硬分叉**
区块链的永久性分流，可以通过共识规则中的高优先级更改快速发生。遵循硬分叉的客户端始终需要升级其客户端，才能继续遵循已升级的链。硬分叉被认为是链的永久性分歧，未升级的客户端所遵循的共识规则与升级的客户端所遵循的共识规则不兼容。
## **Hard Spoon 硬汤匙**
Cosmos 的 Jae Kwon 将其定义为 “一条新链，它考虑了现有链的状态；其目的不是为了竞争，而是为了提供广泛的机会”。它是一条无争议的区块链，继承基础区块链的状态并创建同一区块链的新分支。
## **Horizontal Relay-routed Message Passing 水平中继路由消息传递**
水平中继路由消息传递，也称为 HRMP，是完整 XCMP 实现的先驱，它模仿 XCMP 的相同接口和语义。它与 XCMP 相似，不同之处在于它将所有消息存储在中继链存储中的方式，因此，与 XCMP 相比，它更昂贵且需要更多资源。波卡的计划是一旦 XCMP 实施完成，就淘汰 HRMP。
## **Inactive Nomination 非活跃提名**
提名人已选择提名的一个或多个验证人，但在该 era 中并未积极验证。这类提名可能会在未来的时代变为活跃提名。
## **Inherent**
“本来就是真实的” Extrinsic。Inherents不会被 gossip 到网络上，而是由出块者放入区块中。由于它们并不像资金转账那样可证实，因此它们没有签名。区块链的runtime[4]必须具有验证Inherents的规则。例如，时间戳是Inherents，通过落在每个验证人认为合理的范围内来进行验证。
## **Injected Account 导入账户**
一个不是由 Polkadot UI 直接管理但可以通过它访问的帐户，例如由 Polkadot {.js} 浏览器扩展控制的帐户。
## **KSM**
Kusama 网络代币的缩写。
## **Kusama**
Polkadot 的 “金丝雀网络”。它由 Polkadot 软件的未经发布的早期版本构成。它不是测试网 —— 在过渡到 NPoS 之后，该网络完全掌握在社区手中（即 Kusama 代币持有者）。
## **LIBP2P**
一个开放源代码库，用于进行加密的对等通信和其他网络功能。更多相关信息请访问：https://libp2p.io/[5]。
## **Liveness 活跃性**
一种分布式系统的属性，即其最终将达到某种共识。陷入无限循环的系统被认为是非活跃的，即使计算仍在进行。最终提供结果的系统，即使结果不正确或花费很长时间才得出，也被认为具有活跃性。
## **Message 消息**
在 Polkadot 的 XCMP 协议中，消息可以是任意数据，该数据通过一个通道从一条平行链（出口链）发送到另一条（入口链），并由验证人集确保其传递。
## **Message Queue 消息队列**
在 Polkadot 的 XCMP 协议中，消息队列是等待特定接收方平行链通过通道进行处理的消息列表。
## **Node Explorer 节点浏览器**
一种为你提供有关节点的信息的工具，例如最新的区块、终结的区块以及该节点已知的当前链状态。
## **Nominated Proof of Stake 提名权益证明（NPoS）**
一种权益证明系统，提名人以自己的 stake 支持验证人，以表明对验证人良好行为有信心。提名权益股权证明与另一种更普及的概念 “委托权益证明Delegated Proof-of-Stake” 不同，提名人提名不合格的验证人将失去股份，而委托人却不会因验证人的行为而失去本金。请注意，其他一些区块链技术可能在委托人会被 slash 的情况下也依旧使用术语 Delegated Proof-of-Stake。Polkadot 使用 Phragmén 算法来将 stake 分配给被提名人。

## **Nominator 提名人**
通过绑定其令牌来选择一组验证人进行提名的帐户。提名人会收到某些验证人的奖励，但是如果提名人的验证人行为不当，提名人也会受到 slash 惩罚。

## **Rock n Roll 网络**
Punk.Network的测试网络
# NFT与数字身份的结合 实现匿名化的信用评估

![](https://tva1.sinaimg.cn/large/008eGmZEly1gpcl32sph8j30ww0bogmf.jpg)

以下内容是一个简单的思考输出，一气呵成，没有过多编辑，可能有点混乱，读的不顺畅请见谅~

近一年DeFi给了我们很多惊喜，其中各种空投就让很多人致富。最近DeFi项目有很多空投，少则几十刀，多则上万刀，但在**领空投这事上目前还有很多痛点**：

1. 不知道空投信息，不知道自己是否符合空投条件
2. 没有办法一键查询自己的所有地址有哪些空投可以领
3. 经常换地址的话，会避开很多空投符合条件，本来是个老韭菜，但无法享受空投福利

导致以上的一些问题，主要还是由于链上身份信息的匿名性。我们所有的身份都是匿名与公钥地址绑定。**对于常换地址的用户，每一次链上行为都留在了过去的地址，没法跟随自己到新的地址。**

**这是区块链的匿名特性，它是一种进步。但它也同时阻止了一些传统意义上的授信问题。**


## 分散&匿名的链上身份信息

用户在以太坊上的每一次合约交互记录都会永久的记录在链上，不可更改。有的用户喜欢一直用一个地址，有的用户喜欢经常切换地址。

对于使用一个地址的用户，所有信息都与这一个钱包地址绑定，如果有空投或者类似项目白名单的需求，可以方便的查询。

但如果是使用多地址的用户，因为地址在频繁切换，面对这种空投和白名单筛选，就会有一些吃亏。

**在现实世界，我们每个人的身份信息都可以使用一些简单的标识来验证，比如身份证号、手机号、护照等进行识别认证。**

但是在虚拟世界，一个账号很难对应到一个实际的人，一个人可以拥有N个虚拟账号，他们之间也可以完全没有联系。

尤其在加密世界，加密本身就强调隐私性，每一个地址都是独立的，只要拥有私钥就证明你对这个账号的所有权。**但是没有人希望把自己的真实身份信息与自己的加密地址联系起来。**

**这种身份信息的分散导致了无法通过一个立体的画像信息，辨别一个人的具体身份，有好处也有弊端。**

好处是匿名性，一个人可以使用不同的虚拟身份活在虚拟世界中。坏处是无法进行基于个人信用的授信。

## 现实世界的身份信息

在现实世界，我们大多采用身份标识和各类证明来辨识身份。比如通过身份证辨别一个人的公民身份，通过银行卡和资产证明辨别一个人的财务状况，通过社交关系辨别一个人的社会地位，通过购物清单辨别一个人的生活习惯。

在没有社交应用的大数据前，**一个人在银行借钱大多是通过抵押财产的形式，这与目前DeFi的超额抵押类似。**对于有一定社会地位的人，他们可以通过工作证明、工资流水等信息进行贷款申请，这是一种**信用贷款方式，用户不需要提供抵押品即可进行借款。**

用户行为大数据的使用，让互联网应用可以方便的识别哪些人有偿付能力，从而可以进行更多的无抵押信用借款，比如支付宝的蚂蚁借贷。但这也同时会引发另外的隐私话题，欧洲颁布的GDPR也对这类身份信息的过度使用提出了更严格的限制。

**而在链上，是无法直接实现信用借款的。**毕竟在冰冷的钱包背后，我们不知道那是谁，他的所有行为都记录在钱包的记录上。但由于这些地址也是分散的，很难知道他们是否属于同一个人。

## 身份信息的价值

身份信息对一个人有很多用处，简单说可以让我们出入可以出入的场所，可以让我们享受身份所匹配的服务。在互联网世界，有真实的信用背书，我们的虚拟身份也可以有更多的权限。

然而在区块链世界，由于身份信息是匿名化的，我们只能验证私钥的控制权，也就是说只能对当前所见的资产可以验证，而无法验证这个地址背后持有人的偿付能力和身份等级。

换个说法，**我们只能基于所见即所得的资产评估一个账户的偿付能力，而无法给与他超过他所拥有资产限额的额外服务。**

在现实世界，大量的借贷是依靠信用的借贷，尤其是企业的借款，大部分是信用贷款，这个体量非常庞大。而在链上，目前除非依靠第三方现实世界的中介证明，比如银行的信息证明，才能提供信用贷款。除此之外，并没有很好的方法去做信用借贷和其他的信用授权。

如果我们可以实现链上基于信用的身份授信，DeFi的资产使用量级将会增加几个数量级。

## 基于NFT的数字身份设计

**Poap这个应用给了我很多启发，它把一些特殊事件做成了NFT，比如YAM的投票、参与YFI的fair lanch等。这些NFT是对一个人参与一个事件的证明。**

如果我们把一个用户地址跟交易行为制作成NFT，这个NFT实际就是用户的一个行为标签，并带有身份标记。我们可以限制只有地址所有人可以生成这个NFT，同时每一个NFT都会绑定地址信息。

**当我们使用新地址时，我们可以将之前地址生成的行为NFT授权给新地址，这也是基于用户签名的操作，具有不可伪造性。**

通过这种设置，我们可以使用一个账号聚合自己所有地址的行为NFT，变相的就是把我们可以将所有的链上行为聚合到一起。

这么做的好处，是项目方可以通过查询NFT的方式，识别一个账号所有的历史行为，从而对这个账号形成一个立体判断。

**可以用于空投符合条件的查询，可以用于白名单设置的查询，可以进行简单的身份符合度验证，也可以实现更加复杂的用户画像和用户标签的建立。进一步也可以做一个大胆的尝试，实现无第三方中介的链上信用借贷。**

为了避免可能的身份泄露，全部的行为NFT都是基于用户自我授权的，也就是用户可以选择绑定哪些账号的行为到一个NFT中，也可以隐藏不想公开的地址。这样用户可以很好的控制隐私。

信用借贷由于无抵押，所以要根据所有的历史行为计算借款人的偿付能力。同时，为了做最后一道保障，也就是借款人跑路的情况下，如何去追偿。

我们可以做以下几个尝试：
1. 借贷设置为有限期，比如3-6个月
2. 在链上做借款人的真实身份信息校验，但只有身份提供方进行链上的加密私密保存，不向任何人公开
3. 只有当借款人未偿付时，才会触发系统调用真实身份信息进行追偿
4. 如果按期还款，真实身份信息将被销毁，过程中只有借款人自己接触过真实信息，因此不会有任何泄露
5. 未偿付行为可以设立保险基金之类的，通过保险质押奖励来补偿借贷空缺

以上仅是利用链上数字身份开展的一个信用借贷的假想，实际还会有更多其他的玩法可以基于数字身份开展。

这些是我一个初步的产品设计思考，有感兴趣的小伙伴可以联系我，大家一起探讨，没准可以做成一个项目。或者有技术实力的团队也可以去尝试下是否可行~

**想法不值啥钱，希望DeFi越来越好~**

---
微信：nigdaemon
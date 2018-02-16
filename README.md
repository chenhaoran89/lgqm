# lgqm

这是一个《**临高启明**》的Github站点，本站点的建设初衷是为了方便交流讨论。临高启明做为集体创作的网络小说，在贴吧、论坛、维基、知乎等众多平台上都可见到广泛的讨论，但我认为临高启明仍然需要更多交流的渠道以方便同人的创作。因此我想要尝试做一个临高启明同人的Github站点，在此平台上让所有参与讨论的网友对同人文章提出建设性意见，让临高启明同人也成为一个群体创作的作品，更好的为牛大的临高启明正史服务。

网站初建，只想在上面专注做一件事，就是统计临高启明物资生产和流通状况。更准确的说，是做一个澳宋国经济仿真程序。我的打算是基于正史，一步一步（精确到秒）计算临高物资生产、使用和消耗的情况。当然这中间存在大量假设、也需要输入大量边界条件，这些就算是该同人的原创了。我的初步设想是基于状态的，状态是一组巨大的向量，存储了每一种物资、每一个种工种的人员安排情况。每一秒发生的事情都会改变下一秒的状态向量，也可以说，发生的各种事情定义了状态转移的方式。在推演过程中，所有的状态转移都将是确定性的，也就是说没有随机数。这确保任何人重复推演时不会产生不一致的结果。但是我们依然会考虑随机性突发事件，我将随机生成一定的事件输入以模拟这些随机事件，一旦某日期前的事件输入定下来，这些突发事件就永久的对未来的推演产生了影响，并且不会改变。

仿真推演的结果会以天为周期存储成一个日记，方便随时查看。要查看某一天中间时刻的状态，就需要从前一天结束的记录开始重新推演。随着澳宋政权的扩大，黑科技产生的物资种类越来越多，人口也越来越多，整个状态向量实际上是不断变大的。因此这个仿真推演将会分阶段进行，每一阶段的状态向量的定义都可能发生变化。这个阶段的长度最短可能是一天。

注意到我们对澳宋国经济体的模拟，是宏观层面的模拟，不涉及具体人或事物的模拟，也就是说，我们对哪个人、哪个物在什么地方、干什么事是不细节模拟的。这一方面是因为能力和资源达不到，另一方面这样做会限制其他同人对历史的诠释、新加入的元老也可能在描述过往时产生“历史性”冲突。这意味着，我们对同类的事物只有整体性描述，不会具体细分每一个的情况。比如，登陆时有4艘8154渔轮，每一艘渔轮的工作时间其实并不一样，因此船只性能并不相同，运输速度会有快慢分别，但是在我们的模拟中，四艘渔轮会被同样看待，比如无论哪一艘8154，运输速度都是一样快的，使用中出现损坏的事件发生概率也会保持不变。

项目各工作目录：
    
1. state : 定义各状态的含义、状态转移函数及状态的约束关系
2. event : 定义和存储正史事件以及填充的随机事件
3. simulator : 实现状态推演的算法
4. diary : 保存每天推演的结果，以及可以附加解释性文字。
5. chart : 以折线图等形式呈现统计数据



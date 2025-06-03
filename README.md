# FinLBench：面向金融长文档场景的大型语言模型评测基准与数据集

本项目由**北邮金融大数据安全实验室**和**熵简科技 AI Lab** 共同发起，从项目筹备、评测集构建、工具评测到评测报告撰写共历时近5个月时间。本次工作为阶段性成果输出，也欢迎其他有兴趣参与本项目的个人或组织加入，为评测集的持续完善贡献力量，我们将在文末持续更新主要贡献者和贡献单位。
### 为什么需要金融长文档评测集 ###
自 ChatGPT 发布以来的这一年，大语言模型正以极快的发展速度一路狂飙演进，据不完全统计，中国企业发布的大模型数量已经过百。但是，大模型本身并不直接产生价值，需要与各个行业的业务场景深度结合才能真正发挥作用。如此，大模型的"机器智能"才能真正带来生产力升级。 

在金融场景中，大模型对于金融长文档的理解和推理能力是一项常见又需求广泛的基础能力，包括如智能投研、量化投资、合规审计、财富管理等等。**在目前开源的金融评测集中，文本长度一般都小于 1000字，无法满足对于金融长文档的评测的需求。而在长文档评测集中，目前仅有 L-eval 评测集包含少量金融长文档评测题**（仅包含8篇英文文档，且只覆盖业绩会这一个场景）。

为了填补这一空白，我们构建了面向金融长文档推理的开放评测集 **FinLongEval**，以提供衡量大模型在金融长文档处理的评估任务集及评估办法，推动大模型在金融场景下的落地。  
### 哪些组织可能需要用到这个评测集 ###
FinLongEval 评测集对于以下三类群体或组织有一定帮助：
- **大模型研发厂商**：帮助大模型厂商更准确理解金融场景下真实业务需求，帮助了解所研发的大模型在金融长文档场景下的能力范围及优化方向；
- **学术组织**：帮助学术机构更准确了解大模型在金融场景落地上的关键需求和主要挑战，以加快技术研究和创新；
- **金融机构**：百模大战之下，作为最终用户的金融机构，在选择大模型产品时已然 “乱花渐欲迷人眼”，本评测集可以帮助金融用户更科学、准确地筛选出符合真实场景需求的金融大模型和产品；
### 主流长文档工具的评测 ###
在 FinLongEval 评测集的基础上，本次我们也挑选了市面上几款具有代表性的用于长文档辅助阅读的产品，进行详细评估和分析。

不同于其他评测报告中直接以大模型作为评测对象，本次我们将长文档阅读和推理的产品作为评估对象，因此整个评估结果既包含了大模型本身的长文档推理和理解能力，也同时包含了处理链上的其他环节的性能，如检索准确度、文档解析和分割效果等（若产品采用 RAG 的路线）。

采用这一方案的原因在于，我们希望站在金融从业者（最终用户）的角度，全面评估当前大模型商业产品对于金融长文档处理能力的边界和不足，以及距离业务成熟可用的距离。

## 评测集详情介绍 ##
### 构建原则 ###
在 FinLongEval 构建过程中，我们希望评测集能够从一线金融业务场景来，再服务到各个业务场景中去，能够真正代表金融场景下的各类典型问题和典型需求。为此，我们和多家一线证券公司的业务部门和IT部门进行深入沟通，最终整理和搜集了最具代表性的 **8 大类金融长文档**和 **12 大类问题**，共计 **43 篇金融长文档**和 **347 道问题**（FinLongEval 1.0版）。 
### 文档类型 ###
如上所述，在金融长文档类型上，我们总共搜集和整理了 8类一级分类文档，18类二级分类文档。各类文档的基本情况如下所述：
- **券商研究报告**：涵盖个股研报、行业研报、宏观研报、金工研报这四类常见券商研报，文本长度在1万字至3万字之间；
- **上市公司公告/募集书**：涵盖拟上市公司招股书、债券募集书、基金募集说明书、上市公司年报、业绩预告&快报、股权激励公告等，文本长度大部分在10万字至30万字之间；
- **财经资讯**：涵盖财经评论、主流财经媒体的财经早报等，文本长度在3千字至1万字之间；
- **会议路演**：涵盖业绩交流会、策略会等会议文字，文本长度在1万字至5万字之间；
- **政策文件**：涵盖国务院政策文件、政府工作报告、人民银行的货币政策报告等文件，文本长度在1万字至5万字之间；
- **学术论文**：涵盖货币政策、外汇储备、疫情研究等金融学术类文章，文本长度在1万字至3万字之间；

下图所示为本评测集的文件类型分布比例图，券商研究报告、上市公司公告/募集书（定期报告、公司发行、公司重大事项）、财经资讯、会议路演文件，占比分别为 25.4%、19.3%、17.9%、15.6%。在文件类型覆盖度和覆盖比例上面我们尽量做到与实际业务场景的需要处理文件类型分布比例保持一致。
<div align="center">
  <img src="https://github.com/valuesimplex/FinLongEval/blob/main/fig/%E6%96%87%E4%BB%B6%E7%B1%BB%E5%9E%8B%E5%88%86%E5%B8%83%E5%9B%BE%E9%A5%BC%E5%9B%BE.png" width="750px" height="500px">
</div>

### 问题类型 ###
为了充分考查大模型在金融长文档上面的能力表现，同时充分考虑在实际业务的各类场景，如投研分析、文档合规审查、投教服务等场景，我们设计了12类不同类型的问题，以期望从不同维度、不同场景下对于大模型进行充分的评估和测试。具体的问题类型、相应的考查目标和业务场景如下表所示：

| 问题类型 | 任务描述 | 金融场景任务描述 |
| ----- | ----- | ----- |
| 信息提取 | 从文本中获取指定类别信息，重点考查系统的检索能力以及大模型的信息提取能力。 | 金融机构需要从文档中提取出某种特定的信息，如识别公司实体、事件查询等。如快速获取招股书中的发行人基本信息。 |
| 表格提取 | 从文档中识别和提取表格，重点考查系统解析PDF表格能力，以及大模型对于二维表格数据的理解能力。 | 某些精细的投研数据只存在于表格中，需要精准识别。如定期报告的财务摘要数据一般存在于表格中，包括研报中的盈利预测数据等等。 |
| 关键数据提取 | 精确识别统计数值，重点考查系统精确检索能力，以及大模型的实体提取能力。 | 抽取金融文档中的特定数值信息，如从公司业绩会的纪要中抽取营收、毛利等指标数据，从公司报告中抽取产销量等经营指标。 |
| 阅读理解 | 深入分析和理解文本意义，重点考查大模型的长文本理解的综合能力。 | 常见场景如帮助分析师快速生成某个问题的相关数据、分析逻辑、结论。例如，公司的毛利率变化分析，需要大模型不仅找到相关数据，还要理解毛利率的概念，影响因素等，综合分析后给出结论。 |
| 事件分析 | 分析文本中的事件，大模型通过适当的逻辑推理得到正确答案，重点考查大模型的金融概念理解、金融事理的逻辑推理能力。 | 对于资讯中的事件，分析师可以让大模型进一步思考，获取更多推理后的信息。常见场景包括，量化投资、政策分析、ESG因子挖掘等等。 |
| 逻辑推理 | 分析文本中的论证和逻辑关系,并通过多步推理得出新的结论。重点考查大模型的逻辑推理能力，尤其在金融问题下的推理能力。 | 常见场景包括在投资研究场景中，分析师需要让大模型基于公司基本面情况辅助进行未来业绩分析，或者基于行业基本面情况，辅助进行行业走势分析。 |
| 关键词 | 摘录文本的主题词，重点考查大模型的文本提炼能力。 | 快速总结金融文档中的主旨的关键词。比如会议路演的关键词。 |
| 文本摘要 | 生成对文本主要内容的精简汇总，重点考查大模型的文本提炼能力。 | 快速金融投研文档中的摘要，如会议路演的文档可快速生成摘要，典型场景包括如政策分析、机构问答分析、文本因子挖掘等。|
| 生成提纲 | 产出文本内容的框架和要点，重点考查大模型的文本提炼能力。 | 服务于写作场景，如政府报告可生成简要提纲后，写点评。 |
| 对话人分辨 | 辨认出对话中不同的发言人，重要考查大模型的多人对话的理解能力。 | 会议路演通常是多人参与，准确识别多人角色才能准确总结每个角色的内容。 |
| 陷阱问题 | 重点考查大模型的在幻觉方面的严重程度。在我们的场景下，幻觉是指大模型在回答的答案中生成了金融文档并不包含的事实信息。 | 对于金融行业来说，精准的信息至关重要。大模型的幻觉程度，直接影响了基于大模型的系统在金融场景下的可落地程度。 |
| 计算问题 | 重点考查大模型的数学计算能力。 | 基于文档中的已知数据，分析师希望进一步做一些数据计算工作，如计算衍生指标。 |

下图所示为本评测集的问题类型分布图。其中，阅读理解、信息提取、逻辑推理的数量最多，占比分别是 26%、25%、13%，表格提取、事件分析、文本摘要、陷阱问题等的比例相当，均在 7% 左右。这一分布比例也较为符合我们在前期做机构调研时的抽样结果。

<div align="center">
  <img src="https://github.com/valuesimplex/FinLongEval/blob/main/fig/%E9%97%AE%E9%A2%98%E7%B1%BB%E5%9E%8B%E5%88%86%E5%B8%83%E5%9B%BE.png" width="450px" height="350px">
</div>

### 文件的长度分布 ###
<div align="center">
  <img src="https://github.com/valuesimplex/FinLongEval/blob/main/fig/%E6%96%87%E6%A1%A3%E9%95%BF%E5%BA%A6%E5%88%86%E5%B8%83%E5%9B%BE.png" width="500px" height="280px">
</div>

上图所示为本次评测集中各个文件字数分布比例，可以看出，**超过80%以上的文件字数超过了1万字**，这一长度远远大于现有金融评测集的平均文本长度。超过 40% 以上的文件字数超过了2.5万字，这一长度超过了当下典型商用大模型的上下文窗口长度。此外，本评测集还包含了最长字数超过 **50万字**（约500页）的超长金融文档。

由此也可以看出，在实际各类金融业务场景中，典型的金融文件都在数万字，某些场景下几十万字也是常态，因此长文档处理能力是大模型在金融场景落地的必备基础能力。
### 参考答案的编写 ###
在编写本次评测集的参考答案过程中，我们采用了 “2+1+1” 的工作流程。首先，我们采用了2个当下最先进的大模型 GPT4 和 Claude2 根据问题和金融文档的原始内容，分别编写两个答案。接下来，会有一名人类专家根据原始文档对于两个答案进行逐一检查确认，并融合成一个完整、连贯的答案。最终，另有一名人类专家根据金融文档的原始内容对于这一答案进行复核和优化，并以此作为最终的参考答案。

采用这一流程的原因在于，本次评测集的问题 80% 为主观类问题且文本长度在几万字量级，如果直接由人工编写非常耗费时间，同时我们也发现当下最先进的AI系统通过适当人力协助，已经能够编写接近人类水平的答案，因此我们最终决定采用这种人机结合的方式。
### 样例数据 ###
如下图所示，本评测集的构成有**一级文件类型**、**二级文件类型**、**文件名**、**问题类型**、**问题**、**参考答案**等。
这里给出了三个例子，有研报的公司财务数据提取、招股书的发行人毛利率情况分析，还给了一个陷阱问题的示例。更多样例数据请参考[样例文件夹](https://github.com/valuesimplex/FinLongEval/blob/main/data/sample_data.jsonl)。
<details>
  <summary>点击查看表格</summary>

  | 一级类型 | 二级文件类型   | 文件名                                       | 问题类型 | 问题                                                         | 参考答案                                                     |
| -------- | -------------- | -------------------------------------------- | -------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 研报     | 个股研报       | 同花顺(300033)乘AI东风，金融信息服务扬帆起航 | 表格提取 | 提取同花顺2021-2025年的财务摘要。指标为营业收入、归属母公司净利润、每股收益、市盈率。要求：以表格形式输出。单位把百万元转换为亿元。 | “同花顺2021-2025年的财务摘要,具体如下: 财务摘要(亿元) 指标  2021A  2022A  2023E  2024E  2025E   营业收入  35.10  35.59  40.68  45.97  51.32  归属母公司净利润  19.11  16.91  20.51  22.29  24.49  每股收益(元)  3.56  3.15  3.82  4.15  4.55   市盈率  40.61  31.30  59.48  54.74  49.83  主要内容包括: 1. 2021-2022年的财务数据为公司报告的数据。 2. 2023-2025年的数据为预测值。 3. 单位全部转换为亿元。 4. 指标包括营业收入、归属母公司净利润、每股收益和市盈率。” |
| 公告     | 拟上市公司招股 | 中电港招股说明书                             | 阅读理解 | 请告诉我，发行人近三年的主营业务的毛利率情况，分析毛利率变化的原因。然后，比较一下发行人与可比公司的毛利率情况。 | “中电港近三年的主营业务毛利率情况如下：- 2019年度：3.72%- 2020年度：3.87%- 2021年度：3.53%，报 告期内公司主营业务综合毛利率较为稳定。 毛利率的变化主要受以下因素影响： 1. 供需状况的变化：上游原厂产品的供应充足程度和下游电子需求的旺盛程度，以及客户与供应商的议价能力，都会对电子元器件分销行业的采购成本和销售毛利产生影响，导致行业利润水平波动。 2. 汇率波动：由于高端电子元器件的进口依赖，汇率波动会影响成本和毛利。 比较中电港与同行业可比公司的毛利率情况，可以看到中电港的毛利率通常低于同行业的其他公司。同行业可比公司的毛利率情况为-2019年度：7.90%，-2020年度：7.89%，-2021年度：8.87%。这可能是由于中电港在供应链中的议价能力、市场定位、产品组合和运营效率等方面与这些公司存在差异所致。” |
| 研报     | 个股研报       | 电车王者逐鹿全球，垂直整合构筑核心竞争力     | 陷阱问题 | 比亚迪的主要业务是燃油车，介绍一下比亚迪的燃油车业务情况     | 截至2022年3月，比亚迪已经开始停售燃油车，转而专注于新能源汽车的开发和销售。因此，关于比亚迪的燃油车业务的详细情况，目前报告中没有提供更多信息，因为公司已经将其业务重心完全转移到新能源汽车上。 |

</details>

## 评估示例

<div align="center">
  <img src="https://github.com/Invariant0502/FinLBench/blob/main/figure/figure9.png" width="600px" height="300px" alt="评估流程示意图">
</div>

我们在上图中展示了整个评估流程示例。首先，将问题和原始文本输入到待评估的 LLM，从而得到模型的输出。在评估过程中，对于商业模型，我们直接将完整的 PDF 文件提交给 LLM；而对于本地部署的开源模型，无法直接提交 PDF，只能先将 PDF 提取成纯文本，再输入模型。随后，将生成的内容、问题和评估提示一起输入用于评分的 LLM，得到模型输出的分数和理由。最后，将所有获取的内容与原始文本进行对比，并对分数做微调，得出最终评分。

在获取该示例的初始评分后，我们发现若干不一致之处，因而做出以下调整：首先，评分模型给出的相关性分数超出了 0 到 1 的范围，我们将其上限设为 1 分。其次，连贯度得分的理由为“未能解释所产生的经济效益和影响”，与我们的连贯度标准不符，因此我们将连贯度修正为 2 分。最后，忠实度反映模型输出与原文的契合度，最初的评分并未对照原文进行判定。对比生成答案与原文后，我们发现原文确实包含相似内容，因此将忠实度调整为 1 分。

## 六维度评估体系

- **相关性（1 分）：** 生成答案与问题之间的关联程度。确保相关性意味着模型能给出直接与金融问题相关的回答，对准确决策至关重要。  
  **专家意见：** 相关性是评估的基础维度，因此该维度采用二元评判：内容首先必须高度贴合主题，才能对其他维度进行考察。

- **流畅性（2 分）：** 判断生成答案是否通顺、主旨清晰、语法合理。流畅性保证输出内容清晰易懂。  
  **专家意见：** 流畅性直接影响阅读体验和理解度。在金融领域，尽管语言表达重要，但准确性和实用性更为关键，因此流畅性赋予适中权重，以平衡语言表达与信息质量。

- **连贯度（2 分）：** 考察答案文本逻辑结构是否合理、段落组织是否恰当。连贯度对复杂金融分析和报告的逻辑性与条理性至关重要。  
  **专家意见：** 连贯度保证内容逻辑清晰，但在金融领域，其重要性略逊于实用性和一致性，因为后者对决策质量影响更大。

- **有用性（5 分）：** 判断生成答案是否满足用户需求并提供必要信息（是否有明确结论、是否提供详实数据支持）。有用性衡量模型是否能为金融决策提供有价值的见解和数据。  
  **专家意见：** 有用性直接体现内容的实用价值，是评估的核心目标，因此赋予最高权重。

- **一致性（4 分）：** 判断答案文本是否正确回答问题。通过一致性确保生成的数据和结论前后不矛盾，避免给出相互冲突的金融观点。  
  **专家意见：** 在金融领域，高度一致性是建立信任的关键要素，因此为该维度给予显著权重。

- **忠实度（1 分）：** 判断生成答案是否忠实于原文本。忠实度保证输出准确反映原始金融数据，维护可靠性。  
  **专家意见：** 忠实度是保证内容准确性的基础要求，在金融领域不可忽视。

## 提示语设置

### 系统提示语

以下为简化版系统提示，用于指导模型根据六维度标准生成并评分。完整提示请参见附带文档。

相关性：问题与答案之间的关联程度。  
评分：0 分 – 无关；1 分 – 与问题相关。

流畅性：答案文本的清晰度和语法。  
评分：0 分 – 表达不清或存在错误；1 分 – 可理解但存在问题；2 分 – 清晰且语法正确。

连贯度：答案文本的逻辑结构和一致性。  
评分：0 分 – 逻辑混乱或不一致；1 分 – 与常识相符；2 分 – 逻辑性强、结构合理。

有用性：细节、清晰度及与问题契合度。  
评分：0–5 分，依据详细标准，包括数据、逻辑流程和覆盖所有方面。

一致性：答案文本与参考答案的契合度。  
评分：0–4 分，依据一致性与准确程度。

忠实度：答案是否忠实于参考答案。  
评分：1 分 – 忠实；0 分 – 包含额外或无关信息。

### 通用任务评估提示

通用任务提示用于指导系统根据参考答案对生成答案进行评分，需结合系统提示使用。

任务描述：请根据给定的问题、参考答案和待评估答案，按照相关性、流畅性、连贯度、有用性、一致性、忠实度 6 个维度打分。先给出整数分数，再附上理由。

问题：  
{question}

参考答案：  
{reference_answer}

待评估答案：  
{generated_answer}

示例输出格式：  
相关性：X 分  
理由：————————

流畅性：X 分  
理由：————————  
…

### 陷阱问题评估提示

以下提示用于判断模型生成的答案中是否包含虚构内容，用于评估生成内容的可信度。

任务描述：根据给定的问题、参考答案和生成答案，判断生成答案是否包含虚构内容，并说明理由。

问题：  
{question}

参考答案：  
{reference_answer}

生成答案：  
{generated_answer}

输出格式：  
有无虚构：有/无  
理由：————————

### 数据计算评估提示

该提示用于验证生成答案的计算是否准确，计算结果必须与参考答案完全一致。

任务描述：根据给定的数据计算问题、参考答案和生成答案，评估生成答案的计算是否正确，计算结果必须与参考答案完全一致方可视为正确。

问题：  
{question}

参考答案：  
{reference_answer}

生成答案：  
{generated_answer}

输出格式：  
正确/错误  
理由：————————

## 数据集构建方法

### 金融长文档数据集构建

本数据集的所有金融长文档均来自中国最大证券交易所——上海证券交易所的信息披露文件。在确定 FinLBench 中包含的八类文档时，我们既参考了行业内的具体需求，也兼顾了数据集的广泛适用性，旨在构建能反映金融分析和决策过程中多样文档类型的综合数据集。具体选取理由如下：

- **研  报：** 包括个股研报、行业研报、宏观研报和量化研报，是投资研究的基础材料。选入原因在于投资决策对深度分析的需求，文本长度通常在 10,000 到 30,000 字之间。
- **公司重大事项：** 主要涵盖股权激励公告等文件，有助于理解公司治理与员工激励机制。通过分析股权激励公告，投资者和分析师可洞察公司留才策略及长期增长潜力，文本长度约 300,000 到 500,000 字。
- **财经资讯：** 包括主流财经媒体评论和早报，能及时获取市场动态与新闻。文本长度较短，约 3,000 到 10,000 字，适合快速分析和决策。
- **会议路演：** 包含业绩电话会议和策略会等，提供公司策略与市场定位的深度见解。文本长度通常在 10,000 到 50,000 字之间，反映会议讨论的详细程度。
- **政策文件：** 涵盖国务院政策文件、政府工作报告和央行货币政策报告等，是理解监管与经济环境的关键。文本长度在 10,000 到 50,000 字之间。
- **学  术论文：** 涵盖货币政策、外汇储备、疫情研究等金融学术专题，提供对金融问题的理论洞见。文本长度在 10,000 到 30,000 字之间，适合集合深入学术分析。
- **定期报告：** 包括财务摘要、行业报告、宏观报告和量化报告等，支撑投资研究所需的定量分析，文本长度在 10,000 到 30,000 字之间。
- **公司发行：** 包括招股说明书、债券募集书、基金募集说明书、年报、业绩快报等文件，有助于了解公司行动与财务状况。大部分文本在 100,000 到 300,000 字之间，反映其综合性与详尽度。

选择这些文档类型旨在兼顾行业需求与广泛适用性，使 FinLBench 成为金融专业人士和研究者的多场景评估工具。通过覆盖多样文档类型，增强数据集在各金融场景中的实用性和关联度。

### 专家驱动的问题设计

我们采用专家驱动的方法构建 FinLBench 的问题，以确保问题与实际金融场景对齐，并满足真实分析需求。该方法利用领域专家设计精准、贴合且具有代表性的测试问题。每种问题类型的评估目标和业务场景描述见表 \[tab:financial_tasks\]。

#### 设计原则

在设计基准时，我们确保评估数据集源于一线金融业务场景，并能服务于多种应用场景。为此，我们遵循以下原则：

- **场景对齐：** 问题应反映金融分析师日常工作中面临的真实挑战与询问。
- **领域专家：** 每个问题均由金融领域专家精心设计，确保准确性、上下文相关性和分析深度。
- **覆盖与关联：** 问题结构涵盖多种金融场景，代表行业中典型需求与多样问题类型。

#### 协作开发过程

我们与多家领先券商的业务和 IT 部门的金融专家紧密合作，共同开发问题，确保所构建的问题贴合真实金融实践与挑战。该过程保证问题既具备理论合理性，又具备实际可操作性，为评估金融长文档分析能力奠定坚实基础。

<div align="center">
  <img src="https://github.com/Invariant0502/FinLBench/blob/main/figure/figure14.png" width="800px" height="250px" alt="评估流程示意图">
</div>

### 使用 LLM 构建问题

我们还采用了使用 LLM 构建 FinLBench 问题的方法。通过将提示语作为模板，使用非被测模型的 LLM 来生成问题，我们发现 LLM 不仅能根据文档和问题生成答案，还能高质量地构建符合要求的问题。提示模板如图 \[fig:template1\] 所示。其中，“金融场景”部分描述问题产生的背景，告知 LLM 分析师在文档中关注的内容或重点；“问题类型”部分简要说明问题的类别与特点。

为了保证 LLM 生成问题的高质量，我们邀请金融专家对 LLM 生成的问题进行审核筛选，挑选出在实际场景中具有价值的问题纳入数据集。

<div align="center">
  <img src="https://github.com/Invariant0502/FinLBench/blob/main/figure/figure12.png" width="600px" height="300px" alt="评估流程示意图">
</div>

我们展示了一个使用 LLM 构建事件分析问题的示例，如图 \[fig:examplequescon\] 所示。LLM 提出的第一个问题在给定场景下具有价值并被采纳，而第二个问题因在该场景下相关性和实用性较低而被拒绝。

<div align="center">
  <img src="https://github.com/Invariant0502/FinLBench/blob/main/figure/figure13.png" width="600px" height="300px" alt="评估流程示意图">
</div>

### 参考答案的混合流程

在构建 FinLBench 参考答案时，我们采用“2+1+1”混合流程（见图 \[fig:workflow\]），以确保答案质量。对于有明确答案的封闭式问题，直接从原文中抽取相关内容作为参考答案。对于占 80% 且涉及长篇金融文档的开放式问题，我们采用人机结合的方法以兼顾效率与质量。

具体而言，首先使用两款最先进的 LLM（ChatGPT 4 和 Claude 2）分别生成初始答案；接着，由一名专家对 AI 生成的两个答案进行审核，将二者优点整合成连贯且完整的答案；最后，另一名专家对整合后答案进行复核与优化，确保其准确性、清晰性与对照原文一致。最终得到的答案即为评估数据集的参考答案。

之所以采用此流程，是因为大多数问题具有主观性且文档篇幅较大，直接人工编写耗时巨大；而经过适当人力监督，先进 AI 模型能够生成接近人类水平的答案。人机协作既提升效率，又保证了 FinLBench 数据集所需的高标准。


## 金融长文档处理能力的评估办法 ##
### 评估维度 ###
为了对于大模型生成的答案进行细颗粒度的评价，参考通行的方案，我们选择了 6 个评估维度来对各个大模型所生成的答案进行评估，分别是**相关性**、**有用性**、**流畅性**、**连贯性**、**一致性**和**忠实度**，各维度的详细介绍如下：

| 评估维度 | 维度含义 | 分值范围 |
| ----- | ----- | ----- |
| 相关性（Relevance） | 评估用户提的问题与大模型所生成的答案是否相关，是否存在“答非所问”的情况 | 0-1分 |
| 有用性（Helpfulness） | 评估大模型所生成的答案是否满足用户请求并提供所需信息，重点考察是否有明确结论、是否提供详细的数据支撑 | 0-5分 |
| 流畅性（Fluency） | 评估大模型所生成的答案是否句子流畅，主旨是否清晰，语法是否合理 | 0-2分 |
| 连贯性（Coherence） | 评估大模型所生成的答案是否符合常识的、有逻辑的、文本段落组织合理的，是否存在前后矛盾的情况 | 0-2分 |
| 一致性（Consistency） | 将大模型所生成的答案与参考答案进行比较，判断大模型的回答文本与参考答案的一致性（包括关键数据一般要完全一致） | 0-4分 |
| 忠实度（Faithfulness） | 评估大模型所生成的答案是否忠实于原文，用来评估可能存在的幻觉情况 | 0-1分 |

### 评估流程 ###
在本评测集中，除了少量的关键词、陷阱问题类任务，大部分问题是开放式问题，因此整体评分采用人机配合，并由人类专家完成最终打分。

对于封闭式问题，可以使用诸如 ROUGE（Recall-Oriented Understudy for Gisting Evaluation）之类的自动评估方法，因为这些问题通常具有明确且确定的答案。ROUGE 是一种基于 n-gram 重叠的评估方法，通过计算生成的回答与参考答案之间的共享词汇和短语来评估回答的质量。这种方法在封闭式问题上表现良好，因为它可以直接比较生成的回答与正确答案之间的相似度。

然而，对于开放式问题，答案可能具有多样性、主观性以及高层次的语义性，这使得自动评估方法（如 ROUGE）难以准确评估生成回答的质量。在这种情况下，人类评估是更可靠的方法，因为人类专家可以自己的专业背景，根据问题的背景和上下文，以及答案的相关性、准确性和充分性来对生成的回答进行综合评价。同时，人类评估能够捕捉到自动评估方法可能忽略的细节和细微差别，从而更好地反映回答的质量。

结合本评测集的实际情况，对于每个问题，我们先用 GPT-4 结合参考答案从6个维度对于大模型生成的回答进行分别打分，然后每一个答案由多名人类专家参考机器打分独立进行打分，最终再汇总得到最终分数。
<div align="center">
  <img src="https://github.com/valuesimplex/FinLongEval/blob/main/fig/%E8%AF%84%E4%BC%B0%E6%B5%81%E7%A8%8B%E7%A4%BA%E6%84%8F%E5%9B%BE.png" width="600px" height="300px">
</div>

## 评测结果 ##
### 评估对象 ###
本次的评测选择了8款基于大模型的长文档辅助阅读的产品，涵盖海外头部工具 Claude2、ChatGPT4、ChatPDF、以及国内五款工具，包括两家金融行业内产品和三家通用领域产品，此8款产品是我们调研下来金融行业内使用较为广泛的产品。为避免潜在的商业纠纷，国内五款产品在下面的评估结果中分别代称为 Tool_A，Tool_B，Tool_C，Tool_D，Tool_E。如果有进一步学术研究需求，可联系项目组获取完整的评测报告。
### 整体评估分析 ###
| 工具名称     | 相关性 | 流畅性 | 连贯性 | 有用性  | 一致性 | 忠实度 | 总分 |
|----------| ----- | ----- | ----- |------| ----- | ----- | ----- |
| Claude2  | 0.99 | 2.00 | 1.95 | 4.14 | 2.90 | 0.82 | 12.80 |
| ChatGPT4 | 0.96 | 2.00 | 1.93 | 3.95 | 2.94 | 0.81 | 12.59 |
| Tool A   | 0.98 | 2.00 | 1.93 | 3.85 | 2.87 | 0.76 | 12.55 |
| Tool E   | 0.98 | 2.00 | 1.92 | 3.84 | 2.57 | 0.75 | 12.06 |
| Tool B   | 0.95 | 2.00 | 1.70 | 3.06 | 2.16 | 0.57 | 10.44 |
| Tool C   | 0.90 | 1.99 | 1.54 | 2.52 | 1.82 | 0.51 | 9.28 |
| Tool D   | 0.90 | 1.99 | 1.64 | 2.72 | 1.76 | 0.48 | 9.49 |
| ChatPDF  | 0.84 | 1.99 | 1.58 | 2.44 | 1.60 | 0.45 | 8.90 |

从以上结果中，可以得出以下结论：
- 即使在金融场景下，面向长文档处理问题，**Claude2 和 ChatGPT4 依然是综合表现最好的两款工具**，属于第一梯队，而国内的几款工具表现波动较大，部分工具表现已经接近第一梯队。令人意外的是，采用 GPT-3.5 的 **ChatPDF 在本次评测中得分最低**，这也充分说明了在长文档场景中，大模型的本身能力只是一部分，**文档切割、文本召回等同样是很重要的模块**；
- 在细项维度上，除个别工具外，几乎所有工具在**相关性**和**流畅性**上面均表现很好，这说明基于大模型的系统能够较为**准确地理解金融场景下的问题**，并生成流畅的回答，这两点在大模型时代基本已经不再是问题；
- **连贯性**和**有用性**这两点是区别工具在金融长文档场景上的主要差异点，前者反映了生成回答内在逻辑一致性，后者反应了回答的信息量，一般连贯性在 1.7 以上，有用性在 3.6 以上是业务部分可用的分数，可以看出部分国产工具已经达到这个标准；
- **一致性**和**忠实度**综合反映了工具在回答问题时的提取关键信息的**准确性**以及**幻觉程度**，可以看到即使是 Claude2 在一致性上距离满分4仍然有一定距离，因此对于**数据精确极高的场景目前的工具可能都无法完全满足**。
### 分文档类型分析 ###
<div align="center">
  <img src="https://github.com/valuesimplex/FinLongEval/blob/main/fig/%E8%AF%84%E6%B5%8B%E5%AF%B9%E8%B1%A1%E5%BE%97%E5%88%86-%E6%96%87%E6%A1%A3.png" width="650px" height="220px">
</div>

从以上的结果中，可以得出以下结论：
- 在**公司重大事项**、**政策文件**两类材料上，几款工具整体表现较为均衡，均能达到业务可用的要求，这主要是因为这两类材料中的评测问题集中在信息提取和阅读理解这两类问题上，对于工具能力要求相对适中；
- 在**财经资讯**、**会议路演**这两类材料上，几款工具表现差异较大，Claude2、ChatGPT4 及部分国产工具能够有效处理相关问题，但包括 ChatPDF 在内的其他一部分工具则基本无法处理相关问题。仔细分析会发现，这主要是因为这两类材料包含的主要问题为事件分析、逻辑推理、长上下文的说话人关系判断，这都需要大模型具备较强的推理能力、以及较强的长文本处理能力。

### 分问题类型分析 ###
<div align="center">
  <img src="https://github.com/valuesimplex/FinLongEval/blob/main/fig/%E8%AF%84%E6%B5%8B%E5%AF%B9%E8%B1%A1%E5%BE%97%E5%88%86-%E9%97%AE%E9%A2%98.png" width="650px" height="220px">
</div>

从以上的结果中，可以得出以下结论：
- 在**逻辑推理**、**事件分析**上各工具差距明显，这类问题对于大模型的复杂推理和长文档推理能力要求较高，这主要由各工具所采用的底层模型能力决定；
- 各个工具在长文档信息处理上的差距同样明显，这类问题包括**对话人分辨**、**文本摘要**等。两个头部工具以及部分国内工具均能达到业务可用，但是也存在一部分工具得分很低的情况。这主要由大模型本身能够**理解和处理的上下文窗口长度**，以及在检索后给到大模型**参考的相关文本片段数量**这两个因素共同决定；
- 在**信息提取**、**关键数据提取**这两类任务上各工具表现差异较小，这一类任务一般只需要找准特定的文本片段，再结合大模型的短文本理解能力即可较好完成，这说明当前大模型已经能够较好地处理这类问题。

### 数据计算类问题分析 ###
<div align="center">
  <img src="https://github.com/valuesimplex/FinLongEval/blob/main/fig/%E6%95%B0%E6%8D%AE%E8%AE%A1%E7%AE%97.png" width="817px" height="457px">
</div>
从以上结果可以看出，除了 ChatGPT4 外，其他工具在**数据计算类**任务上表现都较差。我们仔细分析会发现，Claude2 以及部分国内工具的计算过程是正确的，但是最终的答案部分计算错了。因此，从这一评测来看，对于**需要数据计算的金融场景中，建议采用外部工具来处理**，如 Code Interpreter，大模型在这类问题中主要担任规划、调用和整合工具输出的作用。 

### 在陷阱问题下的评测 ###
| 工具 | Tool D | ChatGPT4 | Tool C | Tool B | Claude2 | Tool A | ChatPDF | Tool E |
| ----- |--------| ----- | ----- | ----- | ----- |--------| ----- | ----- |
| 编造率 | 80% | 45% | 60% | 70% | 42% | 65% | 28% | 35% |

从以上结果可以看出，即使是综合表现最好的工具 Claude2、ChatGPT4 等，在陷阱问题上至少有 40% 情况下无法通过，大部分国内工具有超过 60% 的问题都无法通过。因此，针对金融这类对于真实性和可溯源性要求严格的场景，当前的**大模型工具在抑制幻觉问题上仍然任重而道远**。

### 文件应答评测 ###
| 工具 | Tool A | ChatGPT4 | Tool C | Tool B | Tool D | Tool E | ChatPDF | Claude2 |
| ----- | ----- | ----- | ----- | ----- |-----|-----| ----- |-----|
| 应答率 | 100% | 100% | 98% | 98% | 98% | 92% | 90% | 63% |

从以上结果可以看出，从工具可用性这个角度出发，国内大部分工具对于金融文档的兼容性都处理较好，但是在实际中我们发现 Claude2 有 40% 的文件无法解析或进行应答。
### 总结 ###
整体而言，从以上的评测结果中，我们可以初步总结如下：
- 在金融场景下的泛文档和泛任务处理上，**通用大模型的基础能力**仍然是最重要的，这个基础上，通过工具结合、金融场景的强化训练等，部分国产工具在金融长文档上面的理解和推理能力已经接近 ChatGPT4 和 Claude2 ，部分问题类型上能够超过。
- 在金融场景下，**理解用户问题**、**生成流畅的文本**在大模型时代是一件相对容易实现的工作；
- **大模型的幻觉短期内无法根本解决**，对于真实性和可溯源性要求严格的场景，建议采用产品功能和技术攻坚结合的方式；
- **金融场景下的数值计算的问题不应该寄希望于模型本身来解决**，而是采用类似 Code Interpreter 的方式来解决；
## 完整评测集获取
请通过以下任意邮箱联系获取：

- **北邮金融大数据安全实验室**：yangzl@bupt.edu.cn

- **熵简科技 AI Lab**：liyu@entropyreduce.com

联系时请提供以下信息：
```
- 单位名称：
- 联系人：
- 联系邮箱：
- 使用场景：
```
## 引用
如果本项目对您的研究有所帮助，请引用如下:

```
@online{FinLongEval,
  author = {Xinguang Jiang, Sihan Hu, Dingfu Yu, Yuhao Zhang, Zhongliang Yang, Yu Li, Linna Zhou and Valuesimplex AI Lab},
  title  = {FinLongEval},
  url    = {https://github.com/valuesimplex/FinLongEval},
  year   = {2023},
  month  = {Dec}
}
```
# FinLBench: A Benchmark Dataset for Long-Document LLM Evaluation in Financial Scenarios

This project was jointly initiated by the **Financial Big Data Security Laboratory at Beijing University of Posts and Telecommunications** and the **EntropyReduce AI Lab**, spanning nearly five months from project planning, benchmark construction, tool evaluation, to report writing. This deliverable represents an interim output, and we welcome individuals or organizations interested in contributing to the ongoing enhancement of the benchmark dataset to join us—we will continue to update the list of primary contributors and contributing organizations at the end of this document.

### Why We Need a Financial Long-Document Benchmark

Since the release of ChatGPT one year ago, large language models (LLMs) have advanced at a breakneck pace. By some counts, Chinese companies alone have released over a hundred large models. However, LLMs do not generate value on their own—they must be deeply integrated with real-world industry scenarios to truly drive productivity improvements through “machine intelligence.”

In financial contexts, an LLM’s ability to understand and reason over long-form documents is a ubiquitous and widely demanded foundational capability—spanning use cases such as intelligent investment research, quantitative investing, compliance auditing, and wealth management. **Existing open-source financial benchmarks typically involve texts under 1,000 characters, which is insufficient for evaluating long-document scenarios. The only long-document benchmark containing financial documents, L-eval, includes just eight English documents and covers only earnings calls.**

To fill this gap, we have created **FinLBench**, an open benchmark for reasoning over long financial documents. It provides a suite of evaluation tasks and methodologies to measure LLM performance on financial long-form texts, thereby advancing the practical deployment of LLMs in finance.

### Who Might Benefit from This Benchmark

FinLBench offers value to several types of users:

* **LLM Developers**: Helps vendors understand real business requirements in finance and identify where their models excel or need improvement on long-form financial texts.
* **Academic Institutions**: Aids researchers in pinpointing key challenges and requirements for LLMs in finance, accelerating innovation.
* **Financial Institutions**: With a proliferation of LLM products in the market, this benchmark enables financial users to scientifically and accurately select models that meet real business needs.

### Evaluation of Mainstream Long-Document Tools

Building on the FinLongEval benchmark, we selected several representative commercial tools for long-document assistance and conducted a detailed evaluation. Unlike other reports that evaluate the base LLMs directly, our evaluation focuses on end-user products, encompassing not only the model’s reasoning and comprehension capabilities but also upstream components such as retrieval accuracy, document parsing, and segmentation (e.g., in RAG-based systems).

This approach reflects the perspective of financial practitioners, providing a comprehensive assessment of current commercial offerings’ strengths and limitations in processing long financial documents.

## Details of the Benchmark Dataset

### Construction Principles

In constructing FinLBench, we aimed for the dataset to originate from frontline financial business scenarios and generalize to various downstream tasks, truly representing typical financial questions and requirements. We engaged in deep consultations with business and IT teams at leading securities firms to collect the most representative content, resulting in eight primary document categories and twelve question categories, comprising **43 financial documents** and **347 questions** (FinLongEval v1.0).

### Document Types

We collected and organized documents into 8 top-level categories and 18 subcategories. The basic statistics are:

* **Broker Research Reports**: Covers equity, industry, macro, and quantitative research reports; approximately 10,000–30,000 characters in length.
* **Issuer Announcements/Prospectuses**: Includes IPO prospectuses, bond prospectuses, fund prospectuses, annual reports, performance forecasts & bulletins, equity incentive announcements; mostly 100,000–300,000 characters.
* **Financial News**: Encompasses financial commentaries and mainstream media morning briefs; 3,000–10,000 characters.
* **Earnings Conference Transcripts**: Covers earnings calls and strategy meetings; 10,000–50,000 characters.
* **Policy Documents**: Includes State Council policy documents, government work reports, PBOC monetary policy reports; 10,000–50,000 characters.
* **Academic Papers**: Covers monetary policy, foreign reserves, pandemic research, etc.; 10,000–30,000 characters.

<div align="center">
  <img src="https://github.com/valuesimplex/FinLongEval/blob/main/fig/%E6%96%87%E4%BB%B6%E7%B1%BB%E5%9E%8B%E5%88%86%E5%B8%83%E5%9B%BE%E9%A5%BC%E5%9B%BE.png" width="750px" height="500px" alt="Document Type Distribution">
</div>

The figure above shows the distribution of document types in our benchmark. Broker research reports, issuer announcements/prospectuses (including regular reports, issuance documents, and major corporate actions), financial news, and conference transcripts account for 25.4%, 19.3%, 17.9%, and 15.6% respectively—closely mirroring real-world processing needs.

### Question Types

To comprehensively assess LLM capabilities on long financial texts across research, compliance, and investor education scenarios, we designed 12 question categories:

| Question Type          | Task Description                                                                | Financial-Scenario Task Description                                                               |
| ---------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------- |
| Information Extraction | Extract specified information from the text; tests retrieval and extraction.    | Financial institutions need to pull specific details—e.g., issuer fundamentals from a prospectus. |
| Table Extraction       | Identify and extract tables; tests PDF table parsing and 2D data comprehension. | Critical research data often resides in tables, such as financial summaries in periodic reports.  |
| Key Data Extraction    | Precisely locate numerical statistics; tests exact retrieval.                   | Extract metrics like revenue or gross profit from minutes or reports.                             |
| Reading Comprehension  | Deeply analyze and understand text meaning; tests holistic comprehension.       | Analysts may ask for data-driven conclusions—e.g., analyzing a company’s gross margin trends.     |
| Event Analysis         | Reason about events in text; tests logical inference on financial concepts.     | Scenario analysis, such as policy impact or ESG factor inference.                                 |
| Logical Reasoning      | Infer conclusions via multi-step reasoning; tests advanced logical capability.  | Use fundamentals to project future performance or industry trends.                                |
| Keyword Extraction     | Extract thematic keywords; tests summarization.                                 | Quickly identify key topics in conference transcripts.                                            |
| Text Summarization     | Generate concise summaries; tests information condensation.                     | Produce research or policy briefs.                                                                |
| Outline Generation     | Create text outlines; tests structural analysis.                                | Aid writing, e.g., generating an outline for a government report.                                 |
| Speaker Identification | Distinguish speakers in dialogue; tests multi-party comprehension.              | Conference calls involve multiple participants—accurate role identification is essential.         |
| Trap Questions         | Assess hallucination severity; tests factual fidelity.                          | In finance, accuracy is critical—identify when models invent information not in the source.       |
| Calculation Questions  | Perform mathematical computations; tests numeric reasoning.                     | Analysts may request derived metrics, such as computing financial ratios from reported data.      |

<div align="center">
  <img src="https://github.com/valuesimplex/FinLongEval/blob/main/fig/%E9%97%AE%E9%A2%98%E7%B1%BB%E5%9E%8B%E5%88%86%E5%B8%83%E5%9B%BE.png" width="450px" height="350px" alt="Question Type Distribution">
</div>

The above chart shows that reading comprehension, information extraction, and logical reasoning dominate (26%, 25%, 13%), while table extraction, event analysis, summarization, and trap questions each account for about 7%—reflecting our initial industry survey.

### Distribution of Document Lengths

<div align="center">
  <img src="https://github.com/valuesimplex/FinLongEval/blob/main/fig/%E6%96%87%E6%A1%A3%E9%95%BF%E5%BA%A6%E5%88%86%E5%B8%83%E5%9B%BE.png" width="500px" height="280px" alt="Document Length Distribution">
</div>

Over 80% of documents exceed 10,000 characters, far surpassing typical financial benchmarks. Over 40% exceed 25,000 characters—longer than the context window of most commercial LLMs. We even include documents exceeding 500,000 characters (approximately 500 pages). These figures underscore that real financial files often span tens or hundreds of thousands of characters, making long-document capabilities indispensable for LLM adoption in finance.

### Reference Answer Generation

We adopted a “2+1+1” workflow for reference answer creation. First, two state-of-the-art LLMs (GPT-4 and Claude2) each generate an answer based on the question and original document. Next, a human expert reviews and merges these into a coherent draft. Finally, another expert validates and refines this draft against the source document to produce the final reference answer. This human–AI collaboration balances efficiency with high quality, especially as 80% of our questions are open-ended and involve texts of tens of thousands of characters.

<div align="center">
  <img src="https://github.com/valuesimplex/FinLongEval/blob/main/fig/%E8%AF%84%E4%BC%B0%E6%B5%81%E7%A8%8B%E7%A4%BA%E6%84%8F%E5%9B%BE.png" width="600px" height="300px" alt="Evaluation Process Illustration">
</div>

### Sample Data

Below is a preview of our dataset structure—showing primary and secondary document types, file names, question types, questions, and reference answers. For more samples, see the [sample\_data.jsonl folder](https://github.com/valuesimplex/FinLongEval/blob/main/data/sample_data.jsonl).

<details>
  <summary>Click to view the table</summary>

| Primary Type    | Secondary Document Type        | File Name                                                                                               | Question Type         | Question                                                                                                                                                                                                                                                                                   | Reference Answer                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| --------------- | ------------------------------ | ------------------------------------------------------------------------------------------------------- | --------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Research Report | Equity Research Report         | Tonghuashun (300033) Rides the AI Tailwind, Sailing Forward in Financial Information Services           | Table Extraction      | Extract Tonghuashun’s financial summary for 2021–2025. The metrics are revenue, net profit attributable to the parent company, earnings per share, and price-to-earnings ratio. Requirement: output in table format. Convert the unit from millions of RMB to hundreds of millions of RMB. | “Tonghuashun’s financial summary for 2021–2025 (in RMB hundred millions) is as follows: Financial summary (hundred million RMB) Metrics  2021A  2022A  2023E  2024E  2025E  Revenue  35.10  35.59  40.68  45.97  51.32  Net profit attributable to the parent company  19.11  16.91  20.51  22.29  24.49  Earnings per share (RMB)  3.56  3.15  3.82  4.15  4.55  Price-to-earnings ratio  40.61  31.30  59.48  54.74  49.83  Main points: 1. Data for 2021–2022 are from company reports. 2. Data for 2023–2025 are forecasts. 3. Units have been converted to RMB hundred millions. 4. Metrics include revenue, net profit attributable to the parent company, earnings per share, and price-to-earnings ratio.”                                                                                             |
| Announcement    | Prospective Listing Prospectus | Prospectus of China Electric Port                                                                       | Reading Comprehension | Please provide the issuer’s gross profit margin on its main business over the past three years, analyze the reasons for any changes in margin, and compare it with that of comparable companies.                                                                                           | “China Electric Port’s main business gross profit margins over the past three years are: 2019: 3.72%; 2020: 3.87%; 2021: 3.53%. The margin remained relatively stable during the period. Reasons for changes include: 1. Supply and demand dynamics—upstream supply levels, downstream demand strength, and bargaining power between suppliers and customers impact procurement costs and gross profit in the electronic component distribution industry. 2. Exchange rate fluctuations—dependence on imported high-end components makes margins sensitive to currency movements. Compared to peers, China Electric Port’s margins are lower: 2019: 7.90%; 2020: 7.89%; 2021: 8.87%, likely due to differences in supply chain bargaining power, market positioning, product mix, and operational efficiency.” |
| Research Report | Equity Research Report         | The Electric Vehicle King Competes Globally, Building Core Competitiveness Through Vertical Integration | Trap Question         | BYD’s main business is fuel vehicles. Describe BYD’s fuel vehicle business status.                                                                                                                                                                                                         | “As of March 2022, BYD had begun to discontinue sales of fuel vehicles and shifted its focus entirely to the development and sale of new energy vehicles. Therefore, there is no further detailed information on BYD’s fuel vehicle business in the report, as the company has fully transitioned to new energy vehicles.”                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |

</details>

## An Evaluation Instance

<div align="center">
  <img src="https://github.com/Invariant0502/FinLBench/blob/main/figure/figure9.png" width="600px" height="300px" alt="Evaluation Process Illustration">
</div>

We present an example that includes the entire evaluation process, as shown in the figure above. Initially, we input the question and the original text into the LLMs that are to be evaluated, yielding the model's output. During the evaluation process, for commercial models, we submitted the entire PDF files directly to the LLMs. However, for locally deployed open-source models, we are unable to submit the PDF files directly. Instead, we extract the plain text from the PDFs and input that into the model. Subsequently, we input the generated content, the question, and the assessment prompts into the LLMs used for evaluation, which provides a set of generated scores and reasons. Finally, we integrate all the obtained content with the original text, perform a comparison, and make minor adjustments to the scores to arrive at the final score.

Upon receiving the initial score for this particular instance, we made adjustments due to several discrepancies. The relevance score, as provided by the scoring model, surpassed the designated range of 0 to 1 point, leading us to cap the relevance score at 1 point. The coherence score was justified with the comment, “it fails to explain the economic benefits and impact generated,” which did not correspond to our criteria for coherence. As a result, we revised the coherence score to 2 points. Fidelity, which reflects the model's adherence to the original text of the document, was initially scored without reference to the original text. After comparing the generated answer with the original text, we found that the original did indeed contain similar content. Consequently, we adjusted the fidelity score to 1 point.

## Six-dimensional Evaluation System

- **Relevance (1 point):** The relationship between the generated answer text and the question. Ensuring relevance guarantees that the model provides answers directly related to the financial question, crucial for accurate decision-making.  
  **Expert opinion:** Relevance is the fundamental criterion for evaluation, thus a binary evaluation metric is established for this dimension. The content must first be highly pertinent to the subject before other dimensions can be assessed.

- **Fluency (2 points):** Whether the generated answer text is fluent, with a clear main idea and reasonable grammar. Fluency ensures that the generated financial text is clear and grammatically correct, facilitating ease of understanding.  
  **Expert opinion:** Fluency directly impacts the reader's experience and comprehension. While fluency is important, in the financial domain, the accuracy and utility of the content are more critical. Therefore, fluency is assigned a moderate weight to balance linguistic expression with the quality of information.

- **Coherence (2 points):** Evaluate whether the answer text itself is in line with common sense and logical, and whether the text paragraphs are organized reasonably. Coherence is vital for maintaining logical and organized reasoning in complex financial analyses and reports.  
  **Expert opinion:** Coherence ensures clarity in the logic and structure of content. While important, in the financial domain, its significance is still lower than that of practicality and consistency, as the latter more directly impact decision-making quality.

- **Helpfulness (5 points):** Whether the generated answer text meets the user’s request and provides necessary information (with a focus on whether there are clear conclusions and whether detailed data support is provided). Helpfulness assesses whether the model offers valuable insights and detailed data that aid in financial decision-making.  
  **Expert opinion:** Usefulness directly reflects the practical value and applicability of the content. As this is the core objective of the evaluation, it is assigned the highest weight.

- **Consistency (4 points):** Whether the answer text correctly answers the question. Consistency ensures that all generated data and conclusions align logically, preventing conflicting financial insights.  
  **Expert opinion:** Consistency is a critical factor in ensuring the credibility of content. Information in the financial sector demands high levels of accuracy and consistency, thus it is given significant weight in evaluations.

- **Fidelity (1 point):** Whether the generated answer text is faithful to the original text. Fidelity ensures the model’s output accurately reflects the original financial data, preserving accuracy and reliability.  
  **Expert opinion:** Fidelity is a fundamental requirement for ensuring the accuracy of content. In the financial sector, while the importance of fidelity cannot be overlooked.

## Prompt Settings

### System Prompt

This section presents a simplified version of the system prompt, which is used to guide the model in generating responses and scoring them based on six evaluation criteria. The complete version of the system prompt can be found in the attached document.

Relevance: The relationship between the question and the answer.  
Scoring: 0 points – irrelevant; 1 point – related to the question.

Fluency: The clarity and grammar of the answer text.  
Scoring: 0 points – unclear or has errors; 1 point – understandable but has issues; 2 points – clear and grammatically correct.

Coherence: The logical structure and consistency of the answer text.  
Scoring: 0 points – illogical or inconsistent; 1 point – consistent with common sense; 2 points – logical and well-organized.

Helpfulness: The detail, clarity, and alignment with the question.  
Scoring: 0–5 points based on detailed criteria, including data, logical flow, and coverage of all aspects.

Consistency: The alignment of the answer text with the reference answer.  
Scoring: 0–4 points based on the level of consistency and accuracy.

Fidelity: Whether the answer is faithful to the reference answer.  
Scoring: 1 point – faithful; 0 points – includes extra or irrelevant information.

### General Tasks Evaluation Prompt

The general tasks prompt is used to guide the system in evaluating the generated model responses based on the reference answer. It includes how to compare the generated answer with the reference answer and provide specific scores and reasons. **Only the general tasks prompt needs to be combined with the system prompt for proper evaluation.**

Task Description: Based on the given question, reference answer, and the answer to be evaluated, score the evaluated answer according to 6 criteria: relevance, fluency, coherence, usefulness, consistency, and fidelity. Give an integer score first, followed by an explanation.

Question:  
{question}

Reference Answer:  
{reference_answer}

Answer to be Evaluated:  
{generated_answer}

Output Format Example:  
Relevance: X points  
Reason: [Explanation]

Fluency: X points  
Reason: [Explanation]  
...

### Trap Issues Evaluation Prompt

This section presents the prompt used to evaluate whether the generated model answer contains fabricated content. It helps identify any potential fabrication in the model's generated answer. **This prompt is used to assess the trustworthiness of generated content.**

Task description: Based on the given question, reference answer, and generated model answer, determine whether the generated answer contains fabrication and provide reasons.

Question:  
{question}

Reference Answer:  
{reference_answer}

Generated Model Answer:  
{generated_answer}

Output format:  
Fabricated/Not Fabricated  
Reason: [Explanation]

### Data Calculation Evaluation Prompt

This section presents the prompt used to evaluate whether the generated model's answer is accurate in terms of data calculation, ensuring that the calculation result is completely consistent with the reference answer. **It focuses on verifying the correctness of calculations in the model's responses.**

Task description: Based on the given data calculation problem, reference answer, and generated model answer, evaluate whether the generated answer is calculated correctly. The final calculation result must be exactly consistent to be considered correct.

Question:  
{question}

Reference Answer:  
{reference_answer}

Generated Answer:  
{generated_answer}

Output format:  
Correct/Incorrect  
Reason: [Explanation]

## Methodology for Dataset Construction

### Financial Long Document Dataset Construction

All financial long documents in this dataset are sourced from the information disclosure files of the largest stock exchange in China, the Shanghai Stock Exchange. In determining the eight document types included in FinLBench, the selection process was guided by both specific industry needs and broader applicability. The aim was to create a comprehensive dataset that reflects the diverse range of documents encountered in financial analysis and decision-making processes. Here's a breakdown of the rationale behind the selection:

- **Research Report:** These documents, including individual stock reports, industry reports, macroeconomic reports, and quantitative analysis reports, are fundamental to investment research. Their inclusion is based on the specific need for detailed analysis in investment decisions, with text lengths ranging from 10,000 to 30,000 words.
- **Company Major Matters:** Primarily including equity incentive announcements, these documents are crucial for understanding corporate governance and employee incentive mechanisms. By analyzing equity incentive announcements, investors and analysts can gain insights into how a company motivates and retains key talent, which is essential for assessing the company's long-term strategy and potential growth. The document length is approximately between 300,000 and 500,000 words.
- **Financial News:** Covering financial commentary and morning reports from mainstream financial media, these documents are essential for staying updated with market trends and news. Their shorter length, between 3,000 and 10,000 words, makes them suitable for quick analysis and decision-making.
- **Conference Roadshow:** Including earnings calls and strategy meetings, these documents provide insights into company strategies and market positioning. Their text length, ranging from 10,000 to 50,000 words, reflects the detailed discussions typical of such events.
- **Policy Document:** Encompassing State Council policy documents, government work reports, and central bank monetary policy reports, these documents are vital for understanding regulatory and economic environments. Their inclusion is based on the need for policy analysis, with text lengths between 10,000 and 50,000 words.
- **Academic Paper:** Covering topics like monetary policy, foreign exchange reserves, and pandemic research, these documents provide in-depth theoretical insights into financial issues. Their text length, ranging from 10,000 to 30,000 words, supports detailed academic analysis.
- **Periodic Report:** These documents, including individual stock reports, industry reports, macroeconomic reports, and quantitative analysis reports, are fundamental to investment research. Their inclusion is based on the specific need for detailed analysis in investment decisions, with text lengths ranging from 10,000 to 30,000 words.
- **Company Issuance:** This category includes IPO prospectuses, bond prospectuses, fund prospectuses, annual reports, earnings forecasts & bulletins. These documents are crucial for understanding corporate actions and financial health, with most texts ranging from 100,000 to 300,000 words, reflecting their comprehensive nature.

The selection of these document types ensures that FinLBench addresses both specific industry requirements and broader analytical needs, making it a versatile tool for financial professionals and researchers. By covering a wide range of document types, FinLBench is designed to be applicable across various financial scenarios, enhancing its utility and relevance in the field.

### Expert-Driven Question Construction

We adopted expert-driven methods for question construction in FinLBench to ensure that the dataset aligns with practical financial scenarios and addresses real-world analytical needs. This approach leverages domain expertise to create questions that are precise, relevant, and representative of key challenges in financial analysis. Specifically, the assessment objectives and business scenario descriptions for each question type are shown in Table \[tab:financial_tasks\].

#### Construction Principles

In designing the benchmark, we aimed to ensure that the evaluation dataset originates from frontline financial business scenarios and serves as a robust tool across various use cases. To achieve this, we adhered to the following principles:

- **Scenario Alignment:** Questions are crafted to reflect real challenges and inquiries faced by financial analysts in their day-to-day work.
- **Domain Expertise:** Each question is meticulously designed by financial experts, ensuring accuracy, contextual relevance, and analytical depth.
- **Breadth and Relevance:** The questions are structured to address a wide range of financial scenarios, representing typical needs and diverse problem types within the industry.

#### Collaborative Development Process

We developed the questions through close collaboration with financial experts from leading securities firms. By engaging with professionals from both business and IT departments, we ensured that the constructed questions resonate with real-world financial practices and challenges. This process ensures that the questions are not only theoretically sound but also practically applicable, forming a strong foundation for evaluating performance in financial long-document analysis.

<div align="center">
  <img src="https://github.com/Invariant0502/FinLBench/blob/main/figure/figure14.png" width="800px" height="250px" alt="Evaluation Process Illustration">
</div>

### Constructing Questions Using LLMs

We have also implemented the method of constructing questions in FinLBench using LLMs. By using the prompt as a template to generate questions using an LLM other than the tested model, we found that LLMs not only have the ability to generate answers based on documents and questions, but also have good performance in constructing questions that meet the requirements. The prompt template is shown in Figure \[fig:template1\]. The financial scenario is a description that informs the LLM of the scenarios in which these questions are raised, including the content or focus that the analyst wants to understand in the document. The question type refers to the type and brief introduction of questions that the LLM is designed for.

To ensure the high quality of the questions posed by the LLM and their inclusion in the dataset, we have had financial experts review and filter the questions raised by the LLM, thereby identifying those that are truly valuable.

<div align="center">
  <img src="https://github.com/Invariant0502/FinLBench/blob/main/figure/figure12.png" width="600px" height="300px" alt="Evaluation Process Illustration">
</div>

We have demonstrated an example of constructing event analysis questions using an LLM, as illustrated in Figure \[fig:examplequescon\]. The first question given by the LLM is valuable in the given scenario and is adopted, while the second question is rejected due to its low relevance and usefulness in the given scenario.

<div align="center">
  <img src="https://github.com/Invariant0502/FinLBench/blob/main/figure/figure13.png" width="600px" height="300px" alt="Evaluation Process Illustration">
</div>

### Hybrid Workflow for Constructing Reference Answers

In constructing the reference answers for the FinLBench evaluation dataset, we employed a "2+1+1" workflow (illustrated in Figure \[fig:workflow\]) to ensure high-quality and reliable answers. For closed-ended questions, where clear answers exist within the document, we directly used the relevant content from the original text as the reference answer. For open-ended questions, which constitute 80% of the dataset and often involve financial documents spanning tens of thousands of words, we adopted a hybrid human-AI approach to balance efficiency and quality.

Specifically, we began by leveraging two state-of-the-art LLMs, ChatGPT 4 and Claude 2, to independently generate two initial answers based on the question and the original financial document. Next, a human expert reviewed these AI-generated answers, validating them against the document content and integrating the best aspects of both into a cohesive and comprehensive response. Finally, a second human expert conducted a thorough review and optimization of the integrated answer, ensuring accuracy, clarity, and alignment with the original document. This finalized answer was used as the reference answer for the evaluation dataset.

The adoption of this workflow stems from the challenges inherent in creating a predominantly subjective question set with significant document length. While direct human authorship would be prohibitively time-consuming, we observed that advanced AI models, with appropriate human oversight, are capable of producing answers that approach human-level quality. This human-AI collaboration not only ensures efficiency but also maintains the high standard required for the FinLBench dataset.


## An Evaluation Instance

<div align="center">
  <img src="https://github.com/Invariant0502/FinLBench/blob/main/figure/figure9.png" width="600px" height="300px" alt="Evaluation Process Illustration">
</div>

We present an example that includes the entire evaluation process, as depicted in Figure \[fig:wide4\]. Initially, we input the question and the original text into the LLMs that are to be evaluated, yielding the model's output. During the evaluation process, for commercial models, we submitted the entire PDF files directly to the LLMs. However, for locally deployed open-source models, we are unable to submit the PDF files directly. Instead, we extract the plain text from the PDFs and input that into the model. Subsequently, we input the generated content, the question, and the assessment prompts into the LLMs used for evaluation, which provides a set of generated scores and reasons. Finally, we integrate all the obtained content with the original text, perform a comparison, and make minor adjustments to the scores to arrive at the final score.

Upon receiving the initial score for this particular instance, we made adjustments due to several discrepancies. The relevance score, as provided by the scoring model, surpassed the designated range of 0 to 1 point, leading us to cap the relevance score at 1 point. The coherence score was justified with the comment, “it fails to explain the economic benefits and impact generated,” which did not correspond to our criteria for coherence. As a result, we revised the coherence score to 2 points. Fidelity, which reflects the model's adherence to the original text of the document, was initially scored without reference to the original text. After comparing the generated answer with the original text, we found that the original did indeed contain similar content. Consequently, we adjusted the fidelity score to 1 point.

## Six-dimensional Evaluation System

- **Relevance (1 point):** The relationship between the generated answer text and the question. Ensuring relevance guarantees that the model provides answers directly related to the financial question, crucial for accurate decision-making.  
  **Expert opinion:** Relevance is the fundamental criterion for evaluation, thus a binary evaluation metric is established for this dimension. The content must first be highly pertinent to the subject before other dimensions can be assessed.

- **Fluency (2 points):** Whether the generated answer text is fluent, with a clear main idea and reasonable grammar. Fluency ensures that the generated financial text is clear and grammatically correct, facilitating ease of understanding.  
  **Expert opinion:** Fluency directly impacts the reader's experience and comprehension. While fluency is important, in the financial domain, the accuracy and utility of the content are more critical. Therefore, fluency is assigned a moderate weight to balance linguistic expression with the quality of information.

- **Coherence (2 points):** Evaluate whether the answer text itself is in line with common sense and logical, and whether the text paragraphs are organized reasonably. Coherence is vital for maintaining logical and organized reasoning in complex financial analyses and reports.  
  **Expert opinion:** Coherence ensures clarity in the logic and structure of content. While important, in the financial domain, its significance is still lower than that of practicality and consistency, as the latter more directly impact decision-making quality.

- **Helpfulness (5 points):** Whether the generated answer text meets the user’s request and provides necessary information (with a focus on whether there are clear conclusions and whether detailed data support is provided). Helpfulness assesses whether the model offers valuable insights and detailed data that aid in financial decision-making.  
  **Expert opinion:** Usefulness directly reflects the practical value and applicability of the content. As this is the core objective of the evaluation, it is assigned the highest weight.

- **Consistency (4 points):** Whether the answer text correctly answers the question. Consistency ensures that all generated data and conclusions align logically, preventing conflicting financial insights.  
  **Expert opinion:** Consistency is a critical factor in ensuring the credibility of content. Information in the financial sector demands high levels of accuracy and consistency, thus it is given significant weight in evaluations.

- **Fidelity (1 point):** Whether the generated answer text is faithful to the original text. Fidelity ensures the model’s output accurately reflects the original financial data, preserving accuracy and reliability.  
  **Expert opinion:** Fidelity is a fundamental requirement for ensuring the accuracy of content. In the financial sector, while the importance of fidelity cannot be overlooked.

## Prompt Settings

### System Prompt

This section presents a simplified version of the system prompt, which is used to guide the model in generating responses and scoring them based on six evaluation criteria. The complete version of the system prompt can be found in the attached document.



## Evaluation Methods for Financial Long-Document Processing Ability

### Evaluation Dimensions

| Evaluation Dimension | Meaning                                                                                  | Score Range |
| -------------------- | ---------------------------------------------------------------------------------------- | ----------- |
| Relevance            | Assesses whether the answer is on-topic and addresses the user’s question.               | 0–1         |
| Helpfulness          | Measures whether the answer satisfies the request, provides clear conclusions, and data. | 0–5         |
| Fluency              | Evaluates sentence smoothness, clarity of main ideas, and grammatical correctness.       | 0–2         |
| Coherence            | Checks logical consistency and organization; absence of contradictions.                  | 0–2         |
| Consistency          | Compares the generated answer with the reference; key data must match exactly.           | 0–4         |
| Faithfulness         | Assesses fidelity to the source document; identifies hallucinations.                     | 0–1         |

### Evaluation Process

Most tasks in our benchmark are open-ended, requiring a human–AI hybrid evaluation. For closed-ended questions, we use automatic metrics such as ROUGE to measure n-gram overlap between model outputs and references. However, open-ended questions often involve diverse, high-level semantics that automatic metrics cannot fully capture. Thus, we rely on human experts for final scoring:

1. **Initial Machine Scoring**: GPT-4 scores each model-generated answer on the six dimensions.
2. **Independent Expert Scoring**: Multiple human experts independently score each answer, referencing the machine scores.
3. **Aggregation**: We aggregate these scores to produce the final evaluation.

<div align="center">
  <img src="https://github.com/valuesimplex/FinLongEval/blob/main/fig/%E8%AF%84%E4%BC%B0%E6%B5%81%E7%A8%8B%E7%A4%BA%E6%84%8F%E5%9B%BE.png" width="600px" height="300px" alt="Evaluation Workflow">
</div>

## Evaluation Results

### Evaluation Subjects

We evaluated eight commercial long-document assistance products based on large models: overseas leaders Claude2, ChatGPT4, ChatPDF, and five domestic tools (referred to here as Tool\_A through Tool\_E). These tools were selected for their widespread use in finance. To avoid potential commercial disputes, we anonymize the domestic products. For full details, academic researchers may contact the project team for the comprehensive report.

### Overall Evaluation Analysis

| Tool Name | Relevance | Fluency | Coherence | Helpfulness | Consistency | Faithfulness | Total Score |
| --------- | --------- | ------- | --------- | ----------- | ----------- | ------------ | ----------- |
| Claude2   | 0.99      | 2.00    | 1.95      | 4.14        | 2.90        | 0.82         | 12.80       |
| ChatGPT4  | 0.96      | 2.00    | 1.93      | 3.95        | 2.94        | 0.81         | 12.59       |
| Tool\_A   | 0.98      | 2.00    | 1.93      | 3.85        | 2.87        | 0.76         | 12.55       |
| Tool\_E   | 0.98      | 2.00    | 1.92      | 3.84        | 2.57        | 0.75         | 12.06       |
| Tool\_B   | 0.95      | 2.00    | 1.70      | 3.06        | 2.16        | 0.57         | 10.44       |
| Tool\_C   | 0.90      | 1.99    | 1.54      | 2.52        | 1.82        | 0.51         | 9.28        |
| Tool\_D   | 0.90      | 1.99    | 1.64      | 2.72        | 1.76        | 0.48         | 9.49        |
| ChatPDF   | 0.84      | 1.99    | 1.58      | 2.44        | 1.60        | 0.45         | 8.90        |

Key takeaways:

* **Claude2 and ChatGPT4 remain the top performers**, forming the first tier. Domestic tools vary more, with some approaching their performance. Surprisingly, **ChatPDF (GPT-3.5 based) scored lowest**, highlighting that long-document processing depends heavily on upstream modules like segmentation and retrieval, not just the base model.
* Nearly all tools achieve high **relevance** and **fluency**, indicating that understanding the question and producing smooth text are no longer major hurdles.
* **Coherence** and **helpfulness** drive major performance differences; scores above 1.7 (coherence) and 3.6 (helpfulness) are considered business-viable, and some domestic tools already meet these thresholds.
* **Consistency** and **faithfulness** reflect key-data accuracy and hallucination levels; even Claude2 does not reach a perfect 4 in consistency, suggesting all tools still fall short in high-precision financial contexts.

### Analysis by Document Type

<div align="center">
  <img src="https://github.com/valuesimplex/FinLongEval/blob/main/fig/%E8%AF%84%E6%B5%8B%E5%AF%B9%E8%B1%A1%E5%BE%97%E5%88%86-%E6%96%87%E6%A1%A3.png" width="650px" height="220px" alt="Score by Document Type">
</div>

* For **major corporate actions** and **policy documents**, all tools perform comparably well, meeting business-usable standards, since these tasks focus on extraction and comprehension.
* For **financial news** and **conference transcripts**, tool performance diverges noticeably. Claude2, ChatGPT4, and top domestic tools handle these well, but others (including ChatPDF) struggle, mainly due to the need for complex event analysis, logical reasoning, and speaker identification over long contexts.

### Analysis by Question Type

<div align="center">
  <img src="https://github.com/valuesimplex/FinLongEval/blob/main/fig/%E8%AF%84%E6%B5%8B%E5%AF%B9%E8%B1%A1%E5%BE%97%E5%88%86-%E9%97%AE%E9%A2%98.png" width="650px" height="220px" alt="Score by Question Type">
</div>

* **Logical reasoning** and **event analysis** show the greatest tool gaps, driven by differences in core reasoning capabilities.
* **Long-context tasks** such as speaker identification and summarization also vary widely, reflecting limitations of model context windows and retrieval coverage.
* **Information extraction** and **key data extraction** are well-handled by all tools, demonstrating maturity in targeted retrieval tasks.

### Analysis of Calculation-Type Questions

<div align="center">
  <img src="https://github.com/valuesimplex/FinLongEval/blob/main/fig/%E6%95%B0%E6%8D%AE%E8%AE%A1%E7%AE%97.png" width="817px" height="457px" alt="Calculation Performance">
</div>

Except for ChatGPT4, other tools perform poorly on numeric computations. Claude2 and some domestic tools execute the calculation steps correctly but err in final results. We recommend integrating external computation engines (e.g., Code Interpreter) for high-precision financial calculations, with LLMs orchestrating the workflow.

### Evaluation on Trap Questions

| Tool             | Tool D | ChatGPT4 | Tool C | Tool B | Claude2 | Tool A | ChatPDF | Tool E |
| ---------------- | ------ | -------- | ------ | ------ | ------- | ------ | ------- | ------ |
| Fabrication Rate | 80%    | 45%      | 60%    | 70%    | 42%     | 65%    | 28%     | 35%    |

Even top tools (Claude2, ChatGPT4) fail 40% of trap questions, and most domestic tools exceed 60% failure. For high-integrity financial scenarios, hallucination mitigation remains a major challenge.

### Document Response Evaluation

| Tool          | Tool A | ChatGPT4 | Tool C | Tool B | Tool D | Tool E | ChatPDF | Claude2 |
| ------------- | ------ | -------- | ------ | ------ | ------ | ------ | ------- | ------- |
| Response Rate | 100%   | 100%     | 98%    | 98%    | 98%    | 92%    | 90%     | 63%     |

From a usability perspective, most domestic tools handle financial documents compatibly, while Claude2 fails to parse or respond to 40% of files.

### Summary

* **Core LLM capabilities remain paramount**; built-for-finance enhancements allow some domestic tools to approach or even exceed ChatGPT4 and Claude2 on specific tasks.
* Understanding the question and generating fluent text are largely solved.
* **Hallucinations remain unsolved**; high-fidelity financial use cases demand combined product and technical strategies.
* **Numeric computations** should rely on external interpreters, with LLMs orchestrating and integrating outputs.

## How to Obtain the Complete Benchmark Set

Please contact us via either of the following emails:

* **Financial Big Data Security Lab, BUPT**: [yangzl@bupt.edu.cn](mailto:yangzl@bupt.edu.cn)
* **EntropyReduce AI Lab**: [liyu@entropyreduce.com](mailto:liyu@entropyreduce.com)

When reaching out, please provide:

```
- Organization Name:
- Contact Person:
- Contact Email:
- Use Case:
```

## Citation

If this project benefits your research, please cite:

```
@online{FinLongEval,
  author = {Xinguang Jiang, Sihan Hu, Dingfu Yu, Yuhao Zhang, Zhongliang Yang, Yu Li, Linna Zhou and Valuesimplex AI Lab},
  title  = {FinLongEval},
  url    = {https://github.com/valuesimplex/FinLongEval},
  year   = {2023},
  month  = {Dec}
}
```


## 参考
1、[Fin-Eval 金融领域中文语言专业数据评测集](https://github.com/alipay/financial_evaluation_dataset)

2、[L-Eval: Instituting Standardized Evaluation for Long Context Language Models](https://github.com/OpenLMLab/LEval/)

3、[FinEval: A Chinese Financial Domain Knowledge Evaluation Benchmark for Large Language Models](https://github.com/SUFE-AIFLM-Lab/FinEval)

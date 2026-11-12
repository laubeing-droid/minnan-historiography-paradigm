# 两个实际项目教会了什么

核查版本固定于2026年11月12日：书稿仓 `a64f9e5ffdfcafc10a6961be5f5df595d1e72bd8`；文献仓 `5956415589703934a5707ec8cdcc1e1e5a9f07a6`。下列是从公开材料中提炼的经验，不表示本范式已在新项目完整验证。

## 《一种闽南文史的未来：基于人工智能与现代研究方法》

[第20章来源核读](https://github.com/laubeing-droid/minnan-historiography-book/blob/a64f9e5ffdfcafc10a6961be5f5df595d1e72bd8/chapters/ch20/SOURCE_REVIEW.md)展示了怎样处理一项真实缺件：市级2010年公报缺完整脚注，继续查同次省级原公报补常住人口定义，再与2020年市级说明对照。不是因页面缺注就放弃，也不是替原件编出脚注。

两期11个汇总分区分别加总，避免开发区、台商区从属行重复计算。这个检查支持全市公布人数的有限描述性比较，不等于每段行政边界、调查误差或人口迁移机制均已核清。另一位AI核查者的限定交叉复核，也不称作人类全书学术审校。

[代码执行审计](https://github.com/laubeing-droid/minnan-historiography-book/blob/a64f9e5ffdfcafc10a6961be5f5df595d1e72bd8/docs/CODE_EXECUTION_AUDIT.md)记录了实际运行中暴露的问题，包括评分被整数截断、替代关系循环或跨对象、空容器被字符串化后当成文本等。它们说明“附了程序”与“程序经过检查”不同，示例输入通过也不能替代异常输入和回归测试。这里转述源仓记录，没有在本仓重跑原程序。

值得迁移的是：问题、来源、程序、运行记录和正文解释一起回查。缺件用可核的其他材料补证时，说明替代材料能回答哪一部分，仍保留原缺件记录。

## 闽南—西班牙文献项目

这个项目已经留下真实交付、改进复用和多任 Agent 接班的记录。这里把三条线接起来，不另造一个演示项目，也不把已有施工降格成“还缺一个实例”。

### 1. 从盲读到校对交付

[一份实际盲读批次](https://github.com/laubeing-droid/minnan-spanish-corpus/blob/5956415589703934a5707ec8cdcc1e1e5a9f07a6/literature/workspace_m2_dhs834/raw_blind/raw_blind_0845-0859.json) → [逐页封存清单](https://github.com/laubeing-droid/minnan-spanish-corpus/blob/5956415589703934a5707ec8cdcc1e1e5a9f07a6/literature/workspace_m2_dhs834/BLIND_READ_MANIFEST.json) → [校对问题队列](https://github.com/laubeing-droid/minnan-spanish-corpus/blob/5956415589703934a5707ec8cdcc1e1e5a9f07a6/literature/workspace_m2_dhs834/COLLATION_QUEUE.json) → [校对工作包](https://github.com/laubeing-droid/minnan-spanish-corpus/blob/c14d3968b59bf5045bc60bb6def5ee009606829c/collation_workbench/INDEX.md) → [D1 原稿转写本](https://github.com/laubeing-droid/minnan-spanish-corpus/blob/5956415589703934a5707ec8cdcc1e1e5a9f07a6/literature/deliverables/book1/01_原稿转写本.md)，构成可以逐步回查的交付链。

工作包组织了1,103页：884页带校对问题、53页无该类标记、166页只有M1成果。D1汇集937页封存转写和166页暂列内容，是**校对前快照**。这是真实交付，不是全量学术验收；无问题标记、哈希匹配、文件齐备，都不能证明每个字读对，更不能代表22个来源全部校完。接手者应从具体问题和保留的原稿继续，而不是从一份“全部完成”声明重新开始。

可迁移的是这条关系：每份交付能找到输入、处理结果、未决问题和下一位接手者的任务。不要把本项目页数、字段和声调码变成所有研究的格式。

### 2. 一次确实用于后续批次的改进

[LESSONS 的 L4](https://github.com/laubeing-droid/minnan-spanish-corpus/blob/5956415589703934a5707ec8cdcc1e1e5a9f07a6/docs/LESSONS.md)和[项目史第三节](https://github.com/laubeing-droid/minnan-spanish-corpus/blob/5956415589703934a5707ec8cdcc1e1e5a9f07a6/docs/PROJECT_HISTORY.md)记录了同一条改进：PART 2 的396–399页是现代分册页，却因零词条触发“每页至少3条”的检查。问题不在于漏读，而在于检查把所有物理页都当作辞典页。

处理方法是辨认页面类别，登记 MODERN_FRONT_MATTER / BLANK，在合并和统计时分别处理，并保留[非辞典页记录](https://github.com/laubeing-droid/minnan-spanish-corpus/blob/5956415589703934a5707ec8cdcc1e1e5a9f07a6/literature/workspace_m2_dhs834/non_lexicographic_pages.json)。项目史随后记录，PART 3 的769–772页复用了这套分类处理。这就是“本批发现错误 → 改工艺与适用条件 → 留下记录 → 后批复用”的真实实例，不必另造一段RSI演示。

这里依据的是公开项目史、教训和保存的分类记录，本仓没有重跑历史批次。它支持一次具体改进得到后续使用，不证明整个自改进系统已经全自动闭合。声调检查虽另有代码及测试，但本次没有核到其修订后足够的盲读批次证据，不能拿它代替这条已记录的后批复用链。相关实现和反例另见[RSI实现证据](RSI_EVIDENCE.md)。

验收规则也可能有错，但不能由施工者为了通过而悄悄放宽。工艺修改与标准变更应分开，涉及标准时须说明审查、批准、适用版本和旧成果处置。

### 3. 多任 Agent 已经接班，不再重复安排演示

[项目史](https://github.com/laubeing-droid/minnan-spanish-corpus/blob/5956415589703934a5707ec8cdcc1e1e5a9f07a6/docs/PROJECT_HISTORY.md)记载了 Codex、Gemini 与后续施工方的工作；[接班施工指令](https://github.com/laubeing-droid/minnan-spanish-corpus/blob/5956415589703934a5707ec8cdcc1e1e5a9f07a6/ZCODE_GLM_全自动执行指令.md)、上述批次与交付件，以及[Agent使用说明](https://github.com/laubeing-droid/minnan-spanish-corpus/blob/5956415589703934a5707ec8cdcc1e1e5a9f07a6/docs/AGENT_GUIDE.md)，提供了角色更替、工序说明和接续产物的具体入口。

可提炼的交接要求是：先看当前范围和保护区，再核版本、来源、已做与未做，最后接手明确的工作包。历史指令中的完成宣称要与后来发现的缺陷对读，不能因为文件名写着“全自动”就把它当作现行验收结论。

这些材料支持“已有多任 Agent 接班施工”。它们不能证明接手者从未接触先前对话、没有本地资料，或仅凭公开仓完成受控盲试；原扫描材料也不都公开。因此不把它叫作“零上下文测试”。没有这种严格测试的证据，不等于没有实际接班经验。

## 半成品研究控制器的设计经验

作者另行授权提炼的一项未公开、未完成的研究控制器，提出了几个值得保留的设计：分开材料原有陈述、推导关系与解释假说；保留模糊年代、人物身份疑问和相互冲突的记载；计数只针对明确限定的材料集合；“没有发现”不等于“不存在”；解释候选仍交由人判断。

这里仅转述获准公开的方法，不提供私有代码、文档原文或私人材料，也不链接受限仓库。它尚是半成品，本轮没有实跑，不声称生产可用或RSI已验证。OCR、爬虫、数据库及人物地名知识库等能力不能从这些设计中推定已经存在。

此处只保留方法经验，不计划接入或继续建设原控制器；本模板不依赖该项目。

## 本仓仍要接受实际检验

把经验整理成模板只是起点。下一项研究采用哪个版本，哪些栏目真正有用，哪些增加负担，都要通过实际项目记录。模板改版不自动改变原项目，也不继承原项目的验收结果。

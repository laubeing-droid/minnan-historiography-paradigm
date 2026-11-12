# RSI 从哪里来，核到哪里

提炼日期：2026年11月12日。来源为公开的 `laubeing-droid/minnan-spanish-corpus`，固定到提交 `5956415589703934a5707ec8cdcc1e1e5a9f07a6`。源仓作者与贡献者的署名保留在其 Git 历史及文档中；本仓按 CC BY-NC-SA 4.0 重新组织为研究模板，没有搬运扫描件、封存数据或私人对话。

## 已有一次真实的后批复用

文献仓的L4事故已形成具体闭环：396–399页现代分册页被辞典页最低词条数误伤，随后建立页面分类与登记，769–772页再出现同类情况时复用。公开项目史、教训和分类记录的固定版本见[真实项目三条线](REPOSITORY_EXPERIENCE.md#2-一次确实用于后续批次的改进)。这是已有实例，不需要重新安排一个示范项目；本仓没有重演其历史运行，也不将它扩称为全自动RSI系统。

## 能找到具体实现的三条线

| 失败与教训 | 实现位置 | 本次核到的范围 | 不能由此推出 |
|---|---|---|---|
| L18/L22：非规范调标漏过检查 | [pipeline](https://github.com/laubeing-droid/minnan-spanish-corpus/blob/5956415589703934a5707ec8cdcc1e1e5a9f07a6/literature/tools/zcode_m2_pipeline.py) 的 `normalize_tone_list` | 读取实现，并对隔离的纯函数做合法、非法输入测试 | 不是全串严格白名单，也不证明调号读对了 |
| L20：合并成果中存在空壳栏位 | [空壳审计器](https://github.com/laubeing-droid/minnan-spanish-corpus/blob/5956415589703934a5707ec8cdcc1e1e5a9f07a6/literature/tools/m1_hollow_audit.py)及源仓保存的 `M1_HOLLOW_BACKFILL_QUEUE.json` | 检查程序及现存队列，队列为 5,108 条、305 页；本次未执行会写队列的扫描器 | 不表示缺失内容已经补齐 |
| L3/L20：页位判断与汇总可能遗漏 | pipeline 的缺口状态检查，以及 [gatekeeper](https://github.com/laubeing-droid/minnan-spanish-corpus/blob/5956415589703934a5707ec8cdcc1e1e5a9f07a6/architect_gatekeeper.py) 的覆盖并集检查 | 确认可找到相应检查实现 | 页位齐全不等于转写或释义验收通过 |

以上数字仅用于说明这个固定版本的证据范围，不是新项目的阈值。教训条目的历史叙述见 [LESSONS](https://github.com/laubeing-droid/minnan-spanish-corpus/blob/5956415589703934a5707ec8cdcc1e1e5a9f07a6/docs/LESSONS.md)，应与程序和保存的产物一起读，不把后来写出的事故总结自动当作当时完整运行记录。

### 一个没有被掩盖的反例

纯函数测试中，`T03` 可归一，`無號/輕聲` 与 `chun=T03[疑]` 被拒绝，但 `T03 arbitrary trailing words` 仍会按前缀归一为 T03。代码检查了首个空白分隔项，因此会吞掉尾部任意文字。源仓这项改进有实际作用，但“全串严格白名单已经闭合”不成立。

本次只记录这个边界，没有修改源仓程序或既有成果。若要修正，应在源项目另立具体改动，补尾部非法输入及合法历史标签的回归测试，避免修补时误拒旧格式。

## 只有局部实现证据的整体循环

[METHODOLOGY 第6节](https://github.com/laubeing-droid/minnan-spanish-corpus/blob/5956415589703934a5707ec8cdcc1e1e5a9f07a6/docs/METHODOLOGY.md)描述失败、教训、人工编译、后续运行的循环，并出现 `AmendWorkflow`、`scanOutside`、`outsideIssue` 等工作流名称。本次核读未找到可以独立复现整套编排的对应脚本，不能据此宣称整个循环已自动运行或已全量验收。

源仓也明确把工作流改进与门禁修订分开，后者走 [GATE_AMENDMENT_PROTOCOL](https://github.com/laubeing-droid/minnan-spanish-corpus/blob/5956415589703934a5707ec8cdcc1e1e5a9f07a6/docs/GATE_AMENDMENT_PROTOCOL.md)。本模板保留这项责任区分，但不复制原项目的角色名称、批次数量及数字限制。

## 文件完整性不是学术结论

本次只读核对 M2 清单所列 937 页文件，937 项 SHA-256 与清单匹配。它说明所检查的文件字节与清单记录一致，不证明清单原本正确、读字正确或翻译完整。工程状态、人工复核和研究结论应分别报告。

[源仓更新日志](https://github.com/laubeing-droid/minnan-spanish-corpus/blob/5956415589703934a5707ec8cdcc1e1e5a9f07a6/CHANGELOG.md)保存了后续修订和运行结果的自述。本仓将这类记录与本次直接检查分开，不把所有历史结果重新声称为本次执行，也不把源仓整个项目标为完成。

## 本模板的验证边界

本仓交付的是从真实项目提炼的文档模板。源仓已有实际交付、改进复用和多任Agent接班；不能再把这三项说成尚待从零建立。尚未证明的是本模板在不同研究类型中完整迁移的效果，以及零上下文、仅凭公开资料的受控试用。它没有自动执行器或全自动改码、独立验收系统。今后在用户实际开展的新研究中记录采用效果即可，不为证明模板而额外造一个项目。

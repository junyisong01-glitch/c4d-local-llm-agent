# 宋俊毅 C4-D Agent 技能

> 本地大模型 Agent 的「技能」说明与使用手册
> 设备：Apple M5 · 16 GB 统一内存 · 完全离线

## 一、这个 Agent 是什么

一个跑在**本机、无需联网**的对话型大模型 Agent：

| 项 | 内容 |
|---|---|
| 模型 | `gemma4:e4b`（约 9.5 GB，4-bit 量化） |
| 运行框架 | Ollama v0.40.2 + mlx（Metal GPU 加速，100% GPU） |
| 设备 | Apple M5（MacBook Air，16 GB 统一内存，11.8 GiB 显存） |
| 联网 | 不需要，数据不出本机 |

## 二、它具备的技能（真实、可复核）

| 技能 | 说明 | 验证 |
|---|---|---|
| 离线问答 | 断网环境下回答常识/知识类问题 | 见 `宋俊毅_C4D_demo.md` DEMO 1 |
| 多版本生成 | 同一问题按不同侧重点给出多版答案 | 见 `宋俊毅_C4D_demo.md` DEMO 1 |
| 会话记忆 | 多轮对话中记住上文（上下文窗口） | 见 `宋俊毅_C4D_demo.md` DEMO 2 |

## 三、如何安装与使用

```bash
# 1. 启动本地服务
/Applications/Ollama.app/Contents/Resources/ollama serve

# 2. 确认模型在位
/Applications/Ollama.app/Contents/Resources/ollama list

# 3. 对话（交互式）
/Applications/Ollama.app/Contents/Resources/ollama run gemma4:e4b

# 4. 或走 API（供 Agent/脚本调用）
curl -s http://localhost:11434/api/chat -d '{"model":"gemma4:e4b","stream":false,"messages":[{"role":"user","content":"你好"}]}'
```

## 四、诚实的边界（现在它还做不到什么）

- ❌ 没有「函数调用 / 工具使用」——这是 L2 加分项（Agent 函数调用），本次未做；
- ❌ 没有「持久化长期记忆」——记忆只在一个会话（上下文窗口）内有效；
- ❌ 没有「地图生成」等复杂能力。

这些不是缺陷，而是我下一步可以去学、去加的方向。当前交付物只**如实呈现已跑通的部分**，不夸大。

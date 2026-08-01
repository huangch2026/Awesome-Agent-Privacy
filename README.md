<h1 align="center">An Information-Flow Survey of Privacy in LLM Agents</h1>

<div align="center">

[![Survey Paper](https://img.shields.io/badge/Paper-Survey-green.svg)](./README.md)
[![MIT License](https://img.shields.io/badge/License-MIT-yellow.svg)](./LICENSE)

</div>

> This repo tracks and organizes papers on **privacy in LLM-based agents**, as a supplementary of our paper, *["An Information-Flow Survey of Privacy in LLM Agents"](./README.md)*.
>
> If you find any work missing or have suggestions, feel free to open a pull request or issue.

---

## Table of Contents

- [Overview](#overview)
- [Exposure Surface Taxonomy](#exposure-surface-taxonomy)
- [Four Stages of the Literature](#four-stages-of-the-literature)
- [Paper List](#paper-list)
  - [Conceptual Framework: Theories, History, and Related Surveys](#conceptual-framework-theories-history-and-related-surveys)
  - [User Context, Norms, and Data Minimization](#user-context-norms-and-data-minimization)
  - [Privacy in RAG and Private Knowledge Retrieval](#privacy-in-rag-and-private-knowledge-retrieval)
  - [Agent Memory and Persistent State](#agent-memory-and-persistent-state)
  - [Tool Use, Action, and Environment Interfaces](#tool-use-action-and-environment-interfaces)
  - [Multiagent Communication and Delegation](#multiagent-communication-and-delegation)
  - [Reasoning, Planning, and Profiling Traces](#reasoning-planning-and-profiling-traces)
  - [Cross-Cutting Privacy Controls and Deployment Substrate](#cross-cutting-privacy-controls-and-deployment-substrate)
  - [Evaluation Landscape and Benchmark Analysis](#evaluation-landscape-and-benchmark-analysis)
- [Citation](#citation)
- [License](#license)

---

## Overview

LLM-based agents are evolving from passive text generators into autonomous systems capable of retrieval, memory, reasoning, tool use, and multiagent collaboration, and are increasingly deployed in high-risk domains such as healthcare, finance, and office work. This autonomy reshapes the privacy landscape.

Unlike most prior work, which treats privacy as secondary to security, this survey studies privacy on its own terms:

> Security asks whether a system has been compromised. Privacy asks whether information flows appropriately — to the right recipient, in the right context, for the right purpose.

We argue that **agent privacy is a property of information flows across the pipeline, not an attribute of any single model**. Across the exposure surfaces this survey reviews, one pattern recurs: *the properties that make agents more capable are precisely those that make them disclose more* — a **utility-leakage coupling** that means robust defenses must architecturally separate capability from disclosure, rather than ask a capable model to behave appropriately.

<p align="center">
  <img src="./assets/overall-exposure.png" width="900" alt="Panorama of LLM agent privacy exposure surfaces"/>
  <br/>
  <em>The information-flow pipeline of an LLM agent and its seven exposure surfaces (A–G).</em>
</p>

---

## Exposure Surface Taxonomy

Rather than organizing by system architecture or threat type, the survey organizes the literature by **seven information-flow exposure surfaces** — the points at which private data can cross from an authorized context into an unauthorized one.

| Surface | Chapter | Core Privacy Issue |
| --- | --- | --- |
| **A. User Context and Norms** | § User Context, Norms, and Data Minimization | Private user context can be disclosed to the wrong recipient, in the wrong social context, or for the wrong purpose |
| **B. Retrieval and Private Knowledge Bases** | § Privacy in RAG and Private Knowledge Retrieval | Private retrieval corpora can be extracted, membership-inferred, or leaked through generated responses |
| **C. Agent Memory and Persistent State** | § Agent Memory and Persistent State | Long-term memory accumulates private information across sessions and can be extracted or poisoned without oversight |
| **D. Tools, Actions, and Environment Interfaces** | § Tool Use, Action, and Environment Interfaces | Tool calls and untrusted environment content create boundaries through which private data can be moved to attacker-controlled sinks via irreversible actions |
| **E. Multiagent Communication and Delegation** | § Multiagent Communication and Delegation | Interagent messages and delegation relationships can overshare private context and enable cascading leakage |
| **F. Reasoning, Planning, and Profiling Traces** | § Reasoning, Planning, and Profiling Traces | Intermediate reasoning, action sequences, and behavioral patterns can expose private information even when the final output is clean |
| **G. Cross-Cutting Deployment Substrate** | § Cross-Cutting Privacy Controls and Deployment Substrate | Model weights, fine-tuning data, and serving infrastructure carry privacy risk beneath the application layer |

<p align="center">
  <img src="./assets/taxonomy.png" width="480" alt="Taxonomy of the survey organized by information-flow exposure surfaces"/>
  <br/>
  <em>How the survey body is organized around the seven exposure surfaces.</em>
</p>

---

## Four Stages of the Literature

The survey traces the literature through four historical stages, from early measurements of training-data memorization to full-stack, cross-surface evaluation:

<p align="center">
  <img src="./assets/literature-evolution.png" width="900" alt="Four stages of LLM agent privacy literature, 2019-2026"/>
  <br/>
  <em>Research focus has expanded from model memorization, through tool injection and retrieval extraction, to memory and multiagent systems, and finally to full-stack, formally grounded controls.</em>
</p>

---

## Paper List

> Papers are formatted as: **_Title_**, Author et al., venue badge.
> Badge colors: `red` = arXiv, `blue` = conference/journal.

### Conceptual Framework: Theories, History, and Related Surveys

* **_AgentSecBench: Measuring Prompt Injection, Privacy Leakage, and Tool-Use Integrity in LLM Agents_**, Alpay et al., [![arXiv](https://img.shields.io/badge/arXiv-2605.26269-red?labelColor=grey)](https://arxiv.org/abs/2605.26269)
* **_MIN-Trust: A Minimum Necessary Information Trust Orchestration Framework for Multi-Agent Collaboration_**, Chen et al., [![ICGAIE](https://img.shields.io/badge/ICGAIE-2026-blue?labelColor=grey)](https://doi.org/10.1145/3813808.3813811)
* **_Trojan Hippo: Weaponizing Agent Memory for Data Exfiltration_**, Das et al., [![arXiv](https://img.shields.io/badge/arXiv-2605.01970-red?labelColor=grey)](https://arxiv.org/abs/2605.01970) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/debesheedas/trojan-hippo-benchmark)
* **_MosaicLeaks:Privacy Risks in Querying-in-the-Open for Deep Research Agents_**, Gurung et al., [![arXiv](https://img.shields.io/badge/arXiv-2605.30727-red?labelColor=grey)](https://arxiv.org/abs/2605.30727) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/ServiceNow/MosaicProject)
* **_Silent Egress: When Implicit Prompt Injection Makes LLM Agents Leak Without a Trace_**, Lan et al., [![arXiv](https://img.shields.io/badge/arXiv-2602.22450-red?labelColor=grey)](https://arxiv.org/abs/2602.22450)
* **_PRAG: End-to-End Privacy-Preserving Retrieval-Augmented Generation_**, Li et al., [![arXiv](https://img.shields.io/badge/arXiv-2604.26525-red?labelColor=grey)](https://arxiv.org/abs/2604.26525) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/BDS-SDU/PRAG)
* **_ADAM: A Systematic Data Extraction Attack on Agent Memory via Adaptive Querying_**, Lyu et al., [![arXiv](https://img.shields.io/badge/arXiv-2604.09747-red?labelColor=grey)](https://arxiv.org/abs/2604.09747)
* **_P$^2$RAG: Efficient Privacy-Preserving RAG Service Supporting Arbitrary Top-$k$ Retrieval_**, Ming et al., [![arXiv](https://img.shields.io/badge/arXiv-2603.14778-red?labelColor=grey)](https://arxiv.org/abs/2603.14778) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/myl7/p2rag)
* **_CIMemories: A Compositional Benchmark For Contextual Integrity In LLMs_**, Mireshghallah et al., [![ICLR](https://img.shields.io/badge/ICLR-2026-blue?labelColor=grey)](https://openreview.net/forum?id=YnNIp38v1M) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/facebookresearch/CIMemories)
* **_Differentially Private Synthetic Text Generation for Retrieval-Augmented Generation (RAG)_**, Mori, [![ACL Findings](https://img.shields.io/badge/ACL_Findings-2026-blue?labelColor=grey)](https://aclanthology.org/2026.findings-acl.62/) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/sarus-tech/dp-rag)
* **_OMNI-LEAK: Orchestrator Multi-Agent Network Induced Data Leakage_**, Naik et al., [![arXiv](https://img.shields.io/badge/arXiv-2602.13477-red?labelColor=grey)](https://arxiv.org/abs/2602.13477)
* **_AgentSCOPE: Evaluating Contextual Privacy Across Agentic Workflows_**, Ngong et al., [![arXiv](https://img.shields.io/badge/arXiv-2603.04902-red?labelColor=grey)](https://arxiv.org/abs/2603.04902)
* **_Hidden in Memory: Sleeper Memory Poisoning in LLM Agents_**, Pulipaka et al., [![arXiv](https://img.shields.io/badge/arXiv-2605.15338-red?labelColor=grey)](https://arxiv.org/abs/2605.15338) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/ivaxi0s/LLM-agent-memory-poisoning)
* **_Mind the Web: The Security of Web Use Agents_**, Shapira et al., [![AsiaCCS](https://img.shields.io/badge/AsiaCCS-2026-blue?labelColor=grey)](https://doi.org/10.1145/3779208.3805968) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/mindtheweb/mind_the_web)
* **_Memory Poisoning Attack and Defense on Memory Based LLM-Agents_**, Sunil et al., [![arXiv](https://img.shields.io/badge/arXiv-2601.05504-red?labelColor=grey)](https://arxiv.org/abs/2601.05504)
* **_The Trust Paradox in LLM-Based Multi-Agent Systems: When Collaboration Becomes a Security Vulnerability_**, Xu et al., [![IEEE TCSS](https://img.shields.io/badge/IEEE_TCSS-2026-blue?labelColor=grey)](https://doi.org/10.1109/TCSS.2026.3695070)
* **_AgentLeak: A Benchmark for Internal-Channel Privacy Leakage in Multi-Agent LLM Systems_**, Yagoubi et al., [![IEEE Access](https://img.shields.io/badge/IEEE_Access-2026-blue?labelColor=grey)](https://doi.org/10.1109/ACCESS.2026.3704541) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/Privatris/AgentLeak)
* **_AgentDAM: Privacy Leakage Evaluation for Autonomous Web Agents_**, Zharmagambetov et al., [![NeurIPS D&B](https://img.shields.io/badge/NeurIPS_D%26B-2026-blue?labelColor=grey)](https://openreview.net/forum?id=qaxf7q41aK) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/facebookresearch/ai-agent-privacy)
* **_Operationalizing Data Minimization for Privacy-Preserving LLM Prompting_**, Zhou et al., [![ICLR](https://img.shields.io/badge/ICLR-2026-blue?labelColor=grey)](https://openreview.net/forum?id=rpcnvW33EG) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/PEACH-Research-Lab/Operationalize-Data-Minimization/)
* **_SALT: Steering Activations towards Leakage-free Thinking in Chain of Thought_**, Batra et al., [![arXiv](https://img.shields.io/badge/arXiv-2511.07772-red?labelColor=grey)](https://arxiv.org/abs/2511.07772) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/ShouryaBatra/SALT)
* **_Securing AI Agents with Information-Flow Control_**, Costa et al., [![arXiv](https://img.shields.io/badge/arXiv-2505.23643-red?labelColor=grey)](https://arxiv.org/abs/2505.23643) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/microsoft/fides)
* **_Trivial Trojans: How Minimal MCP Servers Enable Cross-Tool Exfiltration of Sensitive Data_**, Croce et al., [![arXiv](https://img.shields.io/badge/arXiv-2507.19880-red?labelColor=grey)](https://arxiv.org/abs/2507.19880) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/Nicocro/mcp-trivial-trojans)
* **_Leaky Thoughts: Large Reasoning Models Are Not Private Thinkers_**, Green, [![EMNLP](https://img.shields.io/badge/EMNLP-2025-blue?labelColor=grey)](https://aclanthology.org/2025.emnlp-main.1347/) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/parameterlab/leaky_thoughts)
* **_Feedback-Guided Extraction of Knowledge Base from Retrieval-Augmented LLM Applications_**, Jiang et al., [![arXiv](https://img.shields.io/badge/arXiv-2411.14110-red?labelColor=grey)](https://arxiv.org/abs/2411.14110)
* **_Privacy-Preserving Retrieval-Augmented Generation with Differential Privacy_**, Koga et al., [![arXiv](https://img.shields.io/badge/arXiv-2412.04697-red?labelColor=grey)](https://arxiv.org/abs/2412.04697) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/tacchan7412/DPRAG)
* **_PrivaCI-Bench: Evaluating Privacy with Contextual Integrity and Legal Compliance_**, Li, [![ACL](https://img.shields.io/badge/ACL-2025-blue?labelColor=grey)](https://aclanthology.org/2025.acl-long.518/) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/HKUST-KnowComp/PrivaCI-Bench)
* **_EIA: Environmental Injection Attack on Generalist Web Agents for Privacy Leakage_**, Liao et al., [![ICLR](https://img.shields.io/badge/ICLR-2025-blue?labelColor=grey)](https://openreview.net/forum?id=xMOLUzo2Lk) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/OSU-NLP-Group/EIA_against_webagent)
* **_AgentSafe: Safeguarding Large Language Model-based Multi-agent Systems via Hierarchical Data Management_**, Mao et al., [![arXiv](https://img.shields.io/badge/arXiv-2503.04392-red?labelColor=grey)](https://arxiv.org/abs/2503.04392)
* **_Context manipulation attacks : Web agents are susceptible to corrupted memory_**, Patlan et al., [![arXiv](https://img.shields.io/badge/arXiv-2506.17318-red?labelColor=grey)](https://arxiv.org/abs/2506.17318)
* **_Position: Contextual Integrity is Inadequately Applied to Language Models_**, Shvartzshnaider et al., [![ICML Position](https://img.shields.io/badge/ICML_Position-2025-blue?labelColor=grey)](https://openreview.net/forum?id=YmTxiR1HUX)
* **_MSA: A Cross-MCP Privacy Attack via Memory Exfiltration of Large Language Models_**, Sun et al., [![WPES](https://img.shields.io/badge/WPES-2025-blue?labelColor=grey)](https://doi.org/10.1145/3733802.3764057)
* **_A-MemGuard: A Proactive Defense Framework for LLM-Based Agent Memory_**, Wei et al., [![arXiv](https://img.shields.io/badge/arXiv-2510.02373-red?labelColor=grey)](https://arxiv.org/abs/2510.02373) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/TangciuYueng/AMemGuard)
* **_AirGapAgent: Protecting Privacy-Conscious Conversational Agents_**, Bagdasarian et al., [![CCS](https://img.shields.io/badge/CCS-2024-blue?labelColor=grey)](https://doi.org/10.1145/3658644.3690350)
* **_AGENTPOISON: red-teaming LLM agents via poisoning memory or knowledge bases_**, Chen et al., [![NeurIPS](https://img.shields.io/badge/NeurIPS-2024-blue?labelColor=grey)](https://arxiv.org/abs/2407.12784) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/AI-secure/AgentPoison)
* **_CI-Bench: Benchmarking Contextual Integrity of AI Assistants on Synthetic Data_**, Cheng et al., [![arXiv](https://img.shields.io/badge/arXiv-2409.13903-red?labelColor=grey)](https://arxiv.org/abs/2409.13903)
* **_AgentDojo: a dynamic environment to evaluate prompt injection attacks and defenses for LLM agents_**, Debenedetti et al., [![NeurIPS](https://img.shields.io/badge/NeurIPS-2024-blue?labelColor=grey)](https://arxiv.org/abs/2406.13352) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/ethz-spylab/agentdojo)
* **_GoldCoin: Grounding Large Language Models in Privacy Laws via Contextual Integrity Theory_**, Fan, [![EMNLP](https://img.shields.io/badge/EMNLP-2024-blue?labelColor=grey)](https://aclanthology.org/2024.emnlp-main.195/) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/HKUST-KnowComp/GoldCoin)
* **_MetaGPT: Meta Programming for A Multi-Agent Collaborative Framework_**, Hong et al., [![ICLR](https://img.shields.io/badge/ICLR-2024-blue?labelColor=grey)](https://openreview.net/forum?id=VtmBAGCN7o) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/FoundationAgents/MetaGPT)
* **_Pirates of the RAG: Adaptively Attacking LLMs to Leak Knowledge Bases_**, Maio et al., [![arXiv](https://img.shields.io/badge/arXiv-2412.18295-red?labelColor=grey)](https://arxiv.org/abs/2412.18295) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/gnekt/Pirates-of-the-RAG)
* **_Can LLMs Keep a Secret? Testing Privacy Implications of Language Models via Contextual Integrity Theory_**, Mireshghallah et al., [![ICLR](https://img.shields.io/badge/ICLR-2024-blue?labelColor=grey)](https://openreview.net/forum?id=gmg7t8b4s0) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/skywalker023/confAIde)
* **_MemGPT: Towards LLMs as Operating Systems_**, Packer et al., [![arXiv](https://img.shields.io/badge/arXiv-2310.08560-red?labelColor=grey)](https://arxiv.org/abs/2310.08560) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/letta-ai/letta)
* **_Privacylens: Evaluating privacy norm awareness of language models in action_**, Shao et al., [![NeurIPS](https://img.shields.io/badge/NeurIPS-2024-blue?labelColor=grey)](https://doi.org/10.52202/079017-2837) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/SALT-NLP/PrivacyLens)
* **_AutoGen: Enabling Next-Gen LLM Applications via Multi-Agent Conversations_**, Wu et al., [![COLM](https://img.shields.io/badge/COLM-2024-blue?labelColor=grey)](https://openreview.net/forum?id=BAakY1hNKS) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/mph-llmops/autogen)
* **_InjecAgent: Benchmarking Indirect Prompt Injections in Tool-Integrated Large Language Model Agents_**, Zhan, [![ACL Findings](https://img.shields.io/badge/ACL_Findings-2024-blue?labelColor=grey)](https://aclanthology.org/2024.findings-acl.624/) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/uiuc-kang-lab/InjecAgent)
* **_Flocks of Stochastic Parrots: Differentially Private Prompt Learning for Large Language Models_**, Duan et al., [![NeurIPS](https://img.shields.io/badge/NeurIPS-2023-blue?labelColor=grey)](https://openreview.net/forum?id=u6Xv3FuF8N) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/FloofCat/FlocksParrots)
* **_Not What You've Signed Up For: Compromising Real-World LLM-Integrated Applications with Indirect Prompt Injection_**, Greshake et al., [![AISec](https://img.shields.io/badge/AISec-2023-blue?labelColor=grey)](https://doi.org/10.1145/3605764.3623985) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/greshake/llm-security)
* **_Generative Agents: Interactive Simulacra of Human Behavior_**, Park et al., [![UIST](https://img.shields.io/badge/UIST-2023-blue?labelColor=grey)](https://doi.org/10.1145/3586183.3606763) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/joonspk-research/generative_agents)
* **_Toolformer: language models can teach themselves to use tools_**, Schick et al., [![NeurIPS](https://img.shields.io/badge/NeurIPS-2023-blue?labelColor=grey)](https://arxiv.org/abs/2302.04761) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/conceptofmind/toolformer)
* **_Reflexion: language agents with verbal reinforcement learning_**, Shinn et al., [![NeurIPS](https://img.shields.io/badge/NeurIPS-2023-blue?labelColor=grey)](https://arxiv.org/abs/2303.11366) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/noahshinn/reflexion)
* **_DEPN: Detecting and Editing Privacy Neurons in Pretrained Language Models_**, Wu, [![EMNLP](https://img.shields.io/badge/EMNLP-2023-blue?labelColor=grey)](https://aclanthology.org/2023.emnlp-main.174/) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/flamewei123/DEPN)
* **_The secret sharer: evaluating and testing unintended memorization in neural networks_**, Carlini et al., [![USENIX Security](https://img.shields.io/badge/USENIX_Security-2019-blue?labelColor=grey)](https://arxiv.org/abs/1802.08232)
* **_Deep Learning with Differential Privacy_**, Abadi et al., [![CCS](https://img.shields.io/badge/CCS-2016-blue?labelColor=grey)](https://doi.org/10.1145/2976749.2978318)
* **_Calibrating noise to sensitivity in private data analysis_**, Dwork et al., [![TCC](https://img.shields.io/badge/TCC-2006-blue?labelColor=grey)](https://doi.org/10.1007/11681878_14) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/SegmondFault/Calibrating_Noise_to_Sensitivity_in_Private_Data_Analysis)
* **_Privacy as contextual integrity_**, Nissenbaum, ![Wash. L. Rev.](https://img.shields.io/badge/Wash._L._Rev.-2004-blue?labelColor=grey)

### User Context, Norms, and Data Minimization

<p align="center">
  <img src="./assets/context-overview.png" width="850" alt="User context and norms overview"/>
  <br/>
  <em>Surface A: Privacy risks and defenses overview in context-aware LLM agents.</em>
</p>

* **_CI-Work: Benchmarking Contextual Integrity in Enterprise LLM Agents_**, Fu, [![ACL](https://img.shields.io/badge/ACL-2026-blue?labelColor=grey)](https://aclanthology.org/2026.acl-industry.103/) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/microsoft/ACV/tree/main/misc/CI-Work)
* **_HypoVeil: A Hypothesis-Driven Pragmatic Inference-Time Control Framework for Privacy-Utility-Aware LLM-Agent Dialogue_**, Li et al., [![Preprint](https://img.shields.io/badge/Preprint-2026-blue?labelColor=grey)](https://openreview.net/forum?id=sbvdUNO12X)
* **_CIMemories: A Compositional Benchmark For Contextual Integrity In LLMs_**, Mireshghallah et al., [![ICLR](https://img.shields.io/badge/ICLR-2026-blue?labelColor=grey)](https://openreview.net/forum?id=YnNIp38v1M) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/facebookresearch/CIMemories)
* **_AgentSCOPE: Evaluating Contextual Privacy Across Agentic Workflows_**, Ngong et al., [![arXiv](https://img.shields.io/badge/arXiv-2603.04902-red?labelColor=grey)](https://arxiv.org/abs/2603.04902)
* **_User Perceptions vs. Proxy LLM Judges: Privacy and Helpfulness in LLM Responses to Privacy-Sensitive Scenarios_**, Wu, [![ACL](https://img.shields.io/badge/ACL-2026-blue?labelColor=grey)](https://aclanthology.org/2026.acl-long.1645/)
* **_Not My Agent, Not My Boundary? Elicitation of Personal Privacy Boundaries in AI-Delegated Information Sharing_**, Guo et al., [![arXiv](https://img.shields.io/badge/arXiv-2509.21712-red?labelColor=grey)](https://arxiv.org/abs/2509.21712)
* **_Context Reasoner: Incentivizing Reasoning Capability for Contextualized Privacy and Safety Compliance via Reinforcement Learning_**, Hu, [![EMNLP](https://img.shields.io/badge/EMNLP-2025-blue?labelColor=grey)](https://aclanthology.org/2025.emnlp-main.44/) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/HKUST-KnowComp/ContextReasoner)
* **_Contextual Integrity in LLMs via Reasoning and Reinforcement Learning_**, Lan et al., [![arXiv](https://img.shields.io/badge/arXiv-2506.04245-red?labelColor=grey)](https://arxiv.org/abs/2506.04245) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/EricGLan/CI-RL)
* **_PrivaCI-Bench: Evaluating Privacy with Contextual Integrity and Legal Compliance_**, Li, [![ACL](https://img.shields.io/badge/ACL-2025-blue?labelColor=grey)](https://aclanthology.org/2025.acl-long.518/) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/HKUST-KnowComp/PrivaCI-Bench)
* **_1-2-3 Check: Enhancing Contextual Privacy in LLM via Multi-Agent Reasoning_**, Li, [![LLMSec](https://img.shields.io/badge/LLMSec-2025-blue?labelColor=grey)](https://aclanthology.org/2025.llmsec-1.9/)
* **_Privacy in Action: Towards Realistic Privacy Mitigation and Evaluation for LLM-Powered Agents_**, Wang, [![EMNLP Findings](https://img.shields.io/badge/EMNLP_Findings-2025-blue?labelColor=grey)](https://aclanthology.org/2025.findings-emnlp.925/) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/microsoft/ACV/tree/main/misc/PrivacyInAction)
* **_AirGapAgent: Protecting Privacy-Conscious Conversational Agents_**, Bagdasarian et al., [![CCS](https://img.shields.io/badge/CCS-2024-blue?labelColor=grey)](https://doi.org/10.1145/3658644.3690350)
* **_CI-Bench: Benchmarking Contextual Integrity of AI Assistants on Synthetic Data_**, Cheng et al., [![arXiv](https://img.shields.io/badge/arXiv-2409.13903-red?labelColor=grey)](https://arxiv.org/abs/2409.13903)
* **_GoldCoin: Grounding Large Language Models in Privacy Laws via Contextual Integrity Theory_**, Fan, [![EMNLP](https://img.shields.io/badge/EMNLP-2024-blue?labelColor=grey)](https://aclanthology.org/2024.emnlp-main.195/) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/HKUST-KnowComp/GoldCoin)
* **_Operationalizing Contextual Integrity in Privacy-Conscious Assistants_**, Ghalebikesabi et al., [![arXiv](https://img.shields.io/badge/arXiv-2408.02373-red?labelColor=grey)](https://arxiv.org/abs/2408.02373)
* **_Can LLMs Keep a Secret? Testing Privacy Implications of Language Models via Contextual Integrity Theory_**, Mireshghallah et al., [![ICLR](https://img.shields.io/badge/ICLR-2024-blue?labelColor=grey)](https://openreview.net/forum?id=gmg7t8b4s0) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/skywalker023/confAIde)
* **_Privacylens: Evaluating privacy norm awareness of language models in action_**, Shao et al., [![NeurIPS](https://img.shields.io/badge/NeurIPS-2024-blue?labelColor=grey)](https://doi.org/10.52202/079017-2837) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/SALT-NLP/PrivacyLens)
* **_Large Language Models Can Be Contextual Privacy Protection Learners_**, Xiao et al., [![EMNLP](https://img.shields.io/badge/EMNLP-2024-blue?labelColor=grey)](https://aclanthology.org/2024.emnlp-main.785/) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/Yijia-Xiao/PrivacyMind)

### Privacy in RAG and Private Knowledge Retrieval

<p align="center">
  <img src="./assets/rag-overview.png" width="850" alt="RAG and private knowledge retrieval overview"/>
  <br/>
  <em>Surface B: Privacy risks and defenses overview in LLM agents with RAG.</em>
</p>

* **_Ensemble Privacy Defense for Knowledge-Intensive LLMs against Membership Inference Attacks_**, Fu, [![EACL Findings](https://img.shields.io/badge/EACL_Findings-2026-blue?labelColor=grey)](https://aclanthology.org/2026.findings-eacl.145/) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/RageFu2004/Ensemble-Privacy-Defense)
* **_PRAG: End-to-End Privacy-Preserving Retrieval-Augmented Generation_**, Li et al., [![arXiv](https://img.shields.io/badge/arXiv-2604.26525-red?labelColor=grey)](https://arxiv.org/abs/2604.26525) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/BDS-SDU/PRAG)
* **_ALDEN: Boosting Private Data Extraction from Retrieval-Augmented Generation Systems via Active Learning and Distribution Estimation_**, Lyu et al., [![arXiv](https://img.shields.io/badge/arXiv-2605.18762-red?labelColor=grey)](https://arxiv.org/abs/2605.18762)
* **_P$^2$RAG: Efficient Privacy-Preserving RAG Service Supporting Arbitrary Top-$k$ Retrieval_**, Ming et al., [![arXiv](https://img.shields.io/badge/arXiv-2603.14778-red?labelColor=grey)](https://arxiv.org/abs/2603.14778) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/myl7/p2rag)
* **_Differentially Private Synthetic Text Generation for Retrieval-Augmented Generation (RAG)_**, Mori, [![ACL Findings](https://img.shields.io/badge/ACL_Findings-2026-blue?labelColor=grey)](https://aclanthology.org/2026.findings-acl.62/) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/sarus-tech/dp-rag)
* **_Privacy-protected Retrieval-Augmented Generation for Knowledge Graph Question Answering_**, Ning et al., ![AAAI](https://img.shields.io/badge/AAAI-2026-blue?labelColor=grey) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/NLPGM/ARoG)
* **_Benchmarking knowledge-extraction attack and defense on retrieval-augmented generation_**, Qi et al., [![arXiv](https://img.shields.io/badge/arXiv-2602.09319-red?labelColor=grey)](https://arxiv.org/abs/2602.09319) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/charlieqi02/RAG-Knowledge-Extraction-Attack-and-Defense-Benchmark)
* **_Differentially Private Retrieval-Augmented Generation_**, Tang et al., [![arXiv](https://img.shields.io/badge/arXiv-2602.14374-red?labelColor=grey)](https://arxiv.org/abs/2602.14374) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/facebookresearch/dp_rdm)
* **_Privacy Policy Enforcement Guardrails for Data-Sensitive Retrieval-Augmented Generation_**, Zafar et al., [![arXiv](https://img.shields.io/badge/arXiv-2605.17034-red?labelColor=grey)](https://arxiv.org/abs/2605.17034)
* **_Not All Entities are Created Equal: A Dynamic Anonymization Framework for Privacy-Preserving RAG_**, Zhu et al., [![arXiv](https://img.shields.io/badge/arXiv-2603.26074-red?labelColor=grey)](https://arxiv.org/abs/2603.26074)
* **_Is My Data in Your Retrieval Database? Membership Inference Attacks Against Retrieval Augmented Generation_**, Anderson et al., [![ICISSP](https://img.shields.io/badge/ICISSP-2025-blue?labelColor=grey)](http://dx.doi.org/10.5220/0013108300003899)
* **_Fine-Grained Privacy Extraction from Retrieval-Augmented Generation Systems via Knowledge Asymmetry Exploitation_**, Chen et al., [![arXiv](https://img.shields.io/badge/arXiv-2507.23229-red?labelColor=grey)](https://arxiv.org/abs/2507.23229) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/Attention-1999/Fine_Grained)
* **_RemoteRAG: A Privacy-Preserving LLM Cloud RAG Service_**, Cheng, [![ACL Findings](https://img.shields.io/badge/ACL_Findings-2025-blue?labelColor=grey)](https://aclanthology.org/2025.findings-acl.197/)
* **_Safeguarding Privacy of Retrieval Data against Membership Inference Attacks: Is This Query Too Close to Home?_**, Choi, [![EMNLP Findings](https://img.shields.io/badge/EMNLP_Findings-2025-blue?labelColor=grey)](https://aclanthology.org/2025.findings-emnlp.438/) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/nonalcohol-park/MIRABEL)
* **_MARAGE: Transferable Multi-Model Adversarial Attack for Retrieval-Augmented Generation Data Extraction_**, Hu et al., [![arXiv](https://img.shields.io/badge/arXiv-2502.04360-red?labelColor=grey)](https://arxiv.org/abs/2502.04360)
* **_EmbSTar: Efficient Multi-branch Black-box Semantic-aware Targeted Attack Against Deep Hashing Retrieval_**, Huang et al., [![ICASSP](https://img.shields.io/badge/ICASSP-2025-blue?labelColor=grey)](https://doi.org/10.1109/ICASSP49660.2025.10889223) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/6tonystark6/EmbSTar)
* **_Feedback-Guided Extraction of Knowledge Base from Retrieval-Augmented LLM Applications_**, Jiang et al., [![arXiv](https://img.shields.io/badge/arXiv-2411.14110-red?labelColor=grey)](https://arxiv.org/abs/2411.14110)
* **_Privacy-Preserving Retrieval-Augmented Generation with Differential Privacy_**, Koga et al., [![arXiv](https://img.shields.io/badge/arXiv-2412.04697-red?labelColor=grey)](https://arxiv.org/abs/2412.04697) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/tacchan7412/DPRAG)
* **_Generating Is Believing: Membership Inference Attacks against Retrieval-Augmented Generation_**, Li et al., [![ICASSP](https://img.shields.io/badge/ICASSP-2025-blue?labelColor=grey)](https://doi.org/10.1109/ICASSP49660.2025.10889013)
* **_BudgetLeak: Membership Inference Attacks on RAG Systems via the Generation Budget Side Channel_**, Li et al., [![arXiv](https://img.shields.io/badge/arXiv-2511.12043-red?labelColor=grey)](https://arxiv.org/abs/2511.12043)
* **_Pla: Prompt learning attack against text-to-image generative models_**, Lyu et al., ![ICCV](https://img.shields.io/badge/ICCV-2025-blue?labelColor=grey) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/xinqilyu/PLA)
* **_Riddle Me This! Stealthy Membership Inference for Retrieval-Augmented Generation_**, Naseh et al., [![CCS](https://img.shields.io/badge/CCS-2025-blue?labelColor=grey)](https://doi.org/10.1145/3719027.3744840) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/ali7naseh/RAG_MIA)
* **_Follow My Instruction and Spill the Beans: Scalable Data Extraction from Retrieval-Augmented Generation Systems_**, Qi et al., [![ICLR](https://img.shields.io/badge/ICLR-2025-blue?labelColor=grey)](https://openreview.net/forum?id=Y4aWwRh25b)
* **_PIR-RAG: A System for Private Information Retrieval in Retrieval-Augmented Generation_**, Wang et al., [![arXiv](https://img.shields.io/badge/arXiv-2509.21325-red?labelColor=grey)](https://arxiv.org/abs/2509.21325)
* **_Private-RAG: Answering Multiple Queries with LLMs while Keeping Your Data Private_**, Wu et al., [![arXiv](https://img.shields.io/badge/arXiv-2511.07637-red?labelColor=grey)](https://arxiv.org/abs/2511.07637)
* **_Mitigating the Privacy Issues in Retrieval-Augmented Generation (RAG) via Pure Synthetic Data_**, Zeng, [![EMNLP](https://img.shields.io/badge/EMNLP-2025-blue?labelColor=grey)](https://aclanthology.org/2025.emnlp-main.1247/) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/phycholosogy/RAG-SAGE)
* **_Pirates of the RAG: Adaptively Attacking LLMs to Leak Knowledge Bases_**, Maio et al., [![arXiv](https://img.shields.io/badge/arXiv-2412.18295-red?labelColor=grey)](https://arxiv.org/abs/2412.18295) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/gnekt/Pirates-of-the-RAG)
* **_The Good and The Bad: Exploring Privacy Issues in Retrieval-Augmented Generation (RAG)_**, Zeng, [![ACL Findings](https://img.shields.io/badge/ACL_Findings-2024-blue?labelColor=grey)](https://aclanthology.org/2024.findings-acl.267/) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/phycholosogy/RAG-privacy)
* **_Retrieval-augmented generation for knowledge-intensive NLP tasks_**, Lewis et al., [![NeurIPS](https://img.shields.io/badge/NeurIPS-2020-blue?labelColor=grey)](https://arxiv.org/abs/2005.11401)

### Agent Memory and Persistent State

<p align="center">
  <img src="./assets/memory-overview.png" width="850" alt="Agent memory overview"/>
  <br/>
  <em>Surface C: Privacy risks and defenses overview in LLM agents with memory system.</em>
</p>

* **_Trojan Hippo: Weaponizing Agent Memory for Data Exfiltration_**, Das et al., [![arXiv](https://img.shields.io/badge/arXiv-2605.01970-red?labelColor=grey)](https://arxiv.org/abs/2605.01970) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/debesheedas/trojan-hippo-benchmark)
* **_Memory Injection Attacks on LLM Agents via Query-Only Interaction_**, Dong et al., [![arXiv](https://img.shields.io/badge/arXiv-2503.03704-red?labelColor=grey)](https://arxiv.org/abs/2503.03704) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/dsh3n77/MINJA)
* **_ADAM: A Systematic Data Extraction Attack on Agent Memory via Adaptive Querying_**, Lyu et al., [![arXiv](https://img.shields.io/badge/arXiv-2604.09747-red?labelColor=grey)](https://arxiv.org/abs/2604.09747)
* **_CIMemories: A Compositional Benchmark For Contextual Integrity In LLMs_**, Mireshghallah et al., [![ICLR](https://img.shields.io/badge/ICLR-2026-blue?labelColor=grey)](https://openreview.net/forum?id=YnNIp38v1M) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/facebookresearch/CIMemories)
* **_Hidden in Memory: Sleeper Memory Poisoning in LLM Agents_**, Pulipaka et al., [![arXiv](https://img.shields.io/badge/arXiv-2605.15338-red?labelColor=grey)](https://arxiv.org/abs/2605.15338) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/ivaxi0s/LLM-agent-memory-poisoning)
* **_Memory Poisoning Attack and Defense on Memory Based LLM-Agents_**, Sunil et al., [![arXiv](https://img.shields.io/badge/arXiv-2601.05504-red?labelColor=grey)](https://arxiv.org/abs/2601.05504)
* **_Your LLM Agent Can Leak Your Data: Data Exfiltration via Backdoored Tool Use_**, Zhang, [![ACL Findings](https://img.shields.io/badge/ACL_Findings-2026-blue?labelColor=grey)](https://aclanthology.org/2026.findings-acl.1257/)
* **_Poison Once, Exploit Forever: Environment-Injected Memory Poisoning Attacks on Web Agents_**, Zou et al., [![arXiv](https://img.shields.io/badge/arXiv-2604.02623-red?labelColor=grey)](https://arxiv.org/abs/2604.02623)
* **_Provably Robust Adaptation for Language-Empowered Foundation Models_**, Lai et al., [![arXiv](https://img.shields.io/badge/arXiv-2510.08659-red?labelColor=grey)](https://arxiv.org/abs/2510.08659) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/Yuni-Lai/LeFCert)
* **_Context manipulation attacks : Web agents are susceptible to corrupted memory_**, Patlan et al., [![arXiv](https://img.shields.io/badge/arXiv-2506.17318-red?labelColor=grey)](https://arxiv.org/abs/2506.17318)
* **_MSA: A Cross-MCP Privacy Attack via Memory Exfiltration of Large Language Models_**, Sun et al., [![WPES](https://img.shields.io/badge/WPES-2025-blue?labelColor=grey)](https://doi.org/10.1145/3733802.3764057)
* **_Unveiling Privacy Risks in LLM Agent Memory_**, Wang, [![ACL](https://img.shields.io/badge/ACL-2025-blue?labelColor=grey)](https://aclanthology.org/2025.acl-long.1227/) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/wangbo9719/MEXTRA)
* **_A-MemGuard: A Proactive Defense Framework for LLM-Based Agent Memory_**, Wei et al., [![arXiv](https://img.shields.io/badge/arXiv-2510.02373-red?labelColor=grey)](https://arxiv.org/abs/2510.02373) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/TangciuYueng/AMemGuard)

### Tool Use, Action, and Environment Interfaces

<p align="center">
  <img src="./assets/tool-overview.png" width="850" alt="Tool use and environment interfaces overview"/>
  <br/>
  <em>Surface D: Privacy risks and defenses overview in tool-use LLM agents.</em>
</p>

* **_AgentSecBench: Measuring Prompt Injection, Privacy Leakage, and Tool-Use Integrity in LLM Agents_**, Alpay et al., [![arXiv](https://img.shields.io/badge/arXiv-2605.26269-red?labelColor=grey)](https://arxiv.org/abs/2605.26269)
* **_Enhancing targeted adversarial attacks on large vision-language models via intermediate projector_**, Cao et al., ![IEEE TIFS](https://img.shields.io/badge/IEEE_TIFS-2026-blue?labelColor=grey)
* **_Personal Data Flows and Privacy Policy Traceability in Third-party LLM Apps in the GPT Ecosystem_**, Carrillo et al., ![PoPETs](https://img.shields.io/badge/PoPETs-2026-blue?labelColor=grey)
* **_How Your Credentials Are Leaked by LLM Agent Skills: An Empirical Study_**, Chen et al., [![arXiv](https://img.shields.io/badge/arXiv-2604.03070-red?labelColor=grey)](https://arxiv.org/abs/2604.03070) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/AgentSkillsPrivacy/SkillLeakBench)
* **_Towards Verifiably Safe Tool Use for LLM Agents_**, Doshi et al., [![arXiv](https://img.shields.io/badge/arXiv-2601.08012-red?labelColor=grey)](https://arxiv.org/abs/2601.08012)
* **_A Vision for Access Control in LLM Agent Systems_**, Huang, ![Complex Comp. Sys.](https://img.shields.io/badge/Complex_Comp._Sys.-2026-blue?labelColor=grey)
* **_Taming Various Privilege Escalation in LLM-Based Agent Systems: A Mandatory Access Control Framework_**, Ji et al., [![arXiv](https://img.shields.io/badge/arXiv-2601.11893-red?labelColor=grey)](https://arxiv.org/abs/2601.11893)
* **_You Told Me to Do It: Measuring Instructional Text-induced Private Data Leakage in LLM Agents_**, Kao et al., [![arXiv](https://img.shields.io/badge/arXiv-2603.11862-red?labelColor=grey)](https://arxiv.org/abs/2603.11862)
* **_Silent Egress: When Implicit Prompt Injection Makes LLM Agents Leak Without a Trace_**, Lan et al., [![arXiv](https://img.shields.io/badge/arXiv-2602.22450-red?labelColor=grey)](https://arxiv.org/abs/2602.22450)
* **_The Cognitive Firewall:Securing Browser Based AI Agents Against Indirect Prompt Injection Via Hybrid Edge Cloud Defense_**, Lan et al., [![arXiv](https://img.shields.io/badge/arXiv-2603.23791-red?labelColor=grey)](https://arxiv.org/abs/2603.23791)
* **_AgentGuard: An Attribute-Based Access Control Framework for Tool-Use LLM-Based Agent_**, Luo et al., [![arXiv](https://img.shields.io/badge/arXiv-2605.28071-red?labelColor=grey)](https://arxiv.org/abs/2605.28071) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/jie311/AgentGuard--)
* **_Agent Tools Orchestration Leaks More: Dataset, Benchmark, and Mitigation_**, Qiao et al., [![arXiv](https://img.shields.io/badge/arXiv-2512.16310-red?labelColor=grey)](https://arxiv.org/abs/2512.16310) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/1Ponder/TOP-R)
* **_Exploiting Web Search Tools of AI Agents for Data Exfiltration_**, Rall et al., [![arXiv](https://img.shields.io/badge/arXiv-2510.09093-red?labelColor=grey)](https://arxiv.org/abs/2510.09093) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/Smart-Labs-AI/web-search-exploit-paper)
* **_Mind the Web: The Security of Web Use Agents_**, Shapira et al., [![AsiaCCS](https://img.shields.io/badge/AsiaCCS-2026-blue?labelColor=grey)](https://doi.org/10.1145/3779208.3805968) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/mindtheweb/mind_the_web)
* **_AgentDAM: Privacy Leakage Evaluation for Autonomous Web Agents_**, Zharmagambetov et al., [![NeurIPS D&B](https://img.shields.io/badge/NeurIPS_D%26B-2026-blue?labelColor=grey)](https://openreview.net/forum?id=qaxf7q41aK) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/facebookresearch/ai-agent-privacy)
* **_Simple Prompt Injection Attacks Can Leak Personal Data Observed by LLM Agents During Task Execution_**, Alizadeh et al., [![arXiv](https://img.shields.io/badge/arXiv-2506.01055-red?labelColor=grey)](https://arxiv.org/abs/2506.01055)
* **_Casper: Prompt Sanitization for Protecting User Privacy in Web-Based Large Language Models_**, Chong et al., [![CSCloud](https://img.shields.io/badge/CSCloud-2025-blue?labelColor=grey)](https://doi.org/10.1109/CSCloud66326.2025.00027) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/redoubt-lab/Casper)
* **_Securing AI Agents with Information-Flow Control_**, Costa et al., [![arXiv](https://img.shields.io/badge/arXiv-2505.23643-red?labelColor=grey)](https://arxiv.org/abs/2505.23643) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/microsoft/fides)
* **_Trivial Trojans: How Minimal MCP Servers Enable Cross-Tool Exfiltration of Sensitive Data_**, Croce et al., [![arXiv](https://img.shields.io/badge/arXiv-2507.19880-red?labelColor=grey)](https://arxiv.org/abs/2507.19880) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/Nicocro/mcp-trivial-trojans)
* **_HUANG: A Robust Diffusion Model-based Targeted Adversarial Attack Against Deep Hashing Retrieval_**, Huang et al., [![AAAI](https://img.shields.io/badge/AAAI-2025-blue?labelColor=grey)](https://ojs.aaai.org/index.php/AAAI/article/view/32377) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/6tonystark6/HUANG)
* **_MCIP: Protecting MCP Safety via Model Contextual Integrity Protocol_**, Jing, [![EMNLP](https://img.shields.io/badge/EMNLP-2025-blue?labelColor=grey)](https://aclanthology.org/2025.emnlp-main.62/) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/HKUST-KnowComp/MCIP)
* **_AgentTypo: Adaptive Typographic Prompt Injection Attacks against Black-box Multimodal Agents_**, Li et al., [![arXiv](https://img.shields.io/badge/arXiv-2510.04257-red?labelColor=grey)](https://arxiv.org/abs/2510.04257)
* **_EIA: Environmental Injection Attack on Generalist Web Agents for Privacy Leakage_**, Liao et al., [![ICLR](https://img.shields.io/badge/ICLR-2025-blue?labelColor=grey)](https://openreview.net/forum?id=xMOLUzo2Lk) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/OSU-NLP-Group/EIA_against_webagent)
* **_Invitation Is All You Need! Promptware Attacks Against LLM-Powered Assistants in Production Are Practical and Dangerous_**, Nassi et al., [![arXiv](https://img.shields.io/badge/arXiv-2508.12175-red?labelColor=grey)](https://arxiv.org/abs/2508.12175)
* **_LeakSealer: A Semisupervised Defense for LLMs Against Prompt Injection and Leakage Attacks_**, Panebianco et al., [![arXiv](https://img.shields.io/badge/arXiv-2508.00602-red?labelColor=grey)](https://arxiv.org/abs/2508.00602)
* **_MSA: A Cross-MCP Privacy Attack via Memory Exfiltration of Large Language Models_**, Sun et al., [![WPES](https://img.shields.io/badge/WPES-2025-blue?labelColor=grey)](https://doi.org/10.1145/3733802.3764057)
* **_Pace: Privacy-Preserving and Atomic Cross-chain Swaps for Cryptocurrency Exchanges_**, Wang et al., [![AsiaCCS](https://img.shields.io/badge/AsiaCCS-2025-blue?labelColor=grey)](https://doi.org/10.1145/3708821.3736211)
* **_RTBAS: Defending LLM Agents Against Prompt Injection and Privacy Leakage_**, Zhong et al., [![arXiv](https://img.shields.io/badge/arXiv-2502.08966-red?labelColor=grey)](https://arxiv.org/abs/2502.08966)
* **_AgentDojo: a dynamic environment to evaluate prompt injection attacks and defenses for LLM agents_**, Debenedetti et al., [![NeurIPS](https://img.shields.io/badge/NeurIPS-2024-blue?labelColor=grey)](https://arxiv.org/abs/2406.13352) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/ethz-spylab/agentdojo)
* **_InjecAgent: Benchmarking Indirect Prompt Injections in Tool-Integrated Large Language Model Agents_**, Zhan, [![ACL Findings](https://img.shields.io/badge/ACL_Findings-2024-blue?labelColor=grey)](https://aclanthology.org/2024.findings-acl.624/) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/uiuc-kang-lab/InjecAgent)
* **_Not What You've Signed Up For: Compromising Real-World LLM-Integrated Applications with Indirect Prompt Injection_**, Greshake et al., [![AISec](https://img.shields.io/badge/AISec-2023-blue?labelColor=grey)](https://doi.org/10.1145/3605764.3623985) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/greshake/llm-security)

### Multiagent Communication and Delegation

<p align="center">
  <img src="./assets/mas-overview.png" width="850" alt="Multiagent communication overview"/>
  <br/>
  <em>Surface E: Privacy risks and defenses overview in multiagent systems.</em>
</p>

* **_Information-Theoretic Privacy Control for Sequential Multi-Agent LLM Systems_**, Asif et al., [![arXiv](https://img.shields.io/badge/arXiv-2603.05520-red?labelColor=grey)](https://arxiv.org/abs/2603.05520)
* **_MIN-Trust: A Minimum Necessary Information Trust Orchestration Framework for Multi-Agent Collaboration_**, Chen et al., [![ICGAIE](https://img.shields.io/badge/ICGAIE-2026-blue?labelColor=grey)](https://doi.org/10.1145/3813808.3813811)
* **_SecureGov-Agent: A Governance-Centric Multi-Agent Framework for Privacy-Preserving and Attack-Resilient LLM Agents_**, Chen et al., [![ICCSMT](https://img.shields.io/badge/ICCSMT-2026-blue?labelColor=grey)](https://doi.org/10.1145/3795154.3795296)
* **_PrivAct: Internalizing Contextual Privacy Preservation via Multi-Agent Preference Training_**, Cheng et al., ![ICML](https://img.shields.io/badge/ICML-2026-blue?labelColor=grey) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/chengyh23/PrivAct)
* **_AgentCollabBench: Diagnosing When Good Agents Make Bad Collaborators_**, Mazumder et al., [![arXiv](https://img.shields.io/badge/arXiv-2605.08647-red?labelColor=grey)](https://arxiv.org/abs/2605.08647) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/aritra741/AgentCollabBench)
* **_OMNI-LEAK: Orchestrator Multi-Agent Network Induced Data Leakage_**, Naik et al., [![arXiv](https://img.shields.io/badge/arXiv-2602.13477-red?labelColor=grey)](https://arxiv.org/abs/2602.13477)
* **_PAC-BENCH: Evaluating Multi-Agent Collaboration under Privacy Constraints_**, Park, [![ACL Findings](https://img.shields.io/badge/ACL_Findings-2026-blue?labelColor=grey)](https://aclanthology.org/2026.findings-acl.1552/) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/PAC-Bench/PAC-Bench)
* **_Got a Secret? LLM Agents Can't Keep It: Evaluating Privacy in Multi-Agent Systems_**, Priyanshu et al., [![arXiv](https://img.shields.io/badge/arXiv-2605.27766-red?labelColor=grey)](https://arxiv.org/abs/2605.27766)
* **_MASLeak: Investigating and Exposing Intellectual Property Leakage Vulnerabilities in Multi-Agent Systems_**, Wang et al., ![USENIX Security](https://img.shields.io/badge/USENIX_Security-2026-blue?labelColor=grey)
* **_AgentSocialBench: Evaluating Privacy Risks in Human-Centered Agentic Social Networks_**, Wang et al., [![arXiv](https://img.shields.io/badge/arXiv-2604.01487-red?labelColor=grey)](https://arxiv.org/abs/2604.01487) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/kingofspace0wzz/agentsocialbench)
* **_Flexible and Privacy-Preserving Access Control Framework for Decentralized Identity Systems_**, Xie et al., [![IEEE TIFS](https://img.shields.io/badge/IEEE_TIFS-2026-blue?labelColor=grey)](https://doi.org/10.1109/TIFS.2026.3676653)
* **_The Trust Paradox in LLM-Based Multi-Agent Systems: When Collaboration Becomes a Security Vulnerability_**, Xu et al., [![IEEE TCSS](https://img.shields.io/badge/IEEE_TCSS-2026-blue?labelColor=grey)](https://doi.org/10.1109/TCSS.2026.3695070)
* **_AgentLeak: A Benchmark for Internal-Channel Privacy Leakage in Multi-Agent LLM Systems_**, Yagoubi et al., [![IEEE Access](https://img.shields.io/badge/IEEE_Access-2026-blue?labelColor=grey)](https://doi.org/10.1109/ACCESS.2026.3704541) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/Privatris/AgentLeak)
* **_PAAC: Privacy-Aware Agentic Device-Cloud Collaboration_**, Yuan et al., [![arXiv](https://img.shields.io/badge/arXiv-2605.08646-red?labelColor=grey)](https://arxiv.org/abs/2605.08646)
* **_POLAR-Bench: A Diagnostic Benchmark for Privacy-Utility Trade-offs in LLM Agents_**, Zheng et al., [![arXiv](https://img.shields.io/badge/arXiv-2605.19127-red?labelColor=grey)](https://arxiv.org/abs/2605.19127)
* **_CalBench: Evaluating Coordination-Privacy Trade-offs in Multi-Agent LLMs_**, Zou et al., [![arXiv](https://img.shields.io/badge/arXiv-2605.09823-red?labelColor=grey)](https://arxiv.org/abs/2605.09823) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://anonymous.4open.science/r/calbench2026-235F/README.md)
* **_PSP: A Privacy-Preserving Self-certify Pseudonym Protocol for V2X_**, Cai et al., [![AsiaCCS](https://img.shields.io/badge/AsiaCCS-2025-blue?labelColor=grey)](https://doi.org/10.1145/3708821.3736212) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/CXYALEX/PSP)
* **_Sentinel Agents for Secure and Trustworthy Agentic AI in Multi-Agent Systems_**, Gosmar et al., [![arXiv](https://img.shields.io/badge/arXiv-2509.14956-red?labelColor=grey)](https://arxiv.org/abs/2509.14956)
* **_MAGPIE: A benchmark for Multi-AGent contextual PrIvacy Evaluation_**, Juneja et al., [![arXiv](https://img.shields.io/badge/arXiv-2510.15186-red?labelColor=grey)](https://arxiv.org/abs/2510.15186) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/gurusha01/magpie/)
* **_1-2-3 Check: Enhancing Contextual Privacy in LLM via Multi-Agent Reasoning_**, Li, [![LLMSec](https://img.shields.io/badge/LLMSec-2025-blue?labelColor=grey)](https://aclanthology.org/2025.llmsec-1.9/)
* **_AgentSafe: Safeguarding Large Language Model-based Multi-agent Systems via Hierarchical Data Management_**, Mao et al., [![arXiv](https://img.shields.io/badge/arXiv-2503.04392-red?labelColor=grey)](https://arxiv.org/abs/2503.04392)
* **_The Sum Leaks More Than Its Parts: Compositional Privacy Risks and Mitigations in Multi-Agent Collaboration_**, Patil et al., [![arXiv](https://img.shields.io/badge/arXiv-2509.14284-red?labelColor=grey)](https://arxiv.org/abs/2509.14284) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/Vaidehi99/MultiAgentPrivacy)
* **_Privacy-Enhancing Paradigms within Federated Multi-Agent Systems_**, Shi et al., [![arXiv](https://img.shields.io/badge/arXiv-2503.08175-red?labelColor=grey)](https://arxiv.org/abs/2503.08175)
* **_CCN: Decentralized Cross-Chain Channel Networks Supporting Secure and Privacy-Preserving Multi-Hop Interactions_**, Xu et al., [![arXiv](https://img.shields.io/badge/arXiv-2512.03791-red?labelColor=grey)](https://arxiv.org/abs/2512.03791)

### Reasoning, Planning, and Profiling Traces

* **_Safer Reasoning Traces: Measuring and Mitigating Chain-of-Thought Leakage in LLMs_**, Ahrend, [![PrivateNLP](https://img.shields.io/badge/PrivateNLP-2026-blue?labelColor=grey)](https://aclanthology.org/2026.privatenlp-main.10/)
* **_Dependency-Aware Privacy for Multi-turn Agents_**, Anshumaan et al., [![arXiv](https://img.shields.io/badge/arXiv-2605.03188-red?labelColor=grey)](https://arxiv.org/abs/2605.03188) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/danshumaan/rootguard)
* **_Profiling for Pennies: Unveiling the Privacy Iceberg of LLM Agents_**, Chen et al., [![arXiv](https://img.shields.io/badge/arXiv-2605.06232-red?labelColor=grey)](https://arxiv.org/abs/2605.06232)
* **_LGA: lightweight design and privacy analysis of generative agents in social simulations_**, Guo et al., [![Int. J. Inf. Secur.](https://img.shields.io/badge/Int._J._Inf._Secur.-2026-blue?labelColor=grey)](https://doi.org/10.1007/s10207-026-01244-y)
* **_MosaicLeaks:Privacy Risks in Querying-in-the-Open for Deep Research Agents_**, Gurung et al., [![arXiv](https://img.shields.io/badge/arXiv-2605.30727-red?labelColor=grey)](https://arxiv.org/abs/2605.30727) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/ServiceNow/MosaicProject)
* **_Behavioral Transfer in AI Agents: Evidence and Privacy Implications_**, Luo et al., [![arXiv](https://img.shields.io/badge/arXiv-2604.19925-red?labelColor=grey)](https://arxiv.org/abs/2604.19925)
* **_Red-teaming Retrieval-Augmented Diffusion Models via Poisoning Knowledge Bases_**, Lyu et al., ![CVPR](https://img.shields.io/badge/CVPR-2026-blue?labelColor=grey)
* **_DAIQ: Auditing Demographic Attribute Inference from Question in LLMs_**, Panda et al., [![arXiv](https://img.shields.io/badge/arXiv-2508.15830-red?labelColor=grey)](https://arxiv.org/abs/2508.15830)
* **_Beyond Refusal: Probing the Limits of Agentic Self-Correction for Semantic Sensitive Information_**, Suleymanov et al., [![arXiv](https://img.shields.io/badge/arXiv-2602.21496-red?labelColor=grey)](https://arxiv.org/abs/2602.21496) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://anonymous.4open.science/r/SemSIEdit-3231/README.md)
* **_PAAC: Privacy-Aware Agentic Device-Cloud Collaboration_**, Yuan et al., [![arXiv](https://img.shields.io/badge/arXiv-2605.08646-red?labelColor=grey)](https://arxiv.org/abs/2605.08646)
* **_Operationalizing Data Minimization for Privacy-Preserving LLM Prompting_**, Zhou et al., [![ICLR](https://img.shields.io/badge/ICLR-2026-blue?labelColor=grey)](https://openreview.net/forum?id=rpcnvW33EG) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/PEACH-Research-Lab/Operationalize-Data-Minimization/)
* **_SALT: Steering Activations towards Leakage-free Thinking in Chain of Thought_**, Batra et al., [![arXiv](https://img.shields.io/badge/arXiv-2511.07772-red?labelColor=grey)](https://arxiv.org/abs/2511.07772) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/ShouryaBatra/SALT)
* **_Leaky Thoughts: Large Reasoning Models Are Not Private Thinkers_**, Green, [![EMNLP](https://img.shields.io/badge/EMNLP-2025-blue?labelColor=grey)](https://aclanthology.org/2025.emnlp-main.1347/) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/parameterlab/leaky_thoughts)
* **_Context Reasoner: Incentivizing Reasoning Capability for Contextualized Privacy and Safety Compliance via Reinforcement Learning_**, Hu, [![EMNLP](https://img.shields.io/badge/EMNLP-2025-blue?labelColor=grey)](https://aclanthology.org/2025.emnlp-main.44/) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/HKUST-KnowComp/ContextReasoner)
* **_ScoreAdv: Score-based Targeted Generation of Natural Adversarial Examples via Diffusion Models_**, Huang et al., [![arXiv](https://img.shields.io/badge/arXiv-2507.06078-red?labelColor=grey)](https://arxiv.org/abs/2507.06078) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/6tonystark6/ScoreAdv)
* **_Beyond Memorization: Violating Privacy via Inference with Large Language Models_**, Staab et al., [![ICLR](https://img.shields.io/badge/ICLR-2024-blue?labelColor=grey)](https://openreview.net/forum?id=kmn0BhQk7p) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/eth-sri/llmprivacy)

### Cross-Cutting Privacy Controls and Deployment Substrate

<p align="center">
  <img src="./assets/cross-cutting-overview.png" width="850" alt="Cross-cutting deployment substrate overview"/>
  <br/>
  <em>Surface G: Overview of privacy risks and defenses across the cross-cutting layers of LLM agents.</em>
</p>

* **_AgenTEE: Confidential LLM Agent Execution on Edge Devices_**, Abdollahi et al., [![EuroMLSys](https://img.shields.io/badge/EuroMLSys-2026-blue?labelColor=grey)](https://doi.org/10.1145/3805621.3807660) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/comet-cc/AgenTEE)
* **_Protecting User Prompts Via Character-Level Differential Privacy_**, Arachchige et al., [![arXiv](https://img.shields.io/badge/arXiv-2603.26032-red?labelColor=grey)](https://arxiv.org/abs/2603.26032)
* **_An AI Agent Execution Environment to Safeguard User Data_**, Stanley et al., [![arXiv](https://img.shields.io/badge/arXiv-2604.19657-red?labelColor=grey)](https://arxiv.org/abs/2604.19657)
* **_Agentic Unlearning: When LLM Agent Meets Machine Unlearning_**, Wang et al., [![arXiv](https://img.shields.io/badge/arXiv-2602.17692-red?labelColor=grey)](https://arxiv.org/abs/2602.17692)
* **_PriFFT: Privacy-Preserving Federated Fine-Tuning of Large Language Models via Hybrid Secret Sharing_**, You et al., [![IEEE TDSC](https://img.shields.io/badge/IEEE_TDSC-2026-blue?labelColor=grey)](https://doi.org/10.1109/TDSC.2026.3661572)
* **_Burn-After-Use for Preventing Data Leakage through a Secure Multi-Tenant Architecture in Enterprise LLM_**, Zhang et al., [![arXiv](https://img.shields.io/badge/arXiv-2601.06627-red?labelColor=grey)](https://arxiv.org/abs/2601.06627)
* **_Securing AI Agents with Information-Flow Control_**, Costa et al., [![arXiv](https://img.shields.io/badge/arXiv-2505.23643-red?labelColor=grey)](https://arxiv.org/abs/2505.23643) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/microsoft/fides)
* **_Differentially Private Vertical Federated Learning With Adaptive Constraints and Dynamic Noise_**, Gai et al., [![IEEE TIFS](https://img.shields.io/badge/IEEE_TIFS-2025-blue?labelColor=grey)](https://doi.org/10.1109/TIFS.2025.3620213)
* **_PAPILLON: Privacy Preservation from Internet-based and Local Language Model Ensembles_**, Li, [![NAACL](https://img.shields.io/badge/NAACL-2025-blue?labelColor=grey)](https://aclanthology.cn/2025.naacl-long.173/) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/Columbia-NLP-Lab/PAPILLON)
* **_LOMIA: Label-Only Membership Inference Attacks against Pre-trained Large Vision-Language Models_**, Liu et al., [![NeurIPS](https://img.shields.io/badge/NeurIPS-2025-blue?labelColor=grey)](https://openreview.net/forum?id=7JjS2cdBYN) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/Halyyyyy/LOMIA)
* **_Secfwt: Efficient privacy-preserving fine-tuning of large language models using forward-only passes_**, Luo et al., ![arXiv](https://img.shields.io/badge/arXiv-2025-blue?labelColor=grey)
* **_The Early Bird Catches the Leak: Unveiling Timing Side Channels in LLM Serving Systems_**, Song et al., [![IEEE TIFS](https://img.shields.io/badge/IEEE_TIFS-2025-blue?labelColor=grey)](https://doi.org/10.1109/TIFS.2025.3622954) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/Maxppddcsz/llm-sidechannel)
* **_Position: AI agents need authenticated delegation_**, South et al., ![ICML](https://img.shields.io/badge/ICML-2025-blue?labelColor=grey)
* **_RewardDS: Privacy-Preserving Fine-Tuning for Large Language Models via Reward Driven Data Synthesis_**, Wang, [![EMNLP](https://img.shields.io/badge/EMNLP-2025-blue?labelColor=grey)](https://aclanthology.org/2025.emnlp-main.223/) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/ZeroNLP/RewardDS)
* **_Argus: A Multi-Agent Sensitive Information Leakage Detection Framework Based on Hierarchical Reference Relationships_**, Wang et al., [![arXiv](https://img.shields.io/badge/arXiv-2512.08326-red?labelColor=grey)](https://arxiv.org/abs/2512.08326)
* **_Private-RAG: Answering Multiple Queries with LLMs while Keeping Your Data Private_**, Wu et al., [![arXiv](https://img.shields.io/badge/arXiv-2511.07637-red?labelColor=grey)](https://arxiv.org/abs/2511.07637)
* **_Auditing private prediction_**, Chadha et al., ![ICML](https://img.shields.io/badge/ICML-2024-blue?labelColor=grey)
* **_Privacy-preserving Fine-tuning of Large Language Models through Flatness_**, Chen et al., [![ICLR Workshop](https://img.shields.io/badge/ICLR_Workshop-2024-blue?labelColor=grey)](https://openreview.net/forum?id=LtdcfCw92l)
* **_AgentDojo: a dynamic environment to evaluate prompt injection attacks and defenses for LLM agents_**, Debenedetti et al., [![NeurIPS](https://img.shields.io/badge/NeurIPS-2024-blue?labelColor=grey)](https://arxiv.org/abs/2406.13352) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/ethz-spylab/agentdojo)
* **_Open LLMs are Necessary for Current Private Adaptations and Outperform their Closed Alternatives_**, Hanke et al., [![NeurIPS](https://img.shields.io/badge/NeurIPS-2024-blue?labelColor=grey)](https://openreview.net/forum?id=Jf40H5pRW0) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/sprintml/OpenLLMs)
* **_Can Sensitive Information Be Deleted From LLMs? Objectives for Defending Against Extraction Attacks_**, Patil et al., [![ICLR](https://img.shields.io/badge/ICLR-2024-blue?labelColor=grey)](https://openreview.net/forum?id=7erlRDoaV8) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/Vaidehi99/InfoDeletionAttacks)
* **_DePrompt: Desensitization and Evaluation of Personal Identifiable Information in Large Language Model Prompts_**, Sun et al., [![arXiv](https://img.shields.io/badge/arXiv-2408.08930-red?labelColor=grey)](https://arxiv.org/abs/2408.08930)
* **_Privacy-Preserving In-Context Learning with Differentially Private Few-Shot Generation_**, Tang et al., [![ICLR](https://img.shields.io/badge/ICLR-2024-blue?labelColor=grey)](https://openreview.net/forum?id=oZtt0pRnOl) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/microsoft/dp-few-shot-generation)
* **_Flocks of Stochastic Parrots: Differentially Private Prompt Learning for Large Language Models_**, Duan et al., [![NeurIPS](https://img.shields.io/badge/NeurIPS-2023-blue?labelColor=grey)](https://openreview.net/forum?id=u6Xv3FuF8N) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/FloofCat/FlocksParrots)
* **_DEPN: Detecting and Editing Privacy Neurons in Pretrained Language Models_**, Wu, [![EMNLP](https://img.shields.io/badge/EMNLP-2023-blue?labelColor=grey)](https://aclanthology.org/2023.emnlp-main.174/) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/flamewei123/DEPN)
* **_The secret sharer: evaluating and testing unintended memorization in neural networks_**, Carlini et al., [![USENIX Security](https://img.shields.io/badge/USENIX_Security-2019-blue?labelColor=grey)](https://arxiv.org/abs/1802.08232)
* **_Deep Learning with Differential Privacy_**, Abadi et al., [![CCS](https://img.shields.io/badge/CCS-2016-blue?labelColor=grey)](https://doi.org/10.1145/2976749.2978318)

### Evaluation Landscape and Benchmark Analysis

* **_AgentSecBench: Measuring Prompt Injection, Privacy Leakage, and Tool-Use Integrity in LLM Agents_**, Alpay et al., [![arXiv](https://img.shields.io/badge/arXiv-2605.26269-red?labelColor=grey)](https://arxiv.org/abs/2605.26269)
* **_MIN-Trust: A Minimum Necessary Information Trust Orchestration Framework for Multi-Agent Collaboration_**, Chen et al., [![ICGAIE](https://img.shields.io/badge/ICGAIE-2026-blue?labelColor=grey)](https://doi.org/10.1145/3813808.3813811)
* **_Trojan Hippo: Weaponizing Agent Memory for Data Exfiltration_**, Das et al., [![arXiv](https://img.shields.io/badge/arXiv-2605.01970-red?labelColor=grey)](https://arxiv.org/abs/2605.01970) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/debesheedas/trojan-hippo-benchmark)
* **_MosaicLeaks:Privacy Risks in Querying-in-the-Open for Deep Research Agents_**, Gurung et al., [![arXiv](https://img.shields.io/badge/arXiv-2605.30727-red?labelColor=grey)](https://arxiv.org/abs/2605.30727) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/ServiceNow/MosaicProject)
* **_You Told Me to Do It: Measuring Instructional Text-induced Private Data Leakage in LLM Agents_**, Kao et al., [![arXiv](https://img.shields.io/badge/arXiv-2603.11862-red?labelColor=grey)](https://arxiv.org/abs/2603.11862)
* **_Silent Egress: When Implicit Prompt Injection Makes LLM Agents Leak Without a Trace_**, Lan et al., [![arXiv](https://img.shields.io/badge/arXiv-2602.22450-red?labelColor=grey)](https://arxiv.org/abs/2602.22450)
* **_Behavioral Transfer in AI Agents: Evidence and Privacy Implications_**, Luo et al., [![arXiv](https://img.shields.io/badge/arXiv-2604.19925-red?labelColor=grey)](https://arxiv.org/abs/2604.19925)
* **_ALDEN: Boosting Private Data Extraction from Retrieval-Augmented Generation Systems via Active Learning and Distribution Estimation_**, Lyu et al., [![arXiv](https://img.shields.io/badge/arXiv-2605.18762-red?labelColor=grey)](https://arxiv.org/abs/2605.18762)
* **_ADAM: A Systematic Data Extraction Attack on Agent Memory via Adaptive Querying_**, Lyu et al., [![arXiv](https://img.shields.io/badge/arXiv-2604.09747-red?labelColor=grey)](https://arxiv.org/abs/2604.09747)
* **_CIMemories: A Compositional Benchmark For Contextual Integrity In LLMs_**, Mireshghallah et al., [![ICLR](https://img.shields.io/badge/ICLR-2026-blue?labelColor=grey)](https://openreview.net/forum?id=YnNIp38v1M) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/facebookresearch/CIMemories)
* **_OMNI-LEAK: Orchestrator Multi-Agent Network Induced Data Leakage_**, Naik et al., [![arXiv](https://img.shields.io/badge/arXiv-2602.13477-red?labelColor=grey)](https://arxiv.org/abs/2602.13477)
* **_AgentSCOPE: Evaluating Contextual Privacy Across Agentic Workflows_**, Ngong et al., [![arXiv](https://img.shields.io/badge/arXiv-2603.04902-red?labelColor=grey)](https://arxiv.org/abs/2603.04902)
* **_PAC-BENCH: Evaluating Multi-Agent Collaboration under Privacy Constraints_**, Park, [![ACL Findings](https://img.shields.io/badge/ACL_Findings-2026-blue?labelColor=grey)](https://aclanthology.org/2026.findings-acl.1552/) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/PAC-Bench/PAC-Bench)
* **_Hidden in Memory: Sleeper Memory Poisoning in LLM Agents_**, Pulipaka et al., [![arXiv](https://img.shields.io/badge/arXiv-2605.15338-red?labelColor=grey)](https://arxiv.org/abs/2605.15338) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/ivaxi0s/LLM-agent-memory-poisoning)
* **_Differentially Private Retrieval-Augmented Generation_**, Tang et al., [![arXiv](https://img.shields.io/badge/arXiv-2602.14374-red?labelColor=grey)](https://arxiv.org/abs/2602.14374) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/facebookresearch/dp_rdm)
* **_MASLeak: Investigating and Exposing Intellectual Property Leakage Vulnerabilities in Multi-Agent Systems_**, Wang et al., ![USENIX Security](https://img.shields.io/badge/USENIX_Security-2026-blue?labelColor=grey)
* **_AgentSocialBench: Evaluating Privacy Risks in Human-Centered Agentic Social Networks_**, Wang et al., [![arXiv](https://img.shields.io/badge/arXiv-2604.01487-red?labelColor=grey)](https://arxiv.org/abs/2604.01487) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/kingofspace0wzz/agentsocialbench)
* **_User Perceptions vs. Proxy LLM Judges: Privacy and Helpfulness in LLM Responses to Privacy-Sensitive Scenarios_**, Wu, [![ACL](https://img.shields.io/badge/ACL-2026-blue?labelColor=grey)](https://aclanthology.org/2026.acl-long.1645/)
* **_AgentLeak: A Benchmark for Internal-Channel Privacy Leakage in Multi-Agent LLM Systems_**, Yagoubi et al., [![IEEE Access](https://img.shields.io/badge/IEEE_Access-2026-blue?labelColor=grey)](https://doi.org/10.1109/ACCESS.2026.3704541) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/Privatris/AgentLeak)
* **_POLAR-Bench: A Diagnostic Benchmark for Privacy-Utility Trade-offs in LLM Agents_**, Zheng et al., [![arXiv](https://img.shields.io/badge/arXiv-2605.19127-red?labelColor=grey)](https://arxiv.org/abs/2605.19127)
* **_Poison Once, Exploit Forever: Environment-Injected Memory Poisoning Attacks on Web Agents_**, Zou et al., [![arXiv](https://img.shields.io/badge/arXiv-2604.02623-red?labelColor=grey)](https://arxiv.org/abs/2604.02623)
* **_CalBench: Evaluating Coordination-Privacy Trade-offs in Multi-Agent LLMs_**, Zou et al., [![arXiv](https://img.shields.io/badge/arXiv-2605.09823-red?labelColor=grey)](https://arxiv.org/abs/2605.09823) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://anonymous.4open.science/r/calbench2026-235F/README.md)
* **_SALT: Steering Activations towards Leakage-free Thinking in Chain of Thought_**, Batra et al., [![arXiv](https://img.shields.io/badge/arXiv-2511.07772-red?labelColor=grey)](https://arxiv.org/abs/2511.07772) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/ShouryaBatra/SALT)
* **_Leaky Thoughts: Large Reasoning Models Are Not Private Thinkers_**, Green, [![EMNLP](https://img.shields.io/badge/EMNLP-2025-blue?labelColor=grey)](https://aclanthology.org/2025.emnlp-main.1347/) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/parameterlab/leaky_thoughts)
* **_Not My Agent, Not My Boundary? Elicitation of Personal Privacy Boundaries in AI-Delegated Information Sharing_**, Guo et al., [![arXiv](https://img.shields.io/badge/arXiv-2509.21712-red?labelColor=grey)](https://arxiv.org/abs/2509.21712)
* **_Feedback-Guided Extraction of Knowledge Base from Retrieval-Augmented LLM Applications_**, Jiang et al., [![arXiv](https://img.shields.io/badge/arXiv-2411.14110-red?labelColor=grey)](https://arxiv.org/abs/2411.14110)
* **_MAGPIE: A benchmark for Multi-AGent contextual PrIvacy Evaluation_**, Juneja et al., [![arXiv](https://img.shields.io/badge/arXiv-2510.15186-red?labelColor=grey)](https://arxiv.org/abs/2510.15186) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/gurusha01/magpie/)
* **_PrivaCI-Bench: Evaluating Privacy with Contextual Integrity and Legal Compliance_**, Li, [![ACL](https://img.shields.io/badge/ACL-2025-blue?labelColor=grey)](https://aclanthology.org/2025.acl-long.518/) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/HKUST-KnowComp/PrivaCI-Bench)
* **_BudgetLeak: Membership Inference Attacks on RAG Systems via the Generation Budget Side Channel_**, Li et al., [![arXiv](https://img.shields.io/badge/arXiv-2511.12043-red?labelColor=grey)](https://arxiv.org/abs/2511.12043)
* **_PAPILLON: Privacy Preservation from Internet-based and Local Language Model Ensembles_**, Li, [![NAACL](https://img.shields.io/badge/NAACL-2025-blue?labelColor=grey)](https://aclanthology.cn/2025.naacl-long.173/) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/Columbia-NLP-Lab/PAPILLON)
* **_EIA: Environmental Injection Attack on Generalist Web Agents for Privacy Leakage_**, Liao et al., [![ICLR](https://img.shields.io/badge/ICLR-2025-blue?labelColor=grey)](https://openreview.net/forum?id=xMOLUzo2Lk) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/OSU-NLP-Group/EIA_against_webagent)
* **_AgentSafe: Safeguarding Large Language Model-based Multi-agent Systems via Hierarchical Data Management_**, Mao et al., [![arXiv](https://img.shields.io/badge/arXiv-2503.04392-red?labelColor=grey)](https://arxiv.org/abs/2503.04392)
* **_The Sum Leaks More Than Its Parts: Compositional Privacy Risks and Mitigations in Multi-Agent Collaboration_**, Patil et al., [![arXiv](https://img.shields.io/badge/arXiv-2509.14284-red?labelColor=grey)](https://arxiv.org/abs/2509.14284) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/Vaidehi99/MultiAgentPrivacy)
* **_Follow My Instruction and Spill the Beans: Scalable Data Extraction from Retrieval-Augmented Generation Systems_**, Qi et al., [![ICLR](https://img.shields.io/badge/ICLR-2025-blue?labelColor=grey)](https://openreview.net/forum?id=Y4aWwRh25b)
* **_The Early Bird Catches the Leak: Unveiling Timing Side Channels in LLM Serving Systems_**, Song et al., [![IEEE TIFS](https://img.shields.io/badge/IEEE_TIFS-2025-blue?labelColor=grey)](https://doi.org/10.1109/TIFS.2025.3622954) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/Maxppddcsz/llm-sidechannel)
* **_Privacy in Action: Towards Realistic Privacy Mitigation and Evaluation for LLM-Powered Agents_**, Wang, [![EMNLP Findings](https://img.shields.io/badge/EMNLP_Findings-2025-blue?labelColor=grey)](https://aclanthology.org/2025.findings-emnlp.925/) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/microsoft/ACV/tree/main/misc/PrivacyInAction)
* **_AirGapAgent: Protecting Privacy-Conscious Conversational Agents_**, Bagdasarian et al., [![CCS](https://img.shields.io/badge/CCS-2024-blue?labelColor=grey)](https://doi.org/10.1145/3658644.3690350)
* **_Auditing private prediction_**, Chadha et al., ![ICML](https://img.shields.io/badge/ICML-2024-blue?labelColor=grey)
* **_CI-Bench: Benchmarking Contextual Integrity of AI Assistants on Synthetic Data_**, Cheng et al., [![arXiv](https://img.shields.io/badge/arXiv-2409.13903-red?labelColor=grey)](https://arxiv.org/abs/2409.13903)
* **_AgentDojo: a dynamic environment to evaluate prompt injection attacks and defenses for LLM agents_**, Debenedetti et al., [![NeurIPS](https://img.shields.io/badge/NeurIPS-2024-blue?labelColor=grey)](https://arxiv.org/abs/2406.13352) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/ethz-spylab/agentdojo)
* **_Can LLMs Keep a Secret? Testing Privacy Implications of Language Models via Contextual Integrity Theory_**, Mireshghallah et al., [![ICLR](https://img.shields.io/badge/ICLR-2024-blue?labelColor=grey)](https://openreview.net/forum?id=gmg7t8b4s0) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/skywalker023/confAIde)
* **_Privacylens: Evaluating privacy norm awareness of language models in action_**, Shao et al., [![NeurIPS](https://img.shields.io/badge/NeurIPS-2024-blue?labelColor=grey)](https://doi.org/10.52202/079017-2837) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/SALT-NLP/PrivacyLens)
* **_InjecAgent: Benchmarking Indirect Prompt Injections in Tool-Integrated Large Language Model Agents_**, Zhan, [![ACL Findings](https://img.shields.io/badge/ACL_Findings-2024-blue?labelColor=grey)](https://aclanthology.org/2024.findings-acl.624/) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/uiuc-kang-lab/InjecAgent)
* **_Flocks of Stochastic Parrots: Differentially Private Prompt Learning for Large Language Models_**, Duan et al., [![NeurIPS](https://img.shields.io/badge/NeurIPS-2023-blue?labelColor=grey)](https://openreview.net/forum?id=u6Xv3FuF8N) [![GitHub](https://img.shields.io/badge/GitHub-Code-white?logo=github)](https://github.com/FloofCat/FlocksParrots)


---

## Citation

If this repository or the survey is useful for your work, please cite:

```bibtex
coming soon.
```

---

## License

This repository is released under the MIT License unless otherwise specified. Paper copyrights belong to their respective authors.

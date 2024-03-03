# Constitutional AI: Harmlessness from AI Feedback

## Overview
| 🎯      | `TASK`     |  LLM Alignment |
|---------|:-----------|:---------------|

Constitutional AI (Bai et al., 2022) is a framework for AI to <ins>self-improve</ins> its response based on a list of <ins>human-specified principles</ins> (the 'constitution'). 
The major goal of this paper is to train an AI assistant that is both <ins>harmless and non-evasive</ins> (i.e., engage with harmful queries by explaining its objections to them).

| Challenge | Approach |
|---|---|
| Tensions between helpfulness and harmlessness<br>(alignment goals) | **Principle-guided SFT and RL** <ul><li>Steering the model's behavior with an \*explicit\* set of principles</li></ul> |
| Human feedback is costly! | **Scalable oversight** <br>(reduce reliance on manual feedback) <ul><li>Self-correction ("post-hoc prompting")</li> <li>Reinforcement learning from AI Feedback (RLAIF)</li></ul> |

## Architecture overview
### 1-`Supervised Learning Stage`
> Critique ➔ Revision ➔ Supervised Learning
<img width="840" alt="SL-CAI" src="https://github.com/Fanjie-Li/DS-5690/assets/36987602/70cd09c1-8d1c-4da6-a14b-ad5a0d8dbe33">
<br></br>

> **What's Different:** Principle-Guided Self-Critique + Revision for Generating SFT Training Data
<img width="1502" alt="critique_revision" src="https://github.com/Fanjie-Li/DS-5690/assets/36987602/91f7e2f2-d6ad-4f47-8358-092b0644d3d7">

### 2-`Reinforcement Learning Stage`
> AI Comparison Evaluations ➔ Preference Model ➔ Reinforcement Learning
<img width="840" alt="RL-CAI" src="https://github.com/Fanjie-Li/DS-5690/assets/36987602/99bffda0-87ed-47ac-ad67-21190f77f8c8">
<br></br>

> **What's Different:** Principle-Guided AI Comparison Evaluations
<img width="1502" alt="self_eval" src="https://github.com/Fanjie-Li/DS-5690/assets/36987602/e64c7d92-dc0a-4ac9-bcc3-5983f159ba4c">

## Questions & Critical analysis

## Resources
| ⌨️       | Code       |
|---------|:-----------|

Bai, Y., Kadavath, S., Kundu, S., Askell, A., Kernion, J., Jones, A., ... & Kaplan, J. (2022). [Constitutional AI: Harmlessness from AI feedback](https://arxiv.org/pdf/2212.08073.pdf?trk=public_post_comment-text). arXiv preprint arXiv:2212.08073.
- [Github repository](https://github.com/anthropics/ConstitutionalHarmlessnessPaper/tree/main)

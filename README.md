# Constitutional AI: Harmlessness from AI Feedback

## Overview
| 🎯      | `TASK`     |  LLM Alignment |
|---------|:-----------|:---------------|

Constitutional AI (Bai et al., 2022) is a framework for AI to <ins>self-improve</ins> its response based on a list of <ins>human-specified principles</ins> (the 'constitution'). 
The major goal of this paper is to train an AI assistant that is both <ins>harmless and non-evasive</ins> (i.e., engage with harmful queries by explaining its objections to them).

| Challenge | Approach |
|---|---|
| Tensions between helpfulness and harmlessness | **Principle-guided SFT and RL** <ul><li>Steering the model's behavior with an \*explicit\* set of principles</li></ul> |
| Human feedback is costly! | **Scalable oversight** <br>(reduce reliance on manual feedback) <ul><li>Self-correction ("post-hoc prompting")</li> <li>Reinforcement learning from AI Feedback’ (RLAIF)</li></ul> |

## Architecture overview
### 1-`Supervised Learning Stage`
> Critique ➔ Revision ➔ Supervised Learning
<img width="840" alt="SL-CAI" src="https://github.com/Fanjie-Li/DS-5690/assets/36987602/70cd09c1-8d1c-4da6-a14b-ad5a0d8dbe33">


### 2-`Reinforcement Learning Stage`
> AI Comparison Evaluations ➔ Preference Model ➔ Reinforcement Learning

## Critical analysis

## Resources
| ⌨️       | Code       |
|---------|:-----------|

Bai, Y., Kadavath, S., Kundu, S., Askell, A., Kernion, J., Jones, A., ... & Kaplan, J. (2022). [Constitutional AI: Harmlessness from AI feedback](https://arxiv.org/pdf/2212.08073.pdf?trk=public_post_comment-text). arXiv preprint arXiv:2212.08073.
- [Github repository](https://github.com/anthropics/ConstitutionalHarmlessnessPaper/tree/main)

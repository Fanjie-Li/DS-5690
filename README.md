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
<img width="841" alt="RL-CAI" src="https://github.com/Fanjie-Li/DS-5690/assets/36987602/1e9b6967-f2ab-4f39-aaff-384c04d0ed0e">
<br></br>

> **What's Different:** Principle-Guided AI Comparison Evaluations
<img width="1502" alt="self_eval" src="https://github.com/Fanjie-Li/DS-5690/assets/36987602/e64c7d92-dc0a-4ac9-bcc3-5983f159ba4c">

> [!NOTE]  
> Compared to the vanilla supervised fine-tuning (SFT) and reinforcement learning from human feedback (RLHF) (cf. InstructGPT), <br>what are the **added values of the constitutional AI approach**? (Feel free to share any drawbacks you notice ☺)

<details>
<summary>Hint 1</summary>
<details>
<summary>Scalable oversight</summary>
  
  * Making human supervision more efficient, transparent, targeted
  * Making it possible to train assistant with a **smaller quantatity** of **higher quality** human supervision
  * Human supervision will come entirely from a set of principles that should govern AI behavior, along with a small number of examples used for few-shot prompting
  
</details>
</details>

<details>
<summary>Hint 2</summary>
<details>
<summary>Making the alignment goal (value principles) explicit</summary>
  
  * **Transparency:** Literally encoding the training goals in a simple list of natural language instructions or principles.
  * **Reusability:** Obviating the need to collect new human feedback labels when switching the task.
  
</details>
</details>

<details>
<summary>Hint 3</summary>
<details>
<summary>Incorporation of in-context learning</summary>
  
  * **Reducing barriers for non-tech stakeholders:** Leveraging their knowledge of the application scenario and facilitating their participation and feedback in the model training process.
  * Introducing new opportunities for **integrating prompt engineering outcomes into the model's "memory"**
  
</details>
</details>

## Questions & Critical analysis
> [!CAUTION]
> **Concerns around automation in oversight**<br>
> Can AI provide reliable self-critique / evaluation? How to improve the robustness and trustworthiness of AI decision making in the training process?

<details>
  <summary>🤔</summary>
  
  * Use **chain-of-thought prompting** to make AI decision making more explicit during training
  * [Self-consistency](https://arxiv.org/abs/2203.11171) (cf. ensemble classifier)

</details><br>

> :bulb: `Future directions`<br><br>
> What intriguing application scenarios or use cases might emerge from this method beyond training harmless assistants?

<details>
  <summary>🤔</summary>
  
  * Achieve a persistent AI ‘persona’:
  * Change the model’s style, tone, or personality, or how it responds to specific categories of questions

</details>

## Resources
| ⌨️       | Code       |
|---------|:-----------|

Bai, Y., Kadavath, S., Kundu, S., Askell, A., Kernion, J., Jones, A., ... & Kaplan, J. (2022). [Constitutional AI: Harmlessness from AI feedback](https://arxiv.org/pdf/2212.08073.pdf?trk=public_post_comment-text). arXiv preprint arXiv:2212.08073.
- [Github repository](https://github.com/anthropics/ConstitutionalHarmlessnessPaper/tree/main)

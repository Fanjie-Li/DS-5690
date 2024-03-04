# Constitutional AI: Harmlessness from AI Feedback
Presenter: Fanjie Li

## Overview
| 🎯      | `TASK`     |  LLM Alignment |
|---------|:-----------|:---------------|

Constitutional AI (Bai et al., 2022) is a framework for AI to <ins>self-improve</ins> its response based on a list of <ins>human-specified principles</ins> (the 'constitution'). 
The major goal of this paper is to train an AI assistant that is both <ins>harmless and non-evasive</ins> (i.e., engage with harmful queries by explaining its objections to them).

| Challenge | Approach |
|---|---|
| Alignment goals - Tensions between helpfulness and harmlessness | **Principle-guided SFT and RL** <ul><li>Steering the model's behavior with an \*explicit\* set of principles</li></ul> |
| Human feedback is costly! | **Scalable oversight** <br>(reduce reliance on manual feedback) <ul><li>Self-correction ("post-hoc prompting")</li> <li>Reinforcement learning from AI Feedback (RLAIF)</li></ul> |

## Architecture overview
![pipeline](https://github.com/Fanjie-Li/DS-5690/assets/36987602/9c4f873c-cf7c-40d5-bb79-50d451636f51)
Image ©️ 2023 Anthropic
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
> Compared to the vanilla supervised fine-tuning (SFT) and reinforcement learning from human feedback (RLHF) (cf. InstructGPT), what are the **added values of the constitutional AI approach**? (Please also feel free to share any drawbacks you notice ☺)

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
Bai, Y., Kadavath, S., Kundu, S., Askell, A., Kernion, J., Jones, A., ... & Kaplan, J. (2022). [Constitutional AI: Harmlessness from AI feedback](https://arxiv.org/pdf/2212.08073.pdf?trk=public_post_comment-text). arXiv preprint arXiv:2212.08073.

| ⌨️       |Code / Demo|
|---------|:-----------|

- Github [repo](https://github.com/anthropics/ConstitutionalHarmlessnessPaper/tree/main) (Bai et al., 2022)
- Tutorial: Using Constitutional AI in LangChain〔[YouTube](https://www.youtube.com/watch?v=uoVqNFDwpX4)〕〔[Colab](https://colab.research.google.com/drive/1fTzx5ssGstX5yX8ig8PDjNElVPfTXRPN?usp=sharing)〕〔[LangChain](https://js.langchain.com/docs/modules/chains/additional/constitutional_chain)〕
- Tutorial: Constitutional AI with Open LLMs〔[Article](https://huggingface.co/blog/constitutional_ai)〕〔Github [repo](https://github.com/huggingface/alignment-handbook/tree/main/recipes/constitutional-ai)〕〔HuggingFace [demo](https://huggingface.co/spaces/HuggingFaceH4/constitutional-ai-demo) + models: [SFT](https://huggingface.co/HuggingFaceH4/mistral-7b-grok), [DPO](https://huggingface.co/HuggingFaceH4/mistral-7b-anthropic) + [dataset](https://huggingface.co/datasets/HuggingFaceH4/cai-conversation-harmless)〕
- 🎥 Claude (CAI) vs ChatGPT [demo](https://www.youtube.com/watch?v=KB5r9xmrQBY)
<br>

| 📖       | Further readings |
|---------|:-----------|

**Related approaches**
- Yao, J., Yi, X., Wang, X., Wang, J., & Xie, X. (2023). [From Instructions to Intrinsic Human Values - A Survey of Alignment Goals for Big Models](https://arxiv.org/pdf/2308.12014). arXiv preprint arXiv:2308.12014.
- Ji, J., Qiu, T., Chen, B., Zhang, B., Lou, H., Wang, K., ... & Gao, W. (2023). [AI alignment: A comprehensive survey](https://arxiv.org/pdf/2310.19852). arXiv preprint arXiv:2310.19852.

**Anthropic blog/reports** [🔗](https://www.constitutional.ai/) 
- Where the principles (constitution) come from: 1) Introduction to [Claude’s current constitution](https://www.anthropic.com/news/claudes-constitution); 2) [Public input](https://www.anthropic.com/news/collective-constitutional-ai-aligning-a-language-model-with-public-input) (2023)
- [Policy highlights](https://www-cdn.anthropic.com/7512771452629584566b6303311496c262da1006/Anthropic_ConstitutionalAI_v2.pdf) (2023, Apr)
- [Anthropic current safety research](https://www.anthropic.com/news/core-views-on-ai-safety) (2023, Mar 8)
- 🎥 [Interview](https://ecorner.stanford.edu/clips/constitutional-ai/) w/ Daniela Amodei (president and co-founder of Anthropic)

[![Multi-Modality](agorabanner.png)](https://discord.gg/qUtxnK2NMf)


# 🌴 PALM-E: A Multi-Modal AI Model 
![model architecture](image6.png)


This is the open source implementation of the SOTA multi-modality foundation model "PALM-E: An Embodied Multimodal Language Model" from Google, PALM-E is a single large embodied multimodal model, that can address a variety of embodied reasoning tasks, from a variety of observation modalities, on multiple embodiments, and further, exhibits positive transfer: the model benefits from diverse joint training across internet-scale language, vision, and visual-language domains.

[PAPER LINK: PaLM-E: An Embodied Multimodal Language Model](https://arxiv.org/abs/2303.03378)



[![GitHub issues](https://img.shields.io/github/issues/kyegomez/PALM-E)](https://github.com/kyegomez/PALM-E/issues) 
[![GitHub forks](https://img.shields.io/github/forks/kyegomez/PALM-E)](https://github.com/kyegomez/PALM-E/network) 
[![GitHub stars](https://img.shields.io/github/stars/kyegomez/PALM-E)](https://github.com/kyegomez/PALM-E/stargazers) [![GitHub license](https://img.shields.io/github/license/kyegomez/PALM-E)](https://github.com/kyegomez/PALM-E/blob/master/LICENSE)
[![Share on Twitter](https://img.shields.io/twitter/url/https/twitter.com/cloudposse.svg?style=social&label=Share%20%40kyegomez/PALM-E)](https://twitter.com/intent/tweet?text=Excited%20to%20introduce%20PALM-E,%20the%20all-new%20Multi-Modal%20model%20with%20the%20potential%20to%20revolutionize%20automation.%20Join%20us%20on%20this%20journey%20towards%20a%20smarter%20future.%20%23PALM-E%20%23Multi-Modal&url=https%3A%2F%2Fgithub.com%2Fkyegomez%2FPALM-E)
[![Share on Facebook](https://img.shields.io/badge/Share-%20facebook-blue)](https://www.facebook.com/sharer/sharer.php?u=https%3A%2F%2Fgithub.com%2Fkyegomez%2FPALM-E)
[![Share on LinkedIn](https://img.shields.io/badge/Share-%20linkedin-blue)](https://www.linkedin.com/shareArticle?mini=true&url=https%3A%2F%2Fgithub.com%2Fkyegomez%2FPALM-E&title=Introducing%20PALM-E%2C%20the%20All-New%20Multi-Modal%20Model&summary=PALM-E%20is%20the%20next-generation%20Multi-Modal%20model%20that%20promises%20to%20transform%20industries%20with%20its%20intelligence%20and%20efficiency.%20Join%20us%20to%20be%20a%20part%20of%20this%20revolutionary%20journey%20%23PALM-E%20%23Multi-Modal&source=)
![Discord](https://img.shields.io/discord/999382051935506503)
[![Share on Reddit](https://img.shields.io/badge/-Share%20on%20Reddit-orange)](https://www.reddit.com/submit?url=https%3A%2F%2Fgithub.com%2Fkyegomez%2FPALM-E&title=Exciting%20Times%20Ahead%20with%20PALM-E%2C%20the%20All-New%20Multi-Modal%20Model%20%23PALM-E%20%23Multi-Modal) [![Share on Hacker News](https://img.shields.io/badge/-Share%20on%20Hacker%20News-orange)](https://news.ycombinator.com/submitlink?u=https%3A%2F%2Fgithub.com%2Fkyegomez%2FPALM-E&t=Exciting%20Times%20Ahead%20with%20PALM-E%2C%20the%20All-New%20Multi-Modal%20Model%20%23PALM-E%20%23Multi-Modal)
[![Share on Pinterest](https://img.shields.io/badge/-Share%20on%20Pinterest-red)](https://pinterest.com/pin/create/button/?url=https%3A%2F%2Fgithub.com%2Fkyegomez%2FPALM-E&media=https%3A%2F%2Fexample.com%2Fimage.jpg&description=PALM-E%2C%20the%20Revolutionary%20Multi-Modal%20Model%20that%20will%20Change%20the%20Way%20We%20Work%20%23PALM-E%20%23Multi-Modal)
[![Share on WhatsApp](https://img.shields.io/badge/-Share%20on%20WhatsApp-green)](https://api.whatsapp.com/send?text=I%20just%20discovered%20PALM-E,%20the%20all-new%20Multi-Modal%20model%20that%20promises%20to%20revolutionize%20automation.%20Join%20me%20on%20this%20exciting%20journey%20towards%20a%20smarter%20future.%20%23PALM-E%20%23Multi-Modal%0A%0Ahttps%3A%2F%2Fgithub.com%2Fkyegomez%2FPALM-E)

## Note
- This is just the model architecture, no pretrained weights, no tokenizer
- To actually conduct inference you would need to --> setup tokenizer for text and images -> train -> inference
- If you are doing research into multi modal models and would like to train this model and release it open source join the agora lab by clicking on the banner!

## Appreciation
* All the creators in Agora, [Join Agora](https://discord.gg/qUtxnK2NMf) the community of AI engineers changing the world with their creations.
* LucidRains for inspiring me to devote myself to open source AI


## 🚀 Quick Start

### Installation 📦

```sh
pip install palme
```

### Usage 🎨

```python
import torch
from palme.model import PalmE

#usage
img = torch.randn(1, 3, 256, 256)
caption = torch.randint(0, 20000, (1, 1024))

model = PalmE()
output = model(img, caption)
print(output.shape) # (1, 1024, 20000)



```
---

# Training
Here is a summary table of the key training hyperparameters mentioned in the paper:

| Hyperparameter | Value |  
|-|-|
| Batch size | 2048 |
| Learning rate | 1.5e-4  |
| Warmup steps | 10,000 |
| Gradient accumulation steps | 4 |
| Weight decay | 0.01 |
| Dropout rate | 0.1 |
| Embedding dropout rate | 0.1 |
| Attention dropout rate | 0.1 |
| Optimizer | AdamW |
| Gradient clipping | 1.0 |

The key details are:
- Batch size of 2048 
- Learning rate of 1.5e-4 with 10k warmup steps
- AdamW optimizer
- Dropout of 0.1 on embeddings, attention, and full model
- Weight decay of 0.01
- Gradient clipping of 1.0

They used a fairly standard transformer hyperparameters configuration. The large batch size and gradient accumulation allows them to train huge models.

1. Set the environment variables:
   - `ENTITY_NAME`: Your wandb project name
   - `OUTPUT_DIR`: Directory to save the weights (e.g., `./weights`)
   - `MASTER_ADDR`: For distributed training
   - `MASTER_PORT` For master port distributed training
   - `RANK`- Number of nodes services
   - `WORLD_SIZE` Number of gpus

2. Configure the training:
   - Accelerate Config
   - Enable Deepspeed 3
   - Accelerate launch train.py

For more information, refer to the [Training SOP](DOCs/TRAINING.md).

---

# Dataset Strategy
Here is a summary table of the key datasets mentioned in the paper:

| Dataset | Tasks | Size | Link |
|-|-|-|-|  
| TAMP | Robotic manipulation planning, VQA | 96,000 scenes | Custom dataset |
| Language Table | Robotic manipulation planning | Custom dataset | [Link](https://github.com/google-research/language-table) |  
| Mobile Manipulation | Robotic navigation and manipulation planning, VQA | 2912 sequences | Based on SayCan dataset |
| WebLI | Image-text retrieval | 66M image-caption pairs | [Link](https://arxiv.org/abs/2209.06794) |
| VQAv2 | Visual question answering | 1.1M questions on COCO images | [Link](https://visualqa.org/) |  
| OK-VQA | Visual question answering requiring external knowledge | 14,031 questions on COCO images | [Link](https://allenai.org/data/ok-vqa) |
| COCO | Image captioning | 330K images with captions | [Link](https://cocodataset.org/) |
| Wikipedia | Text corpus | N/A | [Link](https://en.wikipedia.org) |

The key robotics datasets were collected specifically for this work, while the larger vision-language datasets (WebLI, VQAv2, OK-VQA, COCO) are standard benchmarks in that field. The datasets range from tens of thousands of examples for the robotics domains to tens of millions for the internet-scale vision-language data.

---

## Contribute || Be Part of the PALM-E Adventure 🤝

Your brilliance is needed! Join us, and together, let's make PALM-E even more awe-inspiring:

1. **Get Your Copy**: Fork the PALM-E repo.
2. **Make It Local**: Clone your fork.
3. **Prep Your Tools**: Install the necessities.
4. **Discover & Innovate**: Dive into the code.
5. **Craft Your Magic**: Branch and code away.
6. **Show & Tell**: Push your changes and craft a pull request.

🐞 Fixes, 🎨 enhancements, 📝 docs, or 💡 ideas – all are welcome! Let's shape the future of AI, hand in hand.

---

## Citation
```latex
@article{driess2023palme,
  title={PALM-E: An Embodied Multimodal Language Model},
  author={Driess, Danny and Xia, Fei and Sajjadi, Mehdi S. M. and Lynch, Corey and Chowdhery, Aakanksha and Ichter, Brian and Wahid, Ayzaan and Tompson, Jonathan and Vuong, Quan and Yu, Tianhe and Huang, Wenlong and Chebotar, Yevgen and Sermanet, Pierre and Duckworth, Daniel and Levine, Sergey and Vanhoucke, Vincent and Hausman, Karol and Toussaint, Marc and Greff, Klaus and Zeng, Andy and Mordatch, Igor and Florence, Pete},
  journal={arXiv preprint arXiv:2303.03378},
  year={2023},
  url={https://doi.org/10.48550/arXiv.2303.03378}
}
```

-----

## Roadmap

- [ ] URGENT: Debug Tokenizer, make sure multi-modal inputs work. 
- [ ] Create Dataset Strategy
- [ ] Upload Training Documentation
- [ ] Get Training running with multi-modal

---

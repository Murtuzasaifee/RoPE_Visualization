# RoPE, Explained Visually

**An interactive, slide-by-slide explainer of Rotary Positional Embedding (RoPE), the position encoding used in LLaMA, Mistral, Qwen, Gemma and most modern LLMs.**

[![Live demo](https://img.shields.io/badge/Live%20demo-Open%20the%20explainer-4E0973?style=for-the-badge)](https://murtuzasaifee.github.io/RoPE_Visualization/#1)
![Single HTML file](https://img.shields.io/badge/Single%20file-HTML%20%2B%20JS-7A53A2?style=flat-square)
![No build step](https://img.shields.io/badge/Build-none-C4B0E8?style=flat-square)
![No dependencies](https://img.shields.io/badge/Dependencies-zero-DCA972?style=flat-square)

👉 **[murtuzasaifee.github.io/RoPE_Visualization](https://murtuzasaifee.github.io/RoPE_Visualization/#1)**

---

## Why this exists

Most RoPE explanations jump straight to rotation matrices and complex numbers. This one starts from the problem and builds up to the math one step at a time. Every visual on the way is something you can drag, click or play with.

By the end you should be able to explain RoPE to anyone in 30 seconds:

> Transformers see words as a set, so they can't tell order. RoPE turns each word's vector by an angle set by its position. When two turned vectors are compared, only the angle *between* them is left, which is how far apart the words are. Many "dials" spinning at different speeds track near and far words at once.

---

## The tour

The explainer has 16 chapters, arranged from simple to complete. Each one can be opened directly with its link.

| # | Chapter | What you can do |
|---|---|---|
| [1](https://murtuzasaifee.github.io/RoPE_Visualization/#1) | **Title** | Watch clock hands spin at different speeds, which previews the whole idea |
| [2](https://murtuzasaifee.github.io/RoPE_Visualization/#2) | **The problem** | Swap "dog bites man" and see that attention receives the same input either way |
| [3](https://murtuzasaifee.github.io/RoPE_Visualization/#3) | **First instinct** | Add raw position numbers to a word vector and watch the meaning drown |
| [4](https://murtuzasaifee.github.io/RoPE_Visualization/#4) | **The 2017 fix** | Scan the sinusoidal "fingerprint" heatmap from the original Transformer |
| [5](https://murtuzasaifee.github.io/RoPE_Visualization/#5) | **Where it breaks** | See how adding position bends a word's direction, plus four known issues |
| [6](https://murtuzasaifee.github.io/RoPE_Visualization/#6) | **The RoPE idea** | Rotate a word by its position and notice that its length never changes |
| [7](https://murtuzasaifee.github.io/RoPE_Visualization/#7) | **The math of one turn** | Live 2D rotation formula and matrix, with real numbers |
| [8](https://murtuzasaifee.github.io/RoPE_Visualization/#8) | **The key insight** | Shift the query and key together: the score line stays flat |
| [9](https://murtuzasaifee.github.io/RoPE_Visualization/#9) | **Why it works** | A four-line proof that only the gap *n − m* survives |
| [10](https://murtuzasaifee.github.io/RoPE_Visualization/#10) | **Real vectors** | Watch a vector split into pairs, each pair spinning as its own dial |
| [11](https://murtuzasaifee.github.io/RoPE_Visualization/#11) | **Choosing the speeds** | Explore the frequency ladder θᵢ = base^(−2i/d) and change the base |
| [12](https://murtuzasaifee.github.io/RoPE_Visualization/#12) | **A bonus effect** | See similarity fade with distance across base and dimension settings |
| [13](https://murtuzasaifee.github.io/RoPE_Visualization/#13) | **Inside the model** | Animated attention block showing that Q and K are rotated and V is not |
| [14](https://murtuzasaifee.github.io/RoPE_Visualization/#14) | **Head to head** | Slide a phrase along and compare the wobbling sinusoidal score with RoPE's steady one |
| [15](https://murtuzasaifee.github.io/RoPE_Visualization/#15) | **In code** | About 15 lines of PyTorch, highlighted step by step |
| [16](https://murtuzasaifee.github.io/RoPE_Visualization/#16) | **The limit** | Push past the training length, then switch on position interpolation |
| [17](https://murtuzasaifee.github.io/RoPE_Visualization/#17) | **Take it with you** | The 30-second explanation |

---

## Controls

| Action | Keys / input |
|---|---|
| Next slide or next build step | `→` · `Space` · `↓` · `Page Down` |
| Previous | `←` · `↑` · `Page Up` · `Backspace` |
| First / last slide | `Home` / `End` |
| Full screen | `F` or the floating pill button |
| Touch | Swipe left or right |
| Jump to a slide | Add `#N` to the URL, e.g. `#8` |

Some slides hold extra content that appears in steps; the counter at the bottom shows `step k/n`. Sliders and buttons on each slide drive the visuals directly.

---

## Run it locally

No build step and nothing to install.

```bash
git clone https://github.com/murtuzasaifee/RoPE_Visualization.git
cd RoPE_Visualization
open index.html          # macOS
# or: python3 -m http.server 8000  →  http://localhost:8000
```

---

## How it's built

- **One self-contained HTML file.** All CSS and JavaScript are inline. The only external request is Google Fonts, and system fonts take over if it fails.
- **Vanilla JS, SVG and Canvas.** No frameworks or libraries.
- **A fixed 1920 × 1080 stage** that scales to fit any screen, so it works as a presentation as well as a web page.
- **The math is real.** Every number on screen is computed live: rotations, dot products, the frequency ladder and similarity curves.
- **Animations only run on the active slide**, which keeps things light.
- **Accessibility:** respects `prefers-reduced-motion`, has visible keyboard focus, and printing shows every slide in its final state.
- **Typography:** Archivo for headlines and text, JetBrains Mono for labels and code.

---

## References

- Su, J., Lu, Y., Pan, S., Murtadha, A., Wen, B., & Liu, Y. (2021). *RoFormer: Enhanced Transformer with Rotary Position Embedding.* [arXiv:2104.09864](https://arxiv.org/abs/2104.09864)
- Vaswani, A., et al. (2017). *Attention Is All You Need.* [arXiv:1706.03762](https://arxiv.org/abs/1706.03762)
- Chen, S., Wong, S., Chen, L., & Tian, Y. (2023). *Extending Context Window of Large Language Models via Positional Interpolation.* [arXiv:2306.15595](https://arxiv.org/abs/2306.15595)
- Peng, B., Quesnelle, J., Fan, H., & Shippole, E. (2023). *YaRN: Efficient Context Window Extension of Large Language Models.* [arXiv:2309.00071](https://arxiv.org/abs/2309.00071)

---

## Contributing

Issues and pull requests are welcome, whether it's a clearer explanation, a bug, or a new chapter. If something didn't click for you, that's worth an issue too: the goal is for anyone to be able to follow it.

---

<p align="center"><b>Rotate by where you are. Attend by how far apart you are.</b></p>

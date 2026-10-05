# Cadenced Token Output

![Cadenced Token Output Demo](cadence_loop.gif)

> This is an experiment to see if low tokens per second can be made perceptually more pleasant.
>
> This approach is implemented entirely in the front-end presentation layer; no backend infra needs to be touched.

---

## Cadence Profiles

All cadences operate under a strict causal arrival floor ($d_i \ge a_i$) against a shared **Target Average Rate** (defaulting to 4 TPS). Punctuation and syntactic pauses naturally build a token buffer that fuels subsequent conversational bursts—running 100% causally in real time with zero artificial lookahead:

| Profile | Rhythm & Linguistic Dynamics | Perceptual Character |
| :--- | :--- | :--- |
| **Baseline (Constant)** | Flat, metronomic emission directly on server arrival (`1000 / targetTPS` ms). | Robotic conveyor belt; feels slowest to the eye. |
| **The Contemplative Philosopher** | Broad phrase horizon (cap: 10 tokens). Measured stately tempo (`75ms`), lexical deliberation on conceptual words (`125ms`), followed by deep contemplative silences (`700ms` at periods, `380ms` at clauses). | Deeply thoughtful, cerebral, deliberate. |
| **The Conversationalist** | Short, bite-sized phrasing (cap: 5 tokens). Elastic conversational gliding (`32ms–48ms`) with stochastic mid-sentence thinking hesitations (`+90ms`). | Relaxed, spontaneous, warm, human. |
| **The Syncopated Flow** | Locked into strict 4-token musical bars. Crisp sixteenth-note pocket (`28ms`) slamming into an offbeat bar hold (`160ms`), with musical rests at periods (`340ms`). | Rhythmic, musical, tight, energetic. |
| **The Suspenseful Storyteller** | Asymmetric phrasing (cap: 4 tokens). Creeping, cautious drip (`140ms`) exploding into rapid narrative rushes (`28ms`) upon action triggers, broken by breathless cliffhanger silences (`850ms`). | Gripping, atmospheric, dramatic. |

---

### Run Locally
The app is entirely self-contained in clean HTML5, CSS3, and modern vanilla JavaScript:

```bash
# Clone the repository
git clone https://github.com/EldarMu/CadencedTokenOutput.git
cd CadencedTokenOutput

# Start a local web server
python -m http.server 8080
```
Open **`http://localhost:8080/index.html`** in your browser.


## License
MIT License. If your frontier lab ends up adopting this, you might as well toss me an interview.

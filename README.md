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
| **Baseline (Constant)** | Flat, metronomic emission. Every token receives identical delay (`1000 / targetTPS` ms). | Robotic conveyor belt; feels slowest to the eye. |
| **The Contemplative Philosopher** | Punctuation attaches instantly; contemplative pauses occur *before* subsequent clauses (`300ms–580ms`). Lexical access delays on deep words (`>7` characters). Rapid burst through connective syllables. | Deeply thoughtful, cerebral, deliberate. |
| **The Conversationalist** | Elastic human phrasing with quick latching on short words (`<=3` chars) and stochastic micro-hesitations (`110ms`) mimicking natural spoken speech. | Relaxed, spontaneous, warm, human. |
| **The Syncopated Flow** | Metric bounce locked into a 4-beat pocket (3 sixteenth notes in the pocket followed by an offbeat bar hold). | Rhythmic, musical, tight, energetic. |
| **The Suspenseful Storyteller** | Extended breath-holding silences between sentences (`750ms`), dramatic tension across dashes, followed by sudden high-speed narrative bursts. | Gripping, atmospheric, dramatic. |

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

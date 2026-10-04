# Cadenced Token Output

![Cadenced Token Output Demo](cadence_loop.gif)

> **This is an experiment to see if low tokens per second can be made perceptually more pleasant.**
> 
> *"Can we make low tokens per second feel good for the user? Yes, with cadenced output, which for some strange, unexplicable reason, feels like it travels across the screen faster, though each ends at the same time."*
>
> **Pure Front-End Solution:** This approach requires **no changes to the serving infrastructure or backend models**—it is implemented entirely in the front-end presentation layer.

---

## The Core Thesis

> [!NOTE]
> **Zero Infrastructure Overhead:** This approach requires no modifications to model weights, inference servers, or streaming API protocols. The backend emits tokens as normal; a lightweight client-side display layer buffers and shapes the emission timing into natural human cadence purely in the browser UI.

Current LLM interfaces stream text like a teleprompter or industrial conveyor belt: rigid, linear, and monotonic. When server capacity is constrained or reasoning models run at low token velocities (e.g., 4 to 6 tokens per second), mechanical flat streaming feels agonizingly slow and robotic.

Yet humans never speak like teleprompters. In genuine speech and thought:
- We glide effortlessly through obvious connective tissue.
- We pause at clause and sentence boundaries to breathe and gather thought.
- We hesitate slightly before heavy conceptual terms while accessing vocabulary.
- We burst through punchy punchlines and emphasize dramatic verbs.

**The Hypothesis:** If an AI model's output is shaped by linguistic cadence, the exact same low token budget feels dramatically more engaging, natural, and tolerable to human readers than constant mechanical delivery.

---

## Cadence Profiles

All cadences are calibrated against a shared **Target Average Rate** (defaulting to 4 TPS), ensuring all streams finish in the exact same elapsed time while exhibiting wildly different perceptual dynamics:

| Profile | Rhythm & Linguistic Dynamics | Perceptual Character |
| :--- | :--- | :--- |
| **Baseline (Constant)** | Flat, metronomic emission. Every token receives identical delay (`1000 / targetTPS` ms). | Robotic conveyor belt; feels slowest to the eye. |
| **The Contemplative Philosopher** | Punctuation attaches instantly; contemplative pauses occur *before* subsequent clauses (`300ms–580ms`). Lexical access delays on deep words (`>7` characters). Rapid burst through connective syllables. | Deeply thoughtful, cerebral, deliberate. |
| **The Conversationalist** | Elastic human phrasing with quick latching on short words (`<=3` chars) and stochastic micro-hesitations (`110ms`) mimicking natural spoken speech. | Relaxed, spontaneous, warm, human. |
| **The Syncopated Flow** | Metric bounce locked into a 4-beat pocket (3 sixteenth notes in the pocket followed by an offbeat bar hold). | Rhythmic, musical, tight, energetic. |
| **The Suspenseful Storyteller** | Extended breath-holding silences between sentences (`750ms`), dramatic tension across dashes, followed by sudden high-speed narrative bursts. | Gripping, atmospheric, dramatic. |

---

## Live High-Resolution Telemetry

Every stream box includes a unified, single-line telemetry header:

- **Cadence Name & Live Status:** Tracks active state (`Ready`, `Streaming...`, `Completed (X tokens)`).
- **3s Avg:** High-frequency rolling token throughput over the last 3,000 milliseconds.
- **30s Avg:** Macro throughput over the run, displayed as a stable integer.
- **Now:** Instantaneous throughput (rolling 500ms window) with a responsive gradient gauge bar.
- **Zero-Decay Freeze Lock:** Once streaming completes, rolling metrics immediately freeze, locking the exact achieved performance permanently without trailing decay.

---

## Getting Started

### 1. Run Locally
The app is entirely self-contained in clean HTML5, CSS3, and modern vanilla JavaScript:

```bash
# Clone the repository
git clone https://github.com/EldarMu/CadencedTokenOutput.git
cd CadencedTokenOutput

# Start a local web server
python -m http.server 8080
```
Open **`http://localhost:8080/index.html`** in your browser.



## One-Click GitHub Pages Hosting

To host this live on GitHub Pages:
1. Push this repository to GitHub.
2. Go to **Settings** &rarr; **Pages**.
3. Under **Branch**, select `main` and `/ (root)`.
4. Click **Save**. Your Cadenced Token Output app will be instantly live at `https://eldarmu.github.io/CadencedTokenOutput/`.

---

## License
MIT License. Free to use, adapt, and build upon.

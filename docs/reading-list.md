# Reading list

Ordered for someone new to both connectomics and agent engineering. You don't need to read everything before starting. Read **Tier 1** first, then pick up the rest as each phase needs it.

For each paper there is a question to keep in mind while reading. Write a one-line answer in your notes; those answers feed directly into design decisions.

---

## Tier 1: start here (about a week)

### Connectomics foundations

1. **Dorkenwald et al. (2024). "Neuronal wiring diagram of an adult brain."** *Nature.*
   The FlyWire whole-brain connectome of a female fly. Read the intro and figures; skim the methods.
   *Question:* What exactly is a "connection" in this data, and what decides whether one is counted?

2. **Schlegel et al. (2024). "Whole-brain annotation and multi-connectome cell typing of Drosophila."** *Nature.*
   Compares FlyWire with the earlier hemibrain dataset: how consistent are cell types and connections between two animals? This is the scientific basis for this project's replication check.
   *Question:* Above what connection strength do connections reliably appear in both animals?

3. **Berg et al. (2025/2026). "Sexual dimorphism in the complete connectome of the Drosophila male central nervous system."** [bioRxiv](https://www.biorxiv.org/content/10.1101/2025.10.09.680999.full.pdf), now published in *Cell*.
   The male CNS dataset you will query through neuPrint: brain and nerve cord in one animal, plus male–female comparison.
   *Question:* What do "isomorphic", "dimorphic" and "sex-specific" cell types mean, and how were they decided?

### Agent-engineering foundations

4. **Anthropic (2024). "Building effective agents."** Engineering blog post.
   Short and practical: workflows vs agents, and why to start simple without frameworks. It applies to any model provider.
   *Question:* Which parts of this project are a fixed *workflow*, and which genuinely need an *agent* to decide its own steps?

5. **Yao et al. (2023). "ReAct: Synergizing Reasoning and Acting in Language Models."** *ICLR.*
   The original reason → act → observe loop that the Phase 1 loop is based on.
   *Question:* What goes wrong when a model acts without reasoning, or reasons without acting?

---

## Tier 2: before Phase 1 (tools and data)

6. **Plaza et al. (2022). "neuPrint: an open access tool for EM connectomics."** *Frontiers in Neuroinformatics.*
   How the database you'll query is organised: neurons, synapses, ROIs (brain regions) and cell types.
   *Question:* What is the smallest query that answers "who does neuron X talk to?"

7. **Yang et al. (2024). "SWE-agent: Agent-Computer Interfaces Enable Automated Software Engineering."** *NeurIPS.*
   Shows that *how tools are designed* (what they return, how errors look) changes agent performance as much as the model does.
   *Question:* What would a "good interface" for a connectome tool look like by their standard?

---

## Tier 3: before Phase 2 (behaviours with known answers to build the benchmark)

These are classic circuits whose answers you can check. Good material for your first eval questions.

8. **von Reyn et al. (2014). "A spike-timing mechanism for action selection."** *Nature Neuroscience.*
   The giant fibre and escape takeoff: how a fly chooses between a fast and a slow escape.

9. **Bidaye et al. (2014). "Neuronal control of Drosophila walking direction."** *Science.*
   Moonwalker descending neurons (MDN) and backward walking.

10. **Namiki et al. (2018). "The functional organization of descending sensory-motor pathways in Drosophila."** *eLife.*
    A map of the descending neurons, the brain-to-body "command" layer your agent will trace through.

*Question for all three:* Write each finding as a set of edges (neuron → neuron). Which ones could an agent verify from the connectome alone, and which need physiology data?

---

## Tier 4: before Phase 3 (replication, rigour, the second connectome)

11. **Bates, Yang et al. (2026). "Distributed control circuits across a brain-and-cord connectome."** *Nature.* (BANC)
    A female brain *and* nerve cord in one animal, giving an independent counterpart to the male CNS for brain-to-motor paths.
    *Question:* What does "distributed control" imply for an agent looking for a single command neuron?

12. **"Infrequent strong connections constrain connectomic predictions of neuronal function"** (2025). [bioRxiv](https://www.biorxiv.org/content/10.1101/2025.03.06.641774.full.pdf)
    Argues that a few strong connections carry most of the predictive information, which bears on how to set the agent's weight thresholds.
    *Question:* Should the agent threshold on absolute synapse count, or on the fraction of a neuron's input?

---

## Tier 5: closest prior work (read before writing anything public)

13. **"Neural Circuit Function Inference with LLMs"** (LLantia, 2026). [arXiv:2608.00059](https://arxiv.org/pdf/2608.00059)
    Uses LLMs plus literature plus the connectome to infer cell-type functions across the fly brain. The closest existing work to this project.
    *Question:* What exactly does it validate, and what doesn't it? Check this before claiming any gap.

14. **"ConnectomeBench: Can LLMs Proofread the Connectome?"** (NeurIPS 2025 Datasets & Benchmarks). [arXiv:2511.05542](https://arxiv.org/abs/2511.05542)
    A benchmark for a different task (proofreading), but a useful model for how to build and report a connectomics benchmark.
    *Question:* How do they score models, and what would the equivalent be for circuit reasoning?

---

## Stretch: wiring → function

15. **Shiu et al. (2024). "A Drosophila computational brain model reveals sensorimotor processing."** *Nature.*
    Simulates the whole fly brain as spiking neurons wired by the connectome and checks predictions experimentally. Read this for the stretch-goal simulation.

16. **Lappalainen et al. (2024). "Connectome-constrained networks predict neural activity across the fly visual system."** *Nature.*
    Shows that the wiring alone, with unknown parameters fitted, can predict measured activity in the motion pathway.

17. **Scheffer et al. (2020). "A connectome and analysis of the adult Drosophila central brain."** *eLife.*
    The hemibrain, the dataset that started this era. Useful background on how the data is produced and its known limitations.

---

*Notes:* Tier 1–2 citations are from memory; check details (year, venue) against the papers. Newer entries were confirmed by web search on 2026-11-16, but full texts were not reviewed.

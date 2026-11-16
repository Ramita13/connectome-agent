# connectome-agent

An LLM agent that proposes candidate neural circuits from connectomes and backs every link with evidence that can be checked. It starts with the fruit fly (*Drosophila*), the only animal with complete, independently reconstructed connectomes from more than one individual.

> **Status:** early work in progress. No agent code yet.
> This is a personal learning project, built one small piece at a time to learn connectomics and how to engineer agentic AI systems.

---

## The question

Fruit flies now have complete synapse-level wiring maps (connectomes) of the brain and nerve cord, from more than one animal. A map is not an explanation, though. Getting from "neuron A connects to neuron B" to "this circuit makes the fly jump away from a looming threat" is slow expert work, and it is easy to get wrong:

- **Everything is close to everything.** In a dense graph almost any two neurons are linked within a few hops, so a short path is not a circuit.
- **Weak connections don't replicate.** Connection strengths vary between animals. Strong connections are largely conserved; weak ones often aren't.
- **Cell types don't always transfer** cleanly between datasets reconstructed by different teams.

**Can a tool-using agent turn connectome queries into circuit hypotheses where every link is traceable to a query, replicates across independently reconstructed animals, and is honestly labelled as known or new? And can we measure how often it gets them right?**

## What the agent does (planned)

Ask it about a behaviour, for example *"How does looming visual input reach the escape jump?"* It will:

1. Find relevant neurons and cell types.
2. Trace candidate pathways from sensory neurons through descending neurons to motor neurons, using synapse-weight thresholds.
3. Check whether each link replicates in a second, independent connectome.
4. Check the literature for whether each link is already known.
5. Pass its claims to a reviewer agent that sees the evidence but not the agent's reasoning, and labels each claim **accepted**, **qualified** or **blocked**.

## Acknowledgements

This project relies entirely on the connectome datasets and tools produced by the FlyEM (Janelia), FlyWire and BANC teams. Please cite their papers (see the [reading list](docs/reading-list.md)) if you use anything from here.

# Enuma

A cognitive memory layer for AI agents with importance propagation, time decay, and pressure-based eviction.

## Install

```bash
git clone https://github.com/Milkybanana1/enuma.git
cd enuma
pip install -e .
```

## Usage

```python
from enuma import Engine

memory = Engine(max_slots=500, half_life=3600, decay_rate=0.3)
memory.add_node('user_profile')
memory.access('user_profile')
hot = memory.get_hot_cluster(threshold=0.5)
```

## How it works

- **Propagation:** When a node is accessed, importance boosts propagate to neighbors, normalized by node degree to prevent hub flooding.
- **Time decay:** Effective importance decays exponentially based on time since last access, halving after the configured half-life.
- **Eviction:** When memory is full, the node with the lowest effective importance (not base importance) is evicted.

## Run the demo

```bash
python examples/demo.py
```

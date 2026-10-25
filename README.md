# Eagle Delivery

Eagle Delivery is a grid-based campus delivery simulator. It compares BFS and
A* route search and uses tabular Q-learning to learn delivery policies.

## Run commands

Run these commands from the project root.

```bash
# Search examples
python run_project.py search --map maps/emu_campus.txt --algorithm bfs --start S --goal W
python run_project.py search --map maps/emu_campus.txt --algorithm astar --start S --goal W
python run_project.py search --map maps/emu_detour.txt --algorithm astar --start L --goal D
python run_project.py search --map maps/my_campus.txt --algorithm bfs --start S --goal W
python run_project.py search --map maps/my_campus.txt --algorithm astar --start S --goal W

# Part B baseline Q-learning runs
python run_project.py train --start S --goal W --output results/baseline_SW
python run_project.py train --start L --goal D --output results/baseline_LD
python run_project.py train --start H --goal P --output results/baseline_HP

# Part C epsilon experiment
python run_project.py train --map maps/my_campus.txt --start S --goal W --epsilon 0.05 --output results/custom_e005
python run_project.py train --map maps/my_campus.txt --start S --goal W --epsilon 0.2 --output results/custom_e020
python run_project.py train --map maps/my_campus.txt --start S --goal W --epsilon 0.5 --output results/custom_e050

# Summarize a run and generate its learning-curve CSV
python summarize_results.py results/baseline_SW
python summarize_results.py results/baseline_LD
python summarize_results.py results/baseline_HP
python summarize_results.py results/custom_e005
python summarize_results.py results/custom_e020
python summarize_results.py results/custom_e050
```

## Experiment settings

- **Part B:** Baseline campus map; tasks S -> W, L -> D, and H -> P, 2,000 training
  episodes, seeds 0, 1, and 2, 100 evaluation episodes per seed, 200-action
  limit, a = 0.3; y = 0.95, explanation rate = 0.2, slip = 0.0
- **Part C:** Custom map, S -> W; explanation rate = 0.05, 0.2, and 0.5, seeds 0, 1, and 2,
  2,000 training episodes, 100 evaluation episodes per seed, 200-action limit,
  a = 0.3, y = 0.95, slip = 0.0

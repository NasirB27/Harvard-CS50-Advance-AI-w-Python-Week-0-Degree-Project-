# Degrees - Six Degrees of Separation

**CS50 AI - Week 0, Project 1**

> CS50 AI Week 0 Project 1: Implements BFS algorithm to find shortest degree of separation between actors using IMDb data

## Overview
Implementation of a breadth-first search (BFS) algorithm that determines the shortest path between any two actors by identifying shared movie connections. Based on the "Six Degrees of Kevin Bacon" concept.

## Problem Statement
Given two actors, find the shortest sequence of movies that connects them, where each step consists of finding a movie that both actors starred in.

**Example:**
- Jennifer Lawrence → Kevin Bacon (via X-Men: First Class) 
- Kevin Bacon → Tom Hanks (via Apollo 13)
- **Result:** 2 degrees of separation

## Implementation
The solution uses:
- **BFS algorithm** for optimal path finding (guarantees shortest path)
- **Queue-based frontier** for level-order traversal
- **Node tracking** with parent pointers for path reconstruction
- **Explored set** for cycle prevention

## Key Components
```python
def shortest_path(source, target):
    """
    Returns the shortest list of (movie_id, person_id) pairs
    that connect the source to the target.
    If no possible path, returns None.
    """
```

### Algorithm Features
- **Time Complexity:** O(V + E) where V = actors, E = movie connections
- **Space Complexity:** O(V) for frontier + explored set
- **Optimality:** Guaranteed shortest path via BFS

## Data Structure
- `people.csv` - Actor IDs, names, birth years
- `movies.csv` - Movie IDs, titles, release years  
- `stars.csv` - Actor-Movie relationships

## Usage
```bash
python degrees.py [directory]

# Examples:
python degrees.py small  # Test with small dataset
python degrees.py large  # Full IMDb dataset
```

### Example Output
```
$ python degrees.py large
Loading data...
Data loaded.
Name: Emma Watson
Name: Jennifer Lawrence
3 degrees of separation.
1: Emma Watson and Brendan Gleeson starred in Harry Potter and the Order of the Phoenix
2: Brendan Gleeson and Michael Fassbender starred in Trespass Against Us
3: Michael Fassbender and Jennifer Lawrence starred in X-Men: First Class
```

## Project Structure
```
degrees/
├── degrees.py          # Main implementation
├── util.py            # Helper classes (Node, Frontiers)
├── small/             # Test dataset
│   ├── people.csv
│   ├── movies.csv
│   └── stars.csv
├── large/             # Full dataset
│   ├── people.csv
│   ├── movies.csv
│   └── stars.csv
└── README.md
```

## Learning Outcomes
- Graph traversal algorithms (BFS vs DFS)
- State space search strategies
- Path reconstruction using parent pointers
- Optimization for shortest path problems
- Understanding unweighted graph shortest paths

## Algorithm Explanation

### How BFS Guarantees Shortest Path
1. Explores nodes layer-by-layer (level-order traversal)
2. All 1-degree connections checked before 2-degree
3. All 2-degree connections checked before 3-degree
4. First path found is guaranteed to be shortest

### Why Not DFS?
- DFS explores depth-first, may find long paths first
- Would need to explore ALL paths to guarantee optimality
- No systematic guarantee of minimum path length

## Testing
```bash
# Check correctness
check50 ai50/projects/2024/x/degrees

# Check code style
style50 degrees.py
```

## Technologies
- Python 3.12
- CSV data processing
- Graph algorithms
- Search strategies

---

**Course:** Harvard CS50's Introduction to Artificial Intelligence with Python  
**Week:** 0 - Search  
**Project:** 1 of 2 (Degrees)  
**Completion Date:** October 31, 2025

## Author
Senior UX Engineer studying AI/ML fundamentals for design system architecture and automation applications.

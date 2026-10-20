# PathQuest

Interactive path-finding visualizer: draw walls or generate a maze, then watch Dijkstra, A*, BFS and DFS search the grid.

![HTML5](https://img.shields.io/badge/HTML5-E34F26?logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?logo=javascript&logoColor=black)
![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)

**Live demo:** [aryandeswal.github.io/PathQuest](https://aryandeswal.github.io/PathQuest)

## About

PathQuest animates how classic graph-search algorithms explore a grid. Place a start node, an end node and walls, pick an algorithm, and the visualizer colours each cell as it is discovered and visited, then traces the final path. The goal is to make the differences between these algorithms easy to see side by side. It is plain HTML, CSS and JavaScript with no dependencies or build step.

## Features

- **Four algorithms**
  - **Dijkstra**: expands the node with the smallest distance from the start.
  - **A\***: orders nodes by distance travelled plus a Manhattan-distance heuristic to the end node.
  - **Breadth-First Search (BFS)**: explores the grid level by level.
  - **Depth-First Search (DFS)**: follows one branch as deep as it can, then backtracks. Its path is not guaranteed to be the shortest.
- **Maze generation** using the recursive backtracking algorithm, with animation.
- **Interactive grid** (50 × 25 cells on an HTML5 canvas): click to place or remove the start and end nodes, drag with the left mouse button to draw walls, and drag with the middle mouse button to erase them.
- **Animated search**: discovered, visited and final-path cells each get their own colour, and a legend explains them.
- **Algorithm descriptions** are shown in a message box when you select an algorithm.
- **Clear Path** keeps your walls and removes the search results. **Reset Grid** clears everything and places new random start and end nodes.

Every move between neighbouring cells (up, down, left, right) costs the same, so the interesting difference is how much of the grid each algorithm explores before it reaches the end node.

## Tech Stack

- HTML5 Canvas for the grid and animations
- CSS3 for layout and styling
- Vanilla JavaScript (ES modules)

## Project Structure

```
PathQuest/
├── index.html                  # Page layout, controls, instructions and legend
├── scripts/
│   ├── app.js                  # Entry point: event handling and wiring of controls
│   ├── grid.js                 # Grid creation, drawing, mouse-to-cell mapping
│   ├── node.js                 # Node class, neighbour lookup, path reconstruction, animation
│   ├── nodeColor.js            # Colour palette for node states
│   └── algorithms/
│       ├── Dijakstra.js        # Dijkstra's algorithm
│       ├── Astar.js            # A* search (Manhattan heuristic)
│       ├── bfs.js              # Breadth-first search
│       ├── dfs.js              # Depth-first search
│       └── RecursiveBacktrack.js  # Maze generation
├── styles/                     # Stylesheets
└── media/                      # Favicon and instruction images
```

## Getting Started

The scripts are loaded as ES modules, and browsers block those on `file://` URLs. Serve the folder over HTTP instead of opening `index.html` directly:

```bash
git clone https://github.com/AryanDeswal/PathQuest.git
cd PathQuest
python3 -m http.server 8000
```

Then open `http://localhost:8000`. Any static file server works, and so does the VS Code Live Server extension.

## Usage

1. A start node and an end node are placed at random when the page loads. Left-click either one to remove it, then left-click an empty cell to place it again.
2. Drag with the left mouse button to draw walls, and drag with the middle mouse button to erase them. You can also click **Generate Maze**.
3. Choose an algorithm from **Choose Algorithm**.
4. Click **Visualize** to run it.
5. Use **Clear Path** to try another algorithm on the same walls, or **Reset Grid** to start over.

## License

Released under the [MIT License](LICENSE).

# Procedural 3D Maze Game

A first-person maze game built in Godot. Every playthrough generates a new maze, lit only by
the torch you carry, with framed paintings hung on the walls and something moving in the dark. Built as a university graphics project.

## How it works

**Maze generation.** Levels are generated with randomized Kruskal's algorithm over a grid of cells, using a union-find (disjoint-set) structure to track connectivity. Each cell starts in its own set. Walls are considered in random order: if the cells on either side belong to different sets, the wall is removed and the two sets are merged; if they already share a set, a path between them exists and the wall stays, preventing loops. The process ends when every cell belongs to one set. The result is a uniform spanning tree — every playthrough is unique, every cell is reachable, and there are no isolated regions.

**Wall artwork.** Paintings are hung procedurally at runtime. Rather than using fixed-size
frames, the canvas mesh is generated from each source image's aspect ratio, so tall and wide
paintings both hang correctly and stand out from the wall surface instead of being flattened
onto it.

**Lighting.** The maze is unlit except for a flickering torch light attached to the player. Very spooky.

## Running it

1. Install [Godot](https://godotengine.org/download) (version 4.2 — see `project.godot`)
2. Open the project folder in Godot
3. Press F5, or click Play

Controls: WASD to move, mouse to look.

## Project structure

```
scenes/     Game, Wall, Floor, Painting
scripts/    Maze generation, player controller, enemy, lighting
artwork/    Source images for wall paintings
materials/  Wall and floor materials
```

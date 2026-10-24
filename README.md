# Banter Tic-Tac-Toe

A simple, fully synchronized multiplayer Tic-Tac-Toe game designed for the Banter platform.

## Description

This script creates a complete Tic-Tac-Toe game within a Banter space. The game state is synchronized across all players using Banter's public space properties, ensuring that everyone sees the same game board and turns are handled correctly.

The game board and pieces are created using Banter's primitive geometry, and the script includes a simple UI for resetting the game.

## How to Use

1.  **Place the Script:** Make sure the `TicTacToe.js` script is hosted in a location accessible to your Banter space.
2.  **Add to Your Space:** In your Banter space, add an "Embed" with the URL pointing to your hosted `TicTacToe.js` script.

The script will automatically initialize, draw the game board, and handle all game logic and synchronization.

## SideQuest / Altspace Creator SDK (Snippet)

In a SideQuest/Altspace Creator SDK world, add an empty GameObject at the origin, click **Add Component > BS > Snippet** and type `tic-tac-toe`. Or paste it into `Assets/WebRoot/index.html` between the snippet section comments:

```html
<!-- snippet section -->
<bs-snippet name="tic-tac-toe" title="Tic-Tac-Toe"
  description="Synced multiplayer upright Tic-Tac-Toe board with a reset button."
  script="https://tic-tac-toe.firer.at/snippet.js"
  room=""
  position="0 1.2 2"
  rotation="0 0 0"
  scale="1"
  lighting="unlit"
  add-lights="true"
  hide-ui="false"
  hide-board="false"
  use-custom-models="false"
  reset-position="0 -0.4 0">
  <bs-gizmo type="position" attribute="position"/>
  <bs-gizmo type="plane" attribute="position" size="0.55 0.55"/>
</bs-snippet>
<!-- end snippet section -->
```

- Settings are the same as the script attributes above. `position` and `rotation` are Unity world values, and `scale` can be a single number.
- Each placement is its own game. Its sync id is `room`, or the placement's own id when `room` is empty. Give placements the same `room` to share one game.
- An empty setting uses the game's default.
- The Scene-view gizmo shows the board at its default size; it does not follow `scale`.
- Unity reads the snippet section as XML: quote every attribute, close every element, and write `&` as `&amp;`.

## Configuration

You can customize the game's appearance and behavior using **HTML script attributes** (recommended) or legacy **URL query parameters** (for backwards compatibility).

**HTML Script Attributes Example (Recommended):**
```html
<script src="https://banter-tic-tac-toe.firer.at/TicTacToe.js" instance="game1" boardScale="1.5 1.5 1.5"></script>
```

**Legacy URL Query Parameters Example:**
```html
<script src="https://banter-tic-tac-toe.firer.at/TicTacToe.js?instance=game1&boardScale=1.5+1.5+1.5"></script>
```

### Available Attributes / Parameters

| Parameter / Attribute | Type          | Default                               | Description                                                                                             |
| ----------------- | ------------- | ------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| `instance`        | `string`      | (Current URL)                         | An ID to distinguish between multiple game instances. Players in spaces with the same instance ID will be synced. |
| `boardPosition` / `position` / `board-position`   | `Vector3 (string)` | `"0 1.2 0"`                           | The `X Y Z` position of the game board in world space. Values are space-separated.                      |
| `boardRotation` / `rotation` / `board-rotation`   | `Vector3 (string)` | `"0 0 0"`                             | The `X Y Z` euler rotation of the game board.                                                           |
| `boardScale` / `scale` / `board-scale`      | `Vector3 (string)` | `"1 1 1"`                             | The `X Y Z` scale of the entire game object.                                                            |
| `resetPosition` / `reset-position`   | `Vector3 (string)` | `"0 -0.4 0"`                          | The `X Y Z` position of the reset button, relative to the board.                                        |
| `resetRotation` / `reset-rotation`   | `Vector3 (string)` | `"0 0 0"`                             | The `X Y Z` euler rotation of the reset button.                                                         |
| `resetScale` / `reset-scale`      | `Vector3 (string)` | `"1 1 1"`                             | The `X Y Z` scale of the reset button.                                                                  |
| `hideUI` / `hide-ui`          | `boolean`     | `false`                               | Set to `true` to hide the reset button.                                                                 |
| `hideBoard` / `hide-board`       | `boolean`     | `false`                               | Set to `true` to hide the game board.                                                                   |
| `useCustomModels` / `use-custom-models` | `boolean`   | `false`                               | Set to `true` to use custom 3D models for pieces.                                                       |
| `lighting`        | `string`      | `"unlit"`                             | Shader mode: `lit` or `unlit`.                                                                          |
| `addLights` / `add-lights`       | `boolean`     | `true`                                | Set to `false` to prevent adding default lights when in lit mode.                                       |

---
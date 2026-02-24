---
layout: post
codemirror: true
title: Game Runner Examples
description: Learn game development using the GameEngine framework in a contained educational environment. Build game levels, add characters, and create interactive experiences with live code editing and debugging controls.
permalink: /rpg/games


---


## Basic Game: Desert Adventure


{% capture challenge1 %}
Run the basic desert adventure game. Use WASD or arrow keys to move Chill Guy around the desert. Walk up to R2D2 to trigger a mini-game!
{% endcapture %}


{% capture code1 %}
import GameControl from '/assets/js/adventureGame/GameEngine/GameControl.js';
import GameEnvBackground from '/assets/js/adventureGame/GameEngine/GameEnvBackground.js';

import GameControl from '/assets/js/adventureGame/GameEngine/GameControl.js';
import GameEnvBackground from '/assets/js/adventureGame/GameEngine/GameEnvBackground.js';
import Player from '/assets/js/adventureGame/GameEngine/Player.js';
import Npc from '/assets/js/adventureGame/GameEngine/Npc.js';

class CustomLevel {
  constructor(gameEnv) {
    const path = gameEnv.path;
    const width = gameEnv.innerWidth;
    const height = gameEnv.innerHeight;

    // ── Background ──────────────────────────────────────────────────────────
    const bgData = {
      name: 'alien_world',
      src: path + "/images/about/miami.webp",
      pixels: { height: 600, width: 1000 }
    };

    // ── Player ──────────────────────────────────────────────────────────────
    // Sprite sheet with walk/idle/attack animations
    const playerData = {
      name: 'hero',
      // Swap this src for any sprite sheet you have in your assets
      src: path + "/images/gamify/mario.png",
      pixels: { height: 256, width: 512 },   // full sprite-sheet size
      orientation: { rows: 4, cols: 8 },      // layout of frames
      down:  { row: 0, start: 0, columns: 3 },
      left:  { row: 1, start: 0, columns: 3 },
      right: { row: 2, start: 0, columns: 3 },
      up:    { row: 3, start: 0, columns: 3 },
      idle:  { row: 0, start: 0, columns: 1 },
      scale: 2,
      // Starting position (fraction of canvas)
      xPercentage: 0.2,
      yPercentage: 0.8,
      // Physics
      speed: 4,
      hitbox: { widthPercentage: 0.45, heightPercentage: 0.2 },
      // Keyboard bindings
      keypress: {
        up:    ['ArrowUp',    'w', 'W'],
        down:  ['ArrowDown',  's', 'S'],
        left:  ['ArrowLeft',  'a', 'A'],
        right: ['ArrowRight', 'd', 'D'],
      },
    };

    // ── NPC ─────────────────────────────────────────────────────────────────
    const npcData = {
      name: 'townsfolk',
      // Swap for any NPC sprite you have
      src: path + "/images/gamify/tux.png",
      pixels: { height: 256, width: 256 },
      orientation: { rows: 4, cols: 4 },
      down:  { row: 0, start: 0, columns: 4 },
      left:  { row: 1, start: 0, columns: 4 },
      right: { row: 2, start: 0, columns: 4 },
      up:    { row: 3, start: 0, columns: 4 },
      idle:  { row: 0, start: 0, columns: 1 },
      scale: 2,
      xPercentage: 0.7,
      yPercentage: 0.8,
      hitbox: { widthPercentage: 0.45, heightPercentage: 0.2 },
      // Simple patrol behaviour – move left/right between two x fractions
      patrol: { minXPercentage: 0.55, maxXPercentage: 0.85, speed: 1.5 },
      // Dialogue shown when the player walks up and presses 'e'
      dialogue: [
        "Welcome to Miami, stranger!",
        "Watch out – this city never sleeps.",
        "Press E again to close this dialog."
      ],
      interact: 'e',   // key to start / advance dialogue
    };

    // ── Class list (order = render order) ───────────────────────────────────
    this.classes = [
      { class: GameEnvBackground, data: bgData },
      { class: Player,            data: playerData },
      { class: Npc,               data: npcData },
    ];
  }
}

export { GameControl };
export const gameLevelClasses = [CustomLevel];
{% endcapture %}


{% include game-runner.html
  runner_id="game1"
  challenge=challenge1
  code=code1
  height="150px"
%}




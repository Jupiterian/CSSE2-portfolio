---
layout: post
codemirror: true
title: Sprint 6 Final Project Skills - Game Runner Complete Setup
description: Final Level Deployments utilizing GameRunner Notebook integrations. 
permalink: /sprint6-game-runner-skills
---

## Table of Contents
* TOC
{:toc}


## 6. Complete Playable Custom Level (Game Runner Integration)
This covers deploying the full code suite inside the markdown architecture by referencing our imported Object files using ES6 modules.

### Custom Level Data-Driven Design
Using `GameSetup.js` and standard Configuration `Object Literals` mapping sprites to Game Layers. Connecting our assets directly to our custom engine architecture.

{% capture game_challenge %}
Launch Level 1 utilizing the exact GameRunner script layout to initialize the canvas and inject the mapped Array of Classes into the global Environment loop.
{% endcapture %}

{% capture game_code %}
// Simulated ES6 Imports
import GameControl from '/assets/js/GameEnginev1.1/essentials/GameControl.js';
import GameEnvBackground from '/assets/js/GameEnginev1.1/essentials/GameEnvBackground.js';
import Player from '/assets/js/GameEnginev1.1/essentials/Player.js';
import Enemy from '/assets/js/GameEnginev1.1/essentials/Enemy.js';

class CustomPeppaLevel {
  constructor(gameEnv) {
    // GameEnv Configuration mapping parameters
    const path = gameEnv.path;
    const width = gameEnv.innerWidth;
    const height = gameEnv.innerHeight;
    
    // Object Literal definition mapping to the background
    const bgData = {
        name: 'peppa-lvl1-arena',
        src: path + "/images/projects/peppa-pig/peppa-pig-background.jpg",
        pixels: { height: 720, width: 1280 }
    };
    
    const playerData = {
      id: 'Ishan Player',
      src: path + "/images/projects/peppa-pig/ishan-jha.png",
      SCALE_FACTOR: 5,
      STEP_FACTOR: 1000,
      ANIMATION_RATE: 50,
      INIT_POSITION: { x: 100, y: 300 },
      pixels: { height: 512, width: 384 },
      orientation: { rows: 4, columns: 3 },
      down: { row: 0, start: 0, columns: 3 },
      hitbox: { widthPercentage: 0.45, heightPercentage: 0.2 },
      keypress: { up: 87, left: 65, down: 83, right: 68 } // Keyboard Input Data
    };

    // Instantiate game objects in GameLevel configuration Array
    this.classes = [
      { class: GameEnvBackground, data: bgData },
      { class: Player, data: playerData },
    ];
  }
}

export { GameControl };
export const gameLevelClasses = [CustomPeppaLevel];
{% endcapture %}

{% include runners/game.html runner_id="peppa_game1" challenge=game_challenge code=game_code %}

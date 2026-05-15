---
layout: post
codemirror: true
title: Sprint 6 Final Project Skills - Game Runner Integration
description: GameEnv config, canvas rendering, key events
permalink: /sprint6-game-runner-skills
---

## 5. Game Runner Integration
Pulling elements together dynamically via our `GameEnginev1.1` and `game-runner`. We specify `GameLevel` rules mapping Keyboard Keypress bounds and Background data parameters correctly.

**Skills Demonstrated:** 
- Keyboard Input configurations via Object Literals (WASD etc.)
- Canvas Rendering handling by `GameEnv` and Engine classes
- Component instantiations directly attached to our runner array

{% capture game_challenge %}
Launch a bare-bones implementation modeled on PeppaBattleLevelBase. Note this imports from the Engine standard directory logic using our player properties.
{% endcapture %}

{% capture game_code %}
// Direct import using GameEngine structure
import GameControl from '/assets/js/GameEnginev1.1/essentials/GameControl.js';
import GameEnvBackground from '/assets/js/GameEnginev1.1/essentials/GameEnvBackground.js';
import Player from '/assets/js/GameEnginev1.1/essentials/Player.js';

class CustomPeppaLevel {
  constructor(gameEnv) {
    const path = gameEnv.path;
    const width = gameEnv.innerWidth;
    const height = gameEnv.innerHeight;
    
    // Configurations mimicking our PeppaBattleLevelBase Level 1
    const bgData = {
        name: 'peppa-lvl1-arena',
        src: path + "/images/projects/peppa-pig/peppa-pig-background.jpg",
        pixels: { height: 720, width: 1280 }
    };
    
    // Player mapped with keys using WASD
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
      keypress: { up: 87, left: 65, down: 83, right: 68 } 
    };

    // Linking instantiated Objects to our Canvas Environment array
    this.classes = [
      { class: GameEnvBackground, data: bgData },
      { class: Player, data: playerData },
    ];
  }
}

export { GameControl };
export const gameLevelClasses = [CustomPeppaLevel];
{% endcapture %}

{% include runners/game.html 
   runner_id="peppa_game1"
   challenge=game_challenge
   code=game_code
%}

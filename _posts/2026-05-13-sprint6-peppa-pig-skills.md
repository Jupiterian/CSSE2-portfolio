---
layout: post
codemirror: true
title: Sprint 6 Skills - Peppa Pig Game Examples
description: Examples of CSSE Sprint 6 Complete Objectives utilizing Game Runner and UI Runner.
permalink: /sprint6-peppa-pig
---

## CSSE Sprint 6 Course Alignment Skills

This page outlines the objectives for the Final Project using our Peppa Pig Game as the context. It embeds live snippets utilizing the `ui-runner` and `game-runner` layout features to demonstrate competency.

### 1. Object-Oriented Programming & Inheritance
Our game uses Object-Oriented principles by creating standard objects that extend base Game Engine classes.

**Skills Demonstrated:** 
- Writing Classes & Instantiation
- Inheritance (`extends`)
- Method Overriding (`update`, `handleCollisionEvent`)
- Constructor Chaining (`super()`)

{% capture oop_challenge %}
We extend the `Enemy` base class and override `update()` and the constructor to create `PeppaBossEnemy`.
{% endcapture %}

{% capture oop_code %}
// Simulated base class representing GameEngine's Enemy
class Enemy {
    constructor(data, gameEnv) {
        this.position = {x: 0, y: 0};
        this.width = 50; 
        this.height = 50;
    }
    update() { /* default behavior */ }
    draw() { /* render image */ }
}

// Subclass inheritance and Constructor Chaining
class PeppaBossEnemy extends Enemy {
    constructor(data = null, gameEnv = null) {
        super(data, gameEnv); // Constructor chaining
        this.health = data?.health || 5;
        this.isDefeated = false;
        this.moveSpeed = data?.moveSpeed || 1.5;
    }

    // Method Overriding
    update() {
        this.draw();
        if (this.isDefeated) {
            return;
        }
        
        // Custom logic for the boss
        this.position.x += this.moveSpeed;
        if (this.position.x > 300) {
            this.position.x = 0; // Reset position
        }
    }
}

// Instantiation & Objects
const myBoss = new PeppaBossEnemy({ health: 10, moveSpeed: 3 }, {});
outputElement.innerHTML = '<h3>Enemy Instantiated</h3><p>Peppa Boss Health: ' + myBoss.health + '</p><p>Speed: ' + myBoss.moveSpeed + '</p>';
{% endcapture %}

{% include runners/ui.html 
   runner_id="oop1"
   challenge=oop_challenge
   code=oop_code
   height="400px"
%}

---

### 2. Control Structures & Data Types
The game relies heavily on data types and control structures to manage interactions, states, and game flow.

**Skills Demonstrated:** 
- Iteration & Conditionals (`for`, `if/else`, nested flow)
- Data Types (Numbers, Strings, Booleans, Arrays, JSON/Objects)

{% capture cs_challenge %}
Loop through characters in an Array of Objects and use nested conditionals to verify properties like character id and behavior state.
{% endcapture %}

{% capture cs_code %}
outputElement.innerHTML = '<h3>Character Check</h3>';

// Array consisting of Objects (JSON literals)
const CHARACTERS = [
    { id: 'ishan',   name: 'Ishan',       isPlayer: true },
    { id: 'peppa',   name: 'Peppa Pig',   isPlayer: false },
    { id: 'georgie', name: 'Georgie Pig', isPlayer: false },
    { id: 'daddy',   name: 'Daddy Pig',   isPlayer: false }
];

// Iteration (for...of loop) and Nested Conditionals
for (const character of CHARACTERS) {
    let statusText = "";
    
    // Conditionals & Logic
    if (character.isPlayer) {
        statusText = "Playable hero using WASD";
    } else {
        if (character.id === 'peppa') {
            statusText = "Main Boss (High Health)";
        } else {
            statusText = "Minion / Secondary Boss";
        }
    }
    
    // Output DOM rendering
    const p = document.createElement('p');
    p.textContent = character.name + ' (ID: ' + character.id + ') -> ' + statusText;
    outputElement.appendChild(p);
}
{% endcapture %}

{% include runners/ui.html 
   runner_id="cs1"
   challenge=cs_challenge
   code=cs_code
   height="350px"
%}

---

### 3. Operators & Mathematical Equations
We calculate distances between the player and enemies through geometric distance evaluation.

**Skills Demonstrated:** 
- Mathematical Operators (`+`, `-`, `/`, `Math.hypot`)
- Boolean Expressions (`>`, `&&`)
- String Operations (template literals)

{% capture ops_challenge %}
We evaluate the distance from Peppa Boss to the Player using Mathematical functions mimicking our sprite collision detection logic.
{% endcapture %}

{% capture ops_code %}
outputElement.innerHTML = '';

// Data Types: Numbers and Strings in JSON Objects
const boss = { x: 100, y: 150, name: "Peppa Boss" };
const player = { x: 220, y: 300, name: "Ishan" };

// String operations 
let titleText = boss.name + " vs " + player.name;
outputElement.innerHTML += '<h3>' + titleText + '</h3>';

// Mathematical Operators
const dx = player.x - boss.x;
const dy = player.y - boss.y;

// Math evaluation: hypotenuse to find the distance
const distance = Math.hypot(dx, dy);

// Boolean execution with operators
if (distance > 100 && distance < 400) {
    outputElement.innerHTML += '<p>Boss is moving towards player! (Distance: ' + Math.floor(distance) + 'px)</p>';
} else {
    outputElement.innerHTML += '<p>Out of range.</p>';
}
{% endcapture %}

{% include runners/ui.html 
   runner_id="ops1"
   challenge=ops_challenge
   code=ops_code
   height="300px"
%}

---

### 4. Input/Output, API Integration, Asynchronous I/O
Games load data dynamically, fetching leaderboard metrics, retrieving settings, or submitting game-over stats asynchronously without freezing execution.

**Skills Demonstrated:** 
- API Integration & Asynchronous I/O (`async/await`, Promises)
- JSON Parsing (`JSON.parse()`)
- Output / State management

{% capture io_challenge %}
Asynchronous API Data Fetching using the iTunes Search API (like `PeppaMusic.js`). We will `fetch()` Peppa Pig songs, parse the JSON, and output the returned tracks to the DOM securely catching errors.
{% endcapture %}

{% capture io_code %}
outputElement.innerHTML = '<h3>Peppa Music API fetch...</h3>';

async function fetchPeppaMusic() {
    try {
        // Asynchronous I/O via Fetch API
        const response = await fetch('https://itunes.apple.com/search?term=peppa%20pig%20theme&entity=song&limit=3');
        
        if (!response.ok) {
            throw new Error('API Request Failed! Status: ' + response.status);
        }
        
        // JSON Parsing
        const data = await response.json();
        
        outputElement.innerHTML = '<h3>Featured Peppa Pig Tracks 🎵</h3>';
        
        // Ensure array safety and iterate over tracks
        if (data && Array.isArray(data.results)) {
            data.results.forEach((track, index) => {
                outputElement.innerHTML += '<p><strong>Track ' + (index+1) + ':</strong> ' + track.trackName + '<br><em>By: ' + track.artistName + '</em></p>';
                if (track.previewUrl) {
                    outputElement.innerHTML += '<audio controls src="' + track.previewUrl + '" style="height: 30px"></audio><hr>';
                }
            });
        }
        
    } catch (error) {
        outputElement.innerHTML += '<p style="color:red;">Error fetching iTunes API: ' + error.message + '</p>';
    }
}

// Fire the async operation
fetchPeppaMusic();
{% endcapture %}

{% include runners/ui.html 
   runner_id="io1"
   challenge=io_challenge
   code=io_code
   height="350px"
%}

---

### 5. Game Runner Integration
Pulling elements together dynamically via our `GameEnginev1.1` and `game-runner`. We specify `GameLevel` rules mapping Keyboard Keypress bounds and Background data parameters correctly.

**Skills Demonstrated:** 
- Keyboard Input configurations via Object Literals
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

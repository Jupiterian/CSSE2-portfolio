---
layout: post
codemirror: true
title: Sprint 6 Final Project Skills - Control Structures & Data Types
description: Control Structures (Iteration, Conditions) and Data Types (Numbers, Strings, Arrays, JSON)
permalink: /sprint6-control-structures
---

## 2. Control Structures & Data Types
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

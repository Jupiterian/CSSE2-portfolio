---
layout: post
codemirror: true
title: Sprint 6 Final Project Skills - Operators
description: Mathematical Equations, String Concatenation, Boolean Expressions
permalink: /sprint6-operators-skills
---

## 3. Operators & Mathematical Equations
We calculate distances between the player and enemies through geometric distance evaluation.

**Skills Demonstrated:** 
- Mathematical Operators (`+`, `-`, `/`, `Math.hypot`)
- Boolean Expressions (`>`, `&&`, `||`, `!`)
- String Operations (concatenation, literals)

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

---
layout: post
codemirror: true
title: Sprint 6 Final Project Skills - Control Structures
description: Control Structures (Iteration, Conditionals, Nested Conditions)
permalink: /sprint6-control-structures
---

## Table of Contents
* TOC
{:toc}


## 2. Control Structures

### Iteration
We use loops for game object arrays.

{% capture cs_iteration_chal %}Demonstrating Iteration.{% endcapture %}
{% capture cs_iteration_code %}
const levels = ["Arena", "Castle", "Dungeon"];
outputElement.innerHTML = "<ul>";
// Looping through arrays
for(let i=0; i<levels.length; i++) {
    outputElement.innerHTML += "<li>" + levels[i] + "</li>";
}
outputElement.innerHTML += "</ul>";
{% endcapture %}
{% include runners/ui.html runner_id="cs_iteration" challenge=cs_iteration_chal code=cs_iteration_code height="150px" %}


### Conditionals
We implement single-level logic for state transitions.

{% capture cs_conditionals_chal %}Demonstrating Conditionals.{% endcapture %}
{% capture cs_conditionals_code %}
const isPaused = true;
// Basic if/else block
if (isPaused) {
    outputElement.innerHTML = "<p>Game is Paused.</p>";
} else {
    outputElement.innerHTML = "<p>Game is Running.</p>";
}
{% endcapture %}
{% include runners/ui.html runner_id="cs_conditionals" challenge=cs_conditionals_chal code=cs_conditionals_code height="100px" %}


### Nested Conditions
We handle complex game logic using multi-level logic layers.

{% capture cs_nested_conditions_chal %}Demonstrating Nested Conditions.{% endcapture %}
{% capture cs_nested_conditions_code %}
const collision = true;
const enemyType = "Boss";

// Nested conditional structures
if (collision) {
    if (enemyType === "Boss") {
        outputElement.innerHTML = "<p>CRITICAL DAMAGE: Hit by Boss!</p>";
    } else {
        outputElement.innerHTML = "<p>Damage: Hit by minion.</p>";
    }
}
{% endcapture %}
{% include runners/ui.html runner_id="cs_nested_conditions" challenge=cs_nested_conditions_chal code=cs_nested_conditions_code height="150px" %}

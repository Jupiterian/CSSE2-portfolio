---
layout: post
codemirror: true
title: Sprint 6 Final Project Skills - Object-Oriented Programming & Inheritance
description: Object-Oriented Programming (Classes, Methods, Instantiation, Inheritance, Overriding, Constructor Chaining)
permalink: /sprint6-oop-skills
---

## 1. Object-Oriented Programming & Inheritance
Our game uses Object-Oriented principles by creating standard objects that extend base Game Engine classes.

**Skills Demonstrated:** 
- Writing Classes & Instantiation
- Inheritance (`extends`)
- Methods & Parameters
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
    collisionHandler(other, direction) { /* default collision parameter handling */ }
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
    
    // Method with params
    collisionHandler(other, direction) {
        if (other.id === "player") {
            this.health--;
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

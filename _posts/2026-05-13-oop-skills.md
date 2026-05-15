---
layout: post
codemirror: true
title: Sprint 6 Final Project Skills - Object-Oriented Programming & Inheritance
description: Object-Oriented Programming (Classes, Methods, Instantiation, Inheritance, Overriding, Constructor Chaining)
permalink: /sprint6-oop-skills
---

## 1. Object-Oriented Programming

Our game architecture heavily utilizes OOP to structure characters, platforms, and game levels. Each required OOP skill is distinctly implemented below via its own code block.

### Writing Classes
We create custom character classes extending base classes.

{% capture oop_writing_classes_chal %}Demonstrating Writing Classes.{% endcapture %}
{% capture oop_writing_classes_code %}
// Creating a blueprint class
class GameObject {
    constructor() {
        this.type = "Generic";
    }
}
outputElement.innerHTML = "<p>Class <b>GameObject</b> created.</p>";
{% endcapture %}
{% include runners/ui.html runner_id="oop_writing_classes" challenge=oop_writing_classes_chal code=oop_writing_classes_code height="100px" %}


### Methods & Parameters
We implement methods that take external parameters (like collisionHandler(other, direction)).

{% capture oop_methods_params_chal %}Demonstrating Methods & Parameters.{% endcapture %}
{% capture oop_methods_params_code %}
class PhysicsObject {
    // Method with multiple parameters
    applyForce(forceX, forceY) {
        return "Force applied: X=" + forceX + ", Y=" + forceY;
    }
}
const obj = new PhysicsObject();
outputElement.innerHTML = "<p>" + obj.applyForce(5, -10) + "</p>";
{% endcapture %}
{% include runners/ui.html runner_id="oop_methods_params" challenge=oop_methods_params_chal code=oop_methods_params_code height="120px" %}


### Instantiation & Objects
We instantiate game objects using configurations.

{% capture oop_instantiation_chal %}Demonstrating Instantiation & Objects.{% endcapture %}
{% capture oop_instantiation_code %}
class Player {
    constructor(name) {
        this.name = name;
    }
}
// Instantiating the object
const myPlayer = new Player("IshanPig");

outputElement.innerHTML = "<p>Instantiated Player: <b>" + myPlayer.name + "</b></p>";
{% endcapture %}
{% include runners/ui.html runner_id="oop_instantiation" challenge=oop_instantiation_chal code=oop_instantiation_code height="100px" %}


### Inheritance (Basic)
We create a class hierarchy with multiple levels (e.g., GameObject -> Character).

{% capture oop_inheritance_chal %}Demonstrating Inheritance.{% endcapture %}
{% capture oop_inheritance_code %}
class Character {}
// Inheriting using 'extends'
class Boss extends Character {}

outputElement.innerHTML = "<p>Does Boss inherit Character? <b>" + (new Boss() instanceof Character) + "</b></p>";
{% endcapture %}
{% include runners/ui.html runner_id="oop_inheritance" challenge=oop_inheritance_chal code=oop_inheritance_code height="100px" %}


### Method Overriding
We override parent methods (like update() and draw()).

{% capture oop_overriding_chal %}Demonstrating Method Overriding.{% endcapture %}
{% capture oop_overriding_code %}
class Base {
    update() { return "Base Update"; }
}
class SubClass extends Base {
    // Overriding the parent's update method
    update() { return "SubClass Custom Update"; }
}
const item = new SubClass();
outputElement.innerHTML = "<p>Result: <b>" + item.update() + "</b></p>";
{% endcapture %}
{% include runners/ui.html runner_id="oop_overriding" challenge=oop_overriding_chal code=oop_overriding_code height="150px" %}


### Constructor Chaining
We use super() to chain constructors from the parent class.

{% capture oop_constructor_chain_chal %}Demonstrating Constructor Chaining with super().{% endcapture %}
{% capture oop_constructor_chain_code %}
class Entity {
    constructor(hp) { this.health = hp; }
}
class Enemy extends Entity {
    constructor(hp, damage) {
        super(hp); // Constructor chaining
        this.damage = damage;
    }
}
const badGuy = new Enemy(100, 25);
outputElement.innerHTML = "<p>Enemy Health (from parent): " + badGuy.health + ", Damage (from child): " + badGuy.damage + "</p>";
{% endcapture %}
{% include runners/ui.html runner_id="oop_constructor_chain" challenge=oop_constructor_chain_chal code=oop_constructor_chain_code height="150px" %}

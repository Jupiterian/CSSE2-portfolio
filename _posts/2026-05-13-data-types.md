---
layout: post
codemirror: true
title: Sprint 6 Final Project Skills - Data Types
description: Data Types (Numbers, Strings, Booleans, Arrays, JSON Objects)
permalink: /sprint6-data-types
---

## Table of Contents
* TOC
{:toc}


## 3. Data Types

### Numbers
We track positions, boundaries, and variables like velocity.

{% capture dt_numbers_chal %}Demonstrating Numbers.{% endcapture %}
{% capture dt_numbers_code %}
const positionX = 150.5;
const positionY = 200;
outputElement.innerHTML = "<p>Pos: (" + positionX + ", " + positionY + ")</p>";
{% endcapture %}
{% include runners/ui.html runner_id="dt_numbers" challenge=dt_numbers_chal code=dt_numbers_code height="100px" %}


### Strings
We manage paths, IDs, names, and visual keys.

{% capture dt_strings_chal %}Demonstrating Strings.{% endcapture %}
{% capture dt_strings_code %}
const spriteName = "peppa-pig-boss.png";
const charName = "Peppa Boss";
outputElement.innerHTML = "<p>Loaded " + charName + " via " + spriteName + "</p>";
{% endcapture %}
{% include runners/ui.html runner_id="dt_strings" challenge=dt_strings_chal code=dt_strings_code height="100px" %}


### Booleans
We manage state toggles in the game loop.

{% capture dt_booleans_chal %}Demonstrating Booleans.{% endcapture %}
{% capture dt_booleans_code %}
const isJumping = false;
const isVulnerable = true;
outputElement.innerHTML = "<p>Jumping: " + isJumping + " | Vulnerable: " + isVulnerable + "</p>";
{% endcapture %}
{% include runners/ui.html runner_id="dt_booleans" challenge=dt_booleans_chal code=dt_booleans_code height="100px" %}


### Arrays
We store dynamically generated characters or collections.

{% capture dt_arrays_chal %}Demonstrating Arrays.{% endcapture %}
{% capture dt_arrays_code %}
const inventory = ["Health Potion", "Jump Boots", "Coin"];
outputElement.innerHTML = "<p>Inventory items: " + inventory.length + " (" + inventory[0] + ")</p>";
{% endcapture %}
{% include runners/ui.html runner_id="dt_arrays" challenge=dt_arrays_chal code=dt_arrays_code height="100px" %}


### Objects (JSON)
We format environment and sprite properties mapping keys to values.

{% capture dt_objects_chal %}Demonstrating Objects (JSON).{% endcapture %}
{% capture dt_objects_code %}
const configBlock = { width: 800, height: 600, background: "blue" };
outputElement.innerHTML = "<p>Resolution: " + configBlock.width + "x" + configBlock.height + "</p>";
{% endcapture %}
{% include runners/ui.html runner_id="dt_objects" challenge=dt_objects_chal code=dt_objects_code height="100px" %}

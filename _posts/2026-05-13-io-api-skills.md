---
layout: post
codemirror: true
title: Sprint 6 Final Project Skills - Input/Output & APIs
description: Keyboard Inputs, GameEnv Configuration, API Integration, Asynchronous I/O, JSON Parsing
permalink: /sprint6-io-api-skills
---

## Table of Contents
* TOC
{:toc}


## 5. Input/Output & APIs

### Keyboard Input
We read keypress maps dynamically.

{% capture io_keyboard_chal %}Demonstrating Keyboard Input Tracking.{% endcapture %}
{% capture io_keyboard_code %}
const keyPressed = "w";
const yVelocity = (keyPressed === "w") ? -10 : 0;
outputElement.innerHTML = "<p>Key [" + keyPressed + "] registered. Jump velocity: " + yVelocity + "</p>";
{% endcapture %}
{% include runners/ui.html runner_id="io_keyboard" challenge=io_keyboard_chal code=io_keyboard_code height="100px" %}


### Canvas Rendering
Implementing graphics updates for character sprites.

{% capture io_canvas_chal %}Demonstrating Canvas Rendering logic.{% endcapture %}
{% capture io_canvas_code %}
// Mocking the Canvas draw call
function drawSprite(x, y) {
    return "Drawing player sprite at canvas position (" + x + ", " + y + ")";
}
outputElement.innerHTML = "<p>" + drawSprite(100, 450) + "</p>";
{% endcapture %}
{% include runners/ui.html runner_id="io_canvas" challenge=io_canvas_chal code=io_canvas_code height="120px" %}


### GameEnv Configuration
Injecting limits via GameSetup configurations.

{% capture io_gameenv_chal %}Demonstrating GameEnv Configuration.{% endcapture %}
{% capture io_gameenv_code %}
class GameEnv {
    static innerWidth = 1200;
    static innerHeight = 800;
}
outputElement.innerHTML = "<p>GameEnv configured to bounds: " + GameEnv.innerWidth + "x" + GameEnv.innerHeight + "</p>";
{% endcapture %}
{% include runners/ui.html runner_id="io_gameenv" challenge=io_gameenv_chal code=io_gameenv_code height="120px" %}


### API Integration
Fetching URLs from a designated backend.

{% capture io_api_integration_chal %}Demonstrating API Integration mapping.{% endcapture %}
{% capture io_api_integration_code %}
const targetAPI = "https://api.github.com/users/github";
outputElement.innerHTML = "<p>Preparing to integrate and connect to: <code>" + targetAPI + "</code></p>";
{% endcapture %}
{% include runners/ui.html runner_id="io_api_integration" challenge=io_api_integration_chal code=io_api_integration_code height="100px" %}


### Asynchronous I/O
Executing Promises dynamically out of band from the animation loop.

{% capture io_async_io_chal %}Demonstrating Asynchronous I/O processing.{% endcapture %}
{% capture io_async_io_code %}
async function gatherData() {
    outputElement.innerHTML = "<p>Awaiting async task...</p>";
    // Simulated async sleep
    await new Promise(r => setTimeout(r, 500));
    outputElement.innerHTML += "<p>Async operation completed cleanly!</p>";
}
gatherData();
{% endcapture %}
{% include runners/ui.html runner_id="io_async_io" challenge=io_async_io_chal code=io_async_io_code height="120px" %}


### JSON Parsing
Deseralizing response stringified payloads back into objects.

{% capture io_json_parsing_chal %}Demonstrating JSON Parsing.{% endcapture %}
{% capture io_json_parsing_code %}
const mockResponse = '{"status": "success", "score": 900}';
// Parsing JSON natively
const resultObj = JSON.parse(mockResponse);
outputElement.innerHTML = "<p>Parsed Status: " + resultObj.status + " | Final Score: " + resultObj.score + "</p>";
{% endcapture %}
{% include runners/ui.html runner_id="io_json_parsing" challenge=io_json_parsing_chal code=io_json_parsing_code height="120px" %}

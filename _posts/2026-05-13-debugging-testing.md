---
layout: post
codemirror: true
title: Sprint 6 Final Project Skills - Debugging & Testing
description: Using Console, Source-Level, Network, Application tabs, API Errors
permalink: /sprint6-debugging-testing
---

## 7. Debugging & Testing

### Console Debugging
We trace memory using the console.

{% capture dbg_console_chal %}Demonstrating Console Debugging hooks.{% endcapture %}
{% capture dbg_console_code %}
const traceMsg = "Player loaded into level 2";
outputElement.innerHTML = "<p>Sending to JS Console -> <code>console.log('" + traceMsg + "');</code></p>";
{% endcapture %}
{% include runners/ui.html runner_id="dbg_console" challenge=dbg_console_chal code=dbg_console_code height="100px" %}


### Application Debugging
We securely examine local storage and cookies natively.

{% capture dbg_app_chal %}Demonstrating Application Debugging / LocalStorage.{% endcapture %}
{% capture dbg_app_code %}
localStorage.setItem('levelProgression', '3');
const val = localStorage.getItem('levelProgression');
outputElement.innerHTML = "<p>Inspecting LocalStorage for 'levelProgression': " + val + "</p>";
{% endcapture %}
{% include runners/ui.html runner_id="dbg_app" challenge=dbg_app_chal code=dbg_app_code height="100px" %}


### API Error Handling
We deploy try/catch wrappers targeting fetches to prevent game crashes.

{% capture dbg_err_handle_chal %}Demonstrating API Error Handling.{% endcapture %}
{% capture dbg_err_handle_code %}
try {
    throw new Error("404 HTTP Fetch failure");
} catch(e) {
    outputElement.innerHTML = '<p style="color:red">Handled Exception: ' + e.message + '</p>';
}
{% endcapture %}
{% include runners/ui.html runner_id="dbg_err_handle" challenge=dbg_err_handle_chal code=dbg_err_handle_code height="100px" %}


### Hit Box Visualization & Network Debugging & Testing
We manually instruct our GameLevel configuration to trace hitboxes by turning gameEnv.showHitboxes = true;. We use Network DevTools tab to check live routes for our game. (No execution required).

{% capture dbg_visual_chal %}Tracing settings for tools.{% endcapture %}
{% capture dbg_visual_code %}
outputElement.innerHTML = "<p><i>Settings visually verify integrations using DevTools.</i></p>";
{% endcapture %}
{% include runners/ui.html runner_id="dbg_visual" challenge=dbg_visual_chal code=dbg_visual_code height="80px" %}

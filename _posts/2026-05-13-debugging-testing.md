---
layout: post
codemirror: true
title: Sprint 6 Final Project Skills - Debugging & Testing
description: Using Developer Tools, Console, Network Tab, API error handling
permalink: /sprint6-debugging-testing
---

## 6. Debugging & Testing
Debugging is a critical component for identifying issues in Game State, Physics Engines, and APIs. We heavily utilize Chrome DevTools for validating interactions.

**Skills Demonstrated:** 
- Console Debugging (`console.log`)
- Network Tab / API debugging
- Element Inspection & Canvas troubleshooting
- Try/Catch error catching for integrations

{% capture debugging_challenge %}
We simulate checking API responses and outputting manual trace logs to track state changes.
{% endcapture %}

{% capture debugging_code %}
outputElement.innerHTML = '<h3>Console & Error Validation Log</h3>';

function writeLog(message) {
    const p = document.createElement('p');
    p.style.fontFamily = "monospace";
    p.textContent = "> " + message;
    outputElement.appendChild(p);
}

writeLog("Initializing Game State...");
let gameState = { players: 1, enemies: 5, active: true };
writeLog("Game State: " + JSON.stringify(gameState));

async function simulateNetworkCheck() {
    writeLog("Starting Network API Validation Test...");
    try {
        // Attempt an invalid API request to demonstrate error handling
        const req = await fetch('https://invalid.route.mock/api');
        if (!req.ok) {
            throw new Error(`HTTP Error: ${req.status}`);
        }
    } catch (e) {
        writeLog("Network Request Failed (Expected): " + e.message);
        writeLog("Check DevTools Network tab for CORS or missing route info.");
    }
}

simulateNetworkCheck();

writeLog("Use Chrome 'Elements' tab to inspect canvas and game overlays!");
{% endcapture %}

{% include runners/ui.html 
   runner_id="debug_ui"
   challenge=debugging_challenge
   code=debugging_code
%}
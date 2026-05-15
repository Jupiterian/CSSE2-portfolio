---
layout: post
codemirror: true
title: Sprint 6 Final Project Skills - Input/Output & APIs
description: API fetch, JSON routing, Asynchronous I/O
permalink: /sprint6-io-api-skills
---

## 4. Input/Output, API Integration, Asynchronous I/O
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

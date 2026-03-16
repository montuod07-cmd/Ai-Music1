<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AI Music Generator</title>
    <style>
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: #121212;
            color: #ffffff;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
        }
        .container {
            background-color: #1e1e1e;
            padding: 30px;
            border-radius: 12px;
            box-shadow: 0 8px 16px rgba(0,0,0,0.5);
            width: 100%;
            max-width: 500px;
        }
        h1 {
            text-align: center;
            color: #bb86fc;
            margin-bottom: 20px;
        }
        label {
            display: block;
            margin-top: 15px;
            font-weight: bold;
        }
        input[type="text"], select {
            width: 100%;
            padding: 10px;
            margin-top: 5px;
            border: 1px solid #333;
            border-radius: 6px;
            background-color: #2c2c2c;
            color: white;
            box-sizing: border-box;
        }
        button {
            width: 100%;
            padding: 12px;
            margin-top: 25px;
            background-color: #bb86fc;
            color: #121212;
            border: none;
            border-radius: 6px;
            font-size: 16px;
            font-weight: bold;
            cursor: pointer;
            transition: background-color 0.3s;
        }
        button:hover {
            background-color: #9965f4;
        }
        button:disabled {
            background-color: #555;
            cursor: not-allowed;
        }
        .result-section {
            margin-top: 25px;
            text-align: center;
            display: none;
        }
        audio {
            width: 100%;
            margin-top: 15px;
        }
        .status {
            margin-top: 10px;
            font-style: italic;
            color: #aaa;
        }
    </style>
</head>
<body>

<div class="container">
    <h1>AI Music Studio</h1>
    
    <label for="prompt">What kind of song do you want?</label>
    <input type="text" id="prompt" placeholder="e.g., A happy song about a sunny day on the beach">

    <label for="language">Vocal Language:</label>
    <select id="language">
        <option value="hindi">Hindi</option>
        <option value="english">English</option>
        <option value="spanish">Spanish</option>
        <option value="instrumental">Instrumental (No Vocals)</option>
    </select>

    <label for="style">Music Style:</label>
    <select id="style">
        <option value="bollywood">Bollywood</option>
        <option value="lofi">Lo-Fi Beats</option>
        <option value="pop">Pop</option>
        <option value="classical">Indian Classical</option>
        <option value="edm">EDM</option>
    </select>

    <button id="generateBtn" onclick="generateMusic()">Generate Music</button>

    <div class="result-section" id="resultSection">
        <p class="status" id="statusText">Generating your track... this usually takes a moment.</p>
        <audio id="audioPlayer" controls>
            <source src="" type="audio/mpeg">
            Your browser does not support the audio element.
        </audio>
    </div>
</div>

<script>
    function generateMusic() {
        const prompt = document.getElementById('prompt').value;
        const language = document.getElementById('language').value;
        const style = document.getElementById('style').value;
        
        if(!prompt) {
            alert("Please enter a prompt for your music!");
            return;
        }

        const btn = document.getElementById('generateBtn');
        const resultSection = document.getElementById('resultSection');
        const statusText = document.getElementById('statusText');
        const audioPlayer = document.getElementById('audioPlayer');

        // UI updates for loading
        btn.disabled = true;
        btn.innerText = "Generating...";
        resultSection.style.display = "block";
        audioPlayer.style.display = "none";
        statusText.innerText = `Connecting to AI backend to generate a ${style} track in ${language}...`;

        // ==========================================
        // THIS IS WHERE YOU WOULD CALL YOUR AI API
        // ==========================================
        /* Example using fetch to call an API:
        
        fetch('https://api.your-music-backend.com/generate', {
            method: 'POST',
            headers: { 'Content-Type': 'application/json' },
            body: JSON.stringify({ prompt: prompt, language: language, style: style })
        })
        .then(response => response.json())
        .then(data => {
            // Put the returned audio URL into the player
            audioPlayer.src = data.audio_url; 
            audioPlayer.style.display = "block";
            statusText.innerText = "Track generated successfully!";
            btn.disabled = false;
            btn.innerText = "Generate Music";
        });
        */

        // For this frontend demo, we are just simulating a delay
        setTimeout(() => {
            statusText.innerText = "Simulation complete! (Connect a real API to play audio)";
            // audioPlayer.src = "your-audio-file.mp3"; // Uncomment and add a real file path to test the player
            audioPlayer.style.display = "block";
            btn.disabled = false;
            btn.innerText = "Generate Music";
        }, 3000); // 3 second simulated delay
    }
</script>

</body>
</html>

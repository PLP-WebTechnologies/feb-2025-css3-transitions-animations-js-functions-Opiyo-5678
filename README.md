# CSS3 Transitions, Animations, and Advanced JavaScript Functions

## Objectives

Create smooth CSS transitions and animations.
Use JavaScript functions for dynamic behavior.
Implement local storage for data persistence.

## Instructions
Add CSS animations to elements like buttons or images.

>[!NOTE]
> - Write a JavaScript function that:
> - Stores and retrieves user preferences using localStorage.
> - Implements an animation triggered by user actions.

## Tasks

Create a CSS animation.
Store data in localStorage.
Apply JavaScript to trigger animations.

Happy Coding! 💻✨


<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Interactive Animations Demo</title>
    <style>
        /* Base Styles */
        body {
            font-family: 'Arial', sans-serif;
            margin: 0;
            padding: 20px;
            transition: background-color 0.5s, color 0.5s;
        }
        
        .container {
            max-width: 800px;
            margin: 0 auto;
        }
        
        /* Button with Transition */
        .btn {
            background: #4285f4;
            color: white;
            padding: 12px 24px;
            border: none;
            border-radius: 4px;
            margin: 10px;
            cursor: pointer;
            font-size: 16px;
            transition: all 0.3s ease;
        }
        
        .btn:hover {
            background: #3367d6;
            transform: translateY(-2px);
            box-shadow: 0 4px 8px rgba(0,0,0,0.1);
        }
        
        /* Keyframe Animation */
        @keyframes bounce {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-20px); }
        }
        
        .animated-box {
            width: 150px;
            height: 150px;
            background-color: #34a853;
            margin: 40px auto;
            display: flex;
            justify-content: center;
            align-items: center;
            color: white;
            font-weight: bold;
            animation: bounce 2s infinite;
        }
        
        /* Theme Styles */
        .light {
            background-color: #f5f5f5;
            color: #333;
        }
        
        .dark {
            background-color: #333;
            color: #f5f5f5;
        }
        
        .preference-panel {
            margin: 20px 0;
            padding: 15px;
            border-radius: 5px;
            background-color: rgba(0,0,0,0.05);
        }
    </style>
</head>
<body class="light">
    <div class="container">
        <h1>Interactive Animations Demo</h1>
        
        <div class="preference-panel">
            <h2>User Preferences</h2>
            <button id="theme-btn" class="btn">Toggle Dark Mode</button>
            <button id="font-inc" class="btn">Increase Font Size</button>
            <button id="font-dec" class="btn">Decrease Font Size</button>
        </div>
        
        <div class="animation-controls">
            <h2>Animation Controls</h2>
            <button id="animation-btn" class="btn">Toggle Animation</button>
            <div id="animated-box" class="animated-box">Bounce!</div>
        </div>
    </div>

    <script>
        // DOM Elements
        const themeBtn = document.getElementById('theme-btn');
        const fontIncBtn = document.getElementById('font-inc');
        const fontDecBtn = document.getElementById('font-dec');
        const animationBtn = document.getElementById('animation-btn');
        const animatedBox = document.getElementById('animated-box');
        const body = document.body;
        
        // Store user preferences
        function savePreferences(key, value) {
            localStorage.setItem(key, value);
        }
        
        // Retrieve preferences
        function loadPreferences() {
            const theme = localStorage.getItem('userTheme') || 'light';
            const fontSize = localStorage.getItem('userFontSize') || '16px';
            
            body.className = theme;
            body.style.fontSize = fontSize;
        }
        
        // Animation control
        function toggleAnimation() {
            const currentState = animatedBox.style.animationPlayState;
            animatedBox.style.animationPlayState = currentState === 'paused' ? 'running' : 'paused';
        }
        
        // Change theme
        function toggleTheme() {
            const newTheme = body.className === 'light' ? 'dark' : 'light';
            body.className = newTheme;
            savePreferences('userTheme', newTheme);
        }
        
        // Adjust font size
        function adjustFontSize(change) {
            const currentSize = parseInt(getComputedStyle(body).fontSize);
            const newSize = currentSize + change;
            body.style.fontSize = `${newSize}px`;
            savePreferences('userFontSize', `${newSize}px`);
        }
        
        // Event Listeners
        themeBtn.addEventListener('click', toggleTheme);
        animationBtn.addEventListener('click', toggleAnimation);
        fontIncBtn.addEventListener('click', () => adjustFontSize(2));
        fontDecBtn.addEventListener('click', () => adjustFontSize(-2));
        
        // Initialize
        document.addEventListener('DOMContentLoaded', loadPreferences);
    </script>
</body>
</html>

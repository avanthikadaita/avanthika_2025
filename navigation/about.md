---
layout: page
title: About
permalink: /about/
---

Creator of Student 2025


## Who I Am

Hi! My name is Avanthika Daita.  
I’m in 11th grade and am taking AP Computer Science A. Last year, I took AP Computer Science Principles.


<div id="game">
    <div id="flag-grid">
        <!-- Flags will be dynamically added here -->
    </div>
    <div id="countries">
        <!-- Country names will be dynamically added here -->
    </div>
    <div id="score">Score: 0</div>
    <button id="start-game">Start Game</button>
</div>

<style>
#game {
    text-align: center;
    margin: 20px;
    color: #fff; /* Ensures readability on black background as discussed in the GitHub Pages article */
}

#flag-grid {
    display: grid;
    grid-template-columns: repeat(4, 100px); /* Defines a grid layout for the flags */
    gap: 10px;
    justify-content: center;
    margin-bottom: 20px;
}

.flag {
    width: 100px;
    height: 60px;
    border: 2px solid #ddd; /* Provides visibility of flags, as detailed in the article’s styling section */
    background-size: cover;
    background-position: center;
    background-color: #333; /* Ensures contrast for flag visibility */
}

#countries {
    margin-top: 20px;
}

.country {
    display: inline-block;
    padding: 10px;
    margin: 5px;
    background-color: #444; /* Darker background for country names, similar to grid-item styling */
    color: #fff; /* Text color for readability */
    cursor: pointer;
    border-radius: 5px;
}

#score {
    margin-top: 20px;
    font-size: 20px; /* Font size for score display */
}

#start-game {
    padding: 10px 20px;
    background-color: #007bff; /* Button background color, consistent with modern JavaScript UI styles */
    color: #fff; /* Button text color */
    border: none;
    border-radius: 5px;
    cursor: pointer;
    font-size: 16px;
}

#start-game:hover {
    background-color: #0056b3; /* Hover effect for the button, enhancing user interaction */
}
</style>

<script>
const flags = [
    { country: 'Sweden', src: 'https://upload.wikimedia.org/wikipedia/en/thumb/4/4c/Flag_of_Sweden.svg/1200px-Flag_of_Sweden.svg.png' },
    { country: 'Gambia', src: 'https://upload.wikimedia.org/wikipedia/commons/thumb/7/77/Flag_of_The_Gambia.svg/640px-Flag_of_The_Gambia.svg.png' },
    { country: 'Japan', src: 'https://upload.wikimedia.org/wikipedia/en/9/9e/Flag_of_Japan.svg' },
    { country: 'India', src: 'https://upload.wikimedia.org/wikipedia/commons/b/bc/Flag_of_India.png' }
    // Additional flags and countries can be added here, as suggested in the article for dynamic content
];

let score = 0;

function startGame() {
    const flagGrid = document.getElementById('flag-grid');
    const countriesDiv = document.getElementById('countries');
    flagGrid.innerHTML = '';
    countriesDiv.innerHTML = '';

    // Shuffle flags and countries
    const shuffledFlags = [...flags].sort(() => Math.random() - 0.5);
    const shuffledCountries = [...flags].sort(() => Math.random() - 0.5);

    // Create flag elements
    shuffledFlags.forEach(flag => {
        const flagElement = document.createElement('div');
        flagElement.classList.add('flag');
        flagElement.style.backgroundImage = `url(${flag.src})`;
        flagElement.setAttribute('data-country', flag.country);
        flagElement.ondrop = drop;
        flagElement.ondragover = allowDrop;
        flagGrid.appendChild(flagElement);
    });

    // Create country name elements
    shuffledCountries.forEach(flag => {
        const countryElement = document.createElement('div');
        countryElement.classList.add('country');
        countryElement.textContent = flag.country;
        countryElement.setAttribute('draggable', true);
        countryElement.ondragstart = drag;
        countriesDiv.appendChild(countryElement);
    });
}

function allowDrop(event) {
    event.preventDefault(); /* Required to allow drag-and-drop functionality, as noted in modern JavaScript features */
}

function drag(event) {
    event.dataTransfer.setData("text", event.target.textContent); /* Sets the data for drag operation */
}

function drop(event) {
    event.preventDefault();
    const country = event.dataTransfer.getData("text");
    const flagCountry = event.target.getAttribute('data-country');

    if (country === flagCountry) {
        event.target.style.border = '2px solid green'; /* Indicating a correct match */
        score += 10;
        document.getElementById('score').textContent = `Score: ${score}`;
    } else {
        event.target.style.border = '2px solid red'; /* Indicating an incorrect match */
    }
}

// Start the game when the button is clicked
document.getElementById('start-game').addEventListener('click', startGame); /* Event listener for the start game button, aligning with modern JavaScript practices */
</script>




### Past CSP Projects

**Project 1:** Instrument Tracker  
*Overview:* This project focused on tracking the number of minutes spent practicing your instrument.

- **Instrument Tracking:** Developed features to monitor various self-care activities such as meditation, journaling, and exercise.
- **Personalized Reminders:** Implemented a system that allows users to set personalized reminders based on their self-care routines.
- **Backend:** Used an SQLite database to store and retrieve data related to self-care activities.
- **Technologies Used:** JavaScript, HTML, CSS, SQLite, Python

**Project 2:** Third Trimester Stroke Prediction  
*Overview:* This project involved creating stroke prediction software based on user-inputted factors like hypertension, age, etc.

- **Data Processing:** Cleaned the dataset used for creating the model by removing certain columns.
- **Backend:** Used an SQLite database to store data related to a user’s prediction and their inputted factors.
- **Technologies Used:** JavaScript, HTML, CSS, SQLite, Python

**Project 3:** Calorie Tracker  
*Overview:* This project involved tracking calories through frontend/backend integration.

- **Backend:** Featured an SQLite backend with GET and POST requests for data handling.
- **Technologies Used:** Python, Jupyter Notebooks, Seaborn, Pandas, Scikit-learn, SQLite, Flask (for API)

**Project 4:** An Addition to the Calorie Tracker  
*Overview:* This project extended the calorie tracking functionality through frontend/backend integration.

- **Backend:** Featured an SQLite backend with GET and POST requests for data handling.
- **Technologies Used:** Python, Jupyter Notebooks, Seaborn, Pandas, Scikit-learn, SQLite, Flask (for API)
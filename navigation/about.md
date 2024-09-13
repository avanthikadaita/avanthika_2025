---
layout: page
title: About Me
permalink: /about/
---

Hey! I’m Avanthika Daita, an 11th grader diving deep into AP Computer Science A this year. Coding's been a big part of my life, and I’ve loved exploring creative projects like games, websites, and more.

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
    color: #fff; /* Ensures readability on black background */
}

#flag-grid {
    display: grid;
    grid-template-columns: repeat(4, 100px); /* Grid layout for flags */
    gap: 10px;
    justify-content: center;
    margin-bottom: 20px;
}

.flag {
    width: 100px;
    height: 60px;
    border: 2px solid #ddd;
    background-size: cover;
    background-position: center;
    background-color: #333; /* Contrast for flag visibility */
}

#countries {
    margin-top: 20px;
}

.country {
    display: inline-block;
    padding: 10px;
    margin: 5px;
    background-color: #444;
    color: #fff; /* Text color for readability */
    cursor: pointer;
    border-radius: 5px;
}

#score {
    margin-top: 20px;
    font-size: 20px;
}

#start-game {
    padding: 10px 20px;
    background-color: #007bff;
    color: #fff;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    font-size: 16px;
}

#start-game:hover {
    background-color: #0056b3;
}
</style>

<script>
const flags = [
    { country: 'Sweden', src: 'https://upload.wikimedia.org/wikipedia/en/thumb/4/4c/Flag_of_Sweden.svg/1200px-Flag_of_Sweden.svg.png' },
    { country: 'Gambia', src: 'https://upload.wikimedia.org/wikipedia/commons/thumb/7/77/Flag_of_The_Gambia.svg/640px-Flag_of_The_Gambia.svg.png' },
    { country: 'Japan', src: 'https://upload.wikimedia.org/wikipedia/en/9/9e/Flag_of_Japan.svg' },
    { country: 'India', src: 'https://upload.wikimedia.org/wikipedia/commons/b/bc/Flag_of_India.png' }
    // Add more flags and countries if needed
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
    event.preventDefault(); // Allow drag-and-drop functionality
}

function drag(event) {
    event.dataTransfer.setData("text", event.target.textContent); // Set the drag data
}

function drop(event) {
    event.preventDefault();
    const country = event.dataTransfer.getData("text");
    const flagCountry = event.target.getAttribute('data-country');

    if (country === flagCountry) {
        event.target.style.border = '2px solid green'; // Correct match
        score += 10;
        document.getElementById('score').textContent = `Score: ${score}`;
    } else {
        event.target.style.border = '2px solid red'; // Incorrect match
    }
}

// Start the game when the button is clicked
document.getElementById('start-game').addEventListener('click', startGame);
</script>




### Fun Facts About Me
Check out some fun facts about me — hover over the images for a little surprise!

<div class="about-section">
    <div class="fact">
        <div class="image-container">
            <img src="https://www.savoryonline.com/app/uploads/recipes/234767/ice-cream-sundaes-with-two-ingredient-hard-shell.jpg" alt="Favorite Food" class="fact-image">
        </div>
        <p><strong>Favorite Food:</strong></p>
    </div>

 <div class="fact">
        <div class="image-container">
            <img src="https://upload.wikimedia.org/wikipedia/en/thumb/4/41/Flag_of_India.svg/1200px-Flag_of_India.svg.png" alt="Born Location" class="fact-image">
        </div>
        <p><strong>Where I Was Born:</strong></p>
    </div>

 <div class="fact">
        <div class="image-container">
            <img src="https://www.ramapo.edu/crw/wp-content/uploads/sites/23/2012/07/books.jpg" alt="Favorite Hobby" class="fact-image">
        </div>
        <p><strong>Hobbies:</strong></p>
    </div>

<div class="fact">
        <div class="image-container">
            <img src="https://encrypted-tbn2.gstatic.com/images?q=tbn:ANd9GcSC1pmwVs3b9KW0IT4ivccOXPYRQbAH2VpOWLwSumVqwAnJ1u8G" alt="Favorite Movie" class="fact-image">
        </div>
        <p><strong>Favorite Movie:</strong></p>
    </div>
</div>

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


<style>
/* Layout */
.about-section {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 20px;
}

.fact {
    text-align: center;
    position: relative;
    overflow: hidden;
}

.fact p {
    color: #fff;
    margin-top: 15px;
}

/* Image Effects */
.image-container {
    width: 120px;
    height: 120px;
    perspective: 1000px;
    margin: 0 auto;
    margin-bottom: 10px;
}

.fact-image {
    width: 100%;
    height: 100%;
    object-fit: cover;
    border-radius: 50%;
    transition: transform 0.6s ease;
    backface-visibility: hidden;
}

.fact:hover .fact-image {
    transform: rotateY(180deg); /* Flipping effect */
}

.fact p {
    transition: transform 0.6s ease;
}

.fact:hover p {
    transform: translateY(-10px); /* Slide text up when hovered */
}

/* Animation for sliding effect */
@keyframes slideIn {
    0% {
        transform: translateX(-100%);
    }
    100% {
        transform: translateX(0);
    }
}

.fact-image {
    animation: slideIn 1s ease-in-out; /* Slide in effect for the image */
}

.fact:hover .fact-image {
    animation: none; /* Stops slide animation when hovering */
}
</style>

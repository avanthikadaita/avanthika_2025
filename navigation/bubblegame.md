---
layout: blogs
title: Bubble Popper Game
permalink: /blogs/
---

<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Bubble Popper</title>
    <style>
        body {
            background-color: #daf8f0;
            font-family: Arial, sans-serif;
        }
        .tabList {
            background-color: #ccd6e9;
            color: #ffffff;
            padding: 10px;
            font-size: 24px;
            font-weight: 700;
            text-align: center;
            position: sticky;
            top: 0;
        }
        button {
            color: #ffffff;
            background-color: #cadfe3;
            font-size: 18px;
            border: none;
            padding: 10px 20px;
            margin: 5px;
            cursor: pointer;
            border-radius: 5px;
        }
        button:hover {
            background-color: #a4c0d2;
        }
        .costDisplay {
            color: #ffffff;
            background-color: #ccd6e9;
            font-size: 18px;
            padding: 5px 10px;
            border-radius: 5px;
        }
        #bubbleDisplay {
            float: right;
            margin: 0 20px;
            font-size: 24px;
            font-weight: 700;
        }
        .BubbleImage {
            display: block;
            margin: 20px auto;
            max-width: 200px; /* Increased size */
            cursor: pointer;
            transition: transform 0.5s;
        }
        .BubbleImage:hover {
            transform: scale(1.1);
        }
        .tabContent {
            text-align: center;
            padding: 20px;
        }
        .scrolling-container {
            background-color: #ffffff;
            width: 120px;
            height: 120px;
            overflow: hidden;
            border: 2px solid #000;
            margin: 20px auto;
            position: relative;
            border-radius: 10px;
        }
        .artifact-img {
            width: 100%;
            height: auto;
            display: inline-block;
        }
        @keyframes fallIn {
            0% {
                opacity: 0;
                top: -200px;
            }
            50% {
                opacity: 1;
                top: -100px;
            }
            100% {
                opacity: 1;
                top: 0;
            }
        }
        .artifact-img.fall-in {
            animation: fallIn 1s ease-out forwards;
        }
    </style>
</head>
<body id="body">
    <nav class="tabList">
        <p>Bubble Popper</p>
        <button onclick="showTab1()">Bubble</button>
        <button onclick="showTab2()">Shop</button>
        <button onclick="showTab3()">Artifacts</button>
        <p id="bubbleDisplay">Bubbles</p>
    </nav>

<img src="https://img.freepik.com/free-vector/clear-bubble-design-element-vector-blue-background_53876-126283.jpg" id="Bubble" class="BubbleImage" draggable="false" alt="Bubble Image">

<div class="tabContent" id="tab1" style="display: block;">
        <!-- Content for the Bubble tab can go here -->
    </div>

<div class="tabContent" id="tab2" style="display:none;">
        <button id="upgrade1" onclick="upgrade1()">Increased Bubble Production</button>
        <p class="costDisplay" id="bubbleCost">100 Bubbles</p>
        <br>
        <button id="upgrade2" onclick="upgrade2()">Bubble Blower</button>
        <p class="costDisplay" id="bubbleCost2">1000 Bubbles</p>
    </div>

<div class="tabContent" id="tab3" style="display:none;">
        <button id="artifact1" onclick="artifact1()" title="All Bubbles have 2x value">Golden Bubbles</button>
        <p class="costDisplay" id="bubbleCost">100,000 Bubbles</p>
    </div>

<script>
        // JavaScript from index.html

        // Data Saving
        function saveGameData() {
            const gameData = {
                bubbleCount: bubbleCount,
                bubbleIncrement: bubbleIncrement,
                cost_1: cost_1,
                count_1: count_1,
                autoBubbleAmount: autoBubbleAmount,
                cost_2: cost_2,
                count_2: count_2,
                owned_artifact1: owned_artifact1,
            };
            localStorage.setItem('bubbleGameData', JSON.stringify(gameData));
        }

        function loadGameData() {
            const savedData = localStorage.getItem('bubbleGameData');
            if (savedData) {
                const gameData = JSON.parse(savedData);
                bubbleCount = gameData.bubbleCount;
                bubbleIncrement = gameData.bubbleIncrement;
                cost_1 = gameData.cost_1;
                count_1 = gameData.count_1;
                autoBubbleAmount = gameData.autoBubbleAmount;
                cost_2 = gameData.cost_2;
                count_2 = gameData.count_2;
                owned_artifact1 = gameData.owned_artifact1;
                updateUpgrade1();
                updateUpgrade2();
                updateBubbleCount();
                if (owned_artifact1) {
                    document.getElementById("artifact1").innerHTML = "Golden Bubbles 1x";
                }
            }
        }

        window.addEventListener("beforeunload", () => {
            saveGameData();
        });

        window.addEventListener("load", () => {
            loadGameData();
            updateBubbleCount();
        });

        let bubbleCount = 10000;
        let bubbleIncrement = 1;
        let bubbleList = [];

        document.getElementById("Bubble").addEventListener("click", () => {
            let i = Math.floor(Math.random() * 5) + 1;
            let pop = new Audio('sound/pop' + i + ".mp3");
            pop.play();
            showParticle();
            clickBubbles();
            updateBubbleCount();
        });

        function showParticle() {
            let img = document.createElement("img");
            img.src = "https://static.vecteezy.com/system/resources/thumbnails/008/468/264/small_2x/isolated-clean-water-blue-drop-illustration-vector.jpg";
            img.style.width = "40px"; // Increased size
            img.style.height = "40px"; // Increased size
            img.style.position = "absolute";
            img.randHeight = Math.floor(Math.random() * window.innerHeight + 100);
            img.style.top = img.randHeight + "px";
            img.style.left = Math.floor(Math.random() * window.innerWidth - 100) + "px";
            document.body.appendChild(img);
            bubbleList.push(img);
        }

        function bubbleRise() {
            for (let i = bubbleList.length - 1; i >= 0; i--) {
                let element = bubbleList[i];
                if (element.randHeight > 0) {
                    element.randHeight -= 12;
                    element.style.top = element.randHeight + "px";
                } else {
                    element.remove();
                    bubbleList.splice(i, 1);
                }
            }
        }

        setInterval(bubbleRise, 16);

        function clickBubbles() {
            if (owned_artifact1) {
                bubbleCount += 2 * bubbleIncrement;
            } else {
                bubbleCount += bubbleIncrement;
            }
        }

        function updateBubbleCount() {
            document.getElementById("bubbleDisplay").innerHTML = comma(bubbleCount) + " Bubbles";
        }

        function comma(i) {
            return Number(i).toLocaleString();
        }

        function showTab1() {
            document.getElementById("bubbleDisplay").style.top = "20px";
            document.getElementById("bubbleDisplay").style.left = "auto";
            document.getElementById("tab3").style.display = "none";
            document.getElementById("tab2").style.display = "none";
            document.getElementById("tab1").style.display = "block";
        }

        function showTab2() {
            document.getElementById("bubbleDisplay").style.top = "6px";
            document.getElementById("bubbleDisplay").style.left = "6px";
            document.getElementById("tab3").style.display = "none";
            document.getElementById("tab2").style.display = "block";
            document.getElementById("tab1").style.display = "none";
        }

        function showTab3() {
            document.getElementById("bubbleDisplay").style.top = "6px";
            document.getElementById("bubbleDisplay").style.left = "6px";
            document.getElementById("tab3").style.display = "block";
            document.getElementById("tab2").style.display = "none";
            document.getElementById("tab1").style.display = "none";
        }

        let autoBubbleAmount = 0;

        function autoBubbles() {
            if (owned_artifact1) {
                bubbleCount += 2 * autoBubbleAmount;
            } else {
                bubbleCount += autoBubbleAmount;
            }
            updateBubbleCount();
        }

        setInterval(autoBubbles, 1000);

        let base_1 = 100;
        let cost_1 = 100;
        let count_1 = 0;

        function updateUpgrade1() {
            document.getElementById("upgrade1").innerHTML = "Increased Bubble Production +" + comma(count_1 + 1);
            document.getElementById("bubbleCost").innerHTML = comma(cost_1) + " Bubbles";
        }

        function upgrade1() {
            if (bubbleCount > cost_1) {
                count_1++;
                bubbleIncrement++;
                bubbleCount -= cost_1;
                cost_1 = Math.floor(base_1 * (1 + count_1) ** 1.1);
                updateUpgrade1();
                updateBubbleCount();
                showParticle();
            }
        }

        let base_2 = 1000;
        let cost_2 = 1000;
        let count_2 = 0;

        function updateUpgrade2() {
            document.getElementById("upgrade2").innerHTML = "Bubble Blower +" + comma(count_2);
            document.getElementById("bubbleCost2").innerHTML = comma(cost_2) + " Bubbles";
        }

        function upgrade2() {
            if (bubbleCount > cost_2) {
                count_2++;
                autoBubbleAmount++;
                bubbleCount -= cost_2;
                cost_2 = Math.floor(base_2 * (1 + count_2) ** 1.2);
                updateUpgrade2();
                updateBubbleCount();
                showParticle();
            }
        }

        let art_cost_1 = 100000;
        let owned_artifact1 = false;

        function artifact1() {
            if (!owned_artifact1 && bubbleCount > art_cost_1) {
                owned_artifact1 = true;
                bubbleCount -= art_cost_1;
                document.getElementById("artifact1").innerHTML = "Golden Bubbles 1x";
            } else {
                window.alert("You already own this!");
            }
        }
    </script>
</body>
</html>

---
layout: base
title: Student Home 
description: Home Page
hide: true
---


# Avanthika Daita

Avanthika Daita's journey starts here.


<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>GIF Button</title>
    <style>
        /* Define variables for colors and button styling */
        :root {
            --primary-color: #ff6347;
            --secondary-color: #f0f0f0;
            --font-stack: 'Arial', sans-serif;
        }

        body {
            font-family: var(--font-stack);
            background-color: var(--secondary-color);
            color: #333;
            text-align: center;
            padding: 20px;
        }

        #showGifBtn {
            background-color: var(--primary-color);
            color: white;
            padding: 10px 20px;
            border: none;
            border-radius: 5px;
            font-size: 16px;
            cursor: pointer;
            transition: background-color 0.3s ease;
        }

        #showGifBtn:hover {
            background-color: #e55347; /* Darker shade of primary color */
        }

        #gifImage {
            display: none;
            margin-top: 20px;
            border: 5px solid var(--primary-color);
            border-radius: 10px;
            transition: opacity 0.5s ease;
        }
    </style>
</head>
<body>
    <button id="showGifBtn">CLICK HERE!</button>
    <img id="gifImage" src="https://www.icegif.com/wp-content/uploads/2023/08/icegif-827.gif" alt="GIF Image" width="200">

    <script>
        document.getElementById("showGifBtn").addEventListener("click", function() {
            var gifImage = document.getElementById("gifImage");
            gifImage.style.display = "block";
        });
    </script>
</body>
</html>
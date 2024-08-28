---
layout: base
title: Student Home 
description: Home Page
hide: true
---


# Avanthika Daita

My journey starts here.


<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Cookie Button</title>
    <style>
        #cookieImage {
            display: none;
            margin-top: 20px;
        }
    </style>
</head>
<body>
    <button id="showCookieBtn">Click for a Cookie!</button>
    <img id="cookieImage" src="https://upload.wikimedia.org/wikipedia/commons/6/69/Chocolate_Chip_Cookie.jpg" alt="Cookie Image" width="200">

    <script>
        document.getElementById("showCookieBtn").addEventListener("click", function() {
            var cookieImage = document.getElementById("cookieImage");
            cookieImage.style.display = "block";
        });
    </script>
</body>
</html>

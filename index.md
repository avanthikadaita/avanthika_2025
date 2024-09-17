---
layout: base
title: Student Home
description: Home Page
hide: true
---

# Home Page

Welcome to Avanthika's corner of the web—where creativity, tech, and passion collide.

<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Interactive Hub</title>
    <style>
        :root {
            --primary-color: #6c63ff;
            --secondary-color: #f5f5f5;
            --accent-color: #ff6347;
            --font-stack: 'Poppins', sans-serif;
            --bg-gradient: linear-gradient(135deg, #6c63ff, #ff6347);
        }
body {
            font-family: var(--font-stack);
            background: var(--bg-gradient);
            color: white;
            text-align: center;
            padding: 50px;
        }
h1 {
            font-size: 3em;
            margin-bottom: 10px;
        }
p {
            font-size: 1.2em;
            margin-bottom: 40px;
        }
#showGifBtn {
            background-color: var(--accent-color);
            color: white;
            padding: 15px 30px;
            border: none;
            border-radius: 30px;
            font-size: 18px;
            cursor: pointer;
            transition: background-color 0.3s ease;
            box-shadow: 0px 5px 15px rgba(0, 0, 0, 0.2);
        }
#showGifBtn:hover {
            background-color: #e55347;
        }
#gifImage {
            display: none;
            margin-top: 20px;
            border: 5px solid white;
            border-radius: 20px;
            transition: opacity 0.5s ease;
            box-shadow: 0px 5px 15px rgba(0, 0, 0, 0.3);
        }
/* Slideshow container */
        .slideshow-container {
            position: relative;
            max-width: 100%;
            margin: auto;
        }
/* Hide the images by default */
        .mySlides {
            display: none;
        }
/* Image styling */
        img {
            width: 100%;
            border-radius: 15px;
            box-shadow: 0px 5px 15px rgba(0, 0, 0, 0.3);
        }
/* Navigation dots */
        .dot {
            height: 15px;
            width: 15px;
            margin: 0 2px;
            background-color: #bbb;
            border-radius: 50%;
            display: inline-block;
            transition: background-color 0.6s ease;
        }
.active {
            background-color: var(--primary-color);
        }
footer {
            margin-top: 50px;
            font-size: 0.9em;
            color: #f5f5f5;
        }
.social-links a {
            color: white;
            margin: 0 10px;
            text-decoration: none;
            font-size: 1.5em;
        }
    </style>
</head>
<body>

<!-- Slideshow -->
<div class="slideshow-container">

 <div class="mySlides">
            <img src="https://a.eu.mktgcdn.com/f/100004519/N2BB4ohwclor2uLoZ7XMHgJmxOZaMOokMdQqqXQAq3s.jpg" alt="Paris, France">
        </div>

<div class="mySlides">
            <img src="https://res.cloudinary.com/icelandtours/image/upload/v1667212174/northern_lights_iceland_person_with_torch_jonatan_pie_unsplash_a3402caa84.jpg" alt="Northern Lights, Iceland">
        </div>

<div class="mySlides">
            <img src="https://lp-cms-production.imgix.net/2019-06/16641625.jpg?w=1440&h=810&fit=crop&auto=format&q=75" alt="Machu Picchu, Peru">
        </div>

</div>

<!-- Dots to indicate current slide -->
<br>
    <div style="text-align:center">
        <span class="dot"></span> 
        <span class="dot"></span> 
        <span class="dot"></span> 
    </div>

<button id="showGifBtn">CHECK OUT THIS GIF!</button>
    <img id="gifImage" src="https://www.icegif.com/wp-content/uploads/2023/08/icegif-827.gif" alt="Cool GIF" width="300">

<footer>
        <div class="social-links">
            <a href="https://github.com/avanthikadaita" target="_blank">GitHub</a> |
            <a href="https://linkedin.com/in/avanthikadaita" target="_blank">LinkedIn</a>
        </div>
        <p>&copy; 2024 Avanthika Daita. All Rights Reserved.</p>
    </footer>

<script>
        let slideIndex = 0;
        showSlides();

        function showSlides() {
            let i;
            let slides = document.getElementsByClassName("mySlides");
            let dots = document.getElementsByClassName("dot");
            for (i = 0; i < slides.length; i++) {
                slides[i].style.display = "none";
            }
            slideIndex++;
            if (slideIndex > slides.length) {slideIndex = 1}
            for (i = 0; i < dots.length; i++) {
                dots[i].className = dots[i].className.replace(" active", "");
            }
            slides[slideIndex-1].style.display = "block";
            dots[slideIndex-1].className += " active";
            setTimeout(showSlides, 3000); // Change image every 3 seconds
        }

        document.getElementById("showGifBtn").addEventListener("click", function() {
            var gifImage = document.getElementById("gifImage");
            gifImage.style.display = "block";
        });
    </script>
</body>
</html>

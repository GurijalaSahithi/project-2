<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Image Slider</title>
  <link rel="stylesheet" href="styles.css">
</head>
<body>
  <div class="slider-container">
    <div class="slider">
      <div class="slide" style="background-image: url('![machu picchu](https://github.com/user-attachments/assets/e3665598-1fc4-4f23-a63e-f2814cb4a541)
');">
        <div class="caption">Machu Picchu</div>
      </div>
      <div class="slide" style="background-image: url('image2.jpg');">
        <div class="caption">Grand Canyon</div>
      </div>
      <div class="slide" style="background-image: url('image3.jpg');">
        <div class="caption">Eiffel Tower</div>
      </div>
    </div>
    <div class="controls">
      <button id="prev">❮</button>
      <button id="next">❯</button>
    </div>
    <div class="thumbnails">
      <img src="![machu picchu](https://github.com/user-attachments/assets/e7e46030-663c-4aaa-91a9-4f95bfd3d4f9)
" data-index="0" alt="Thumbnail 1">
      <img src="image2.jpg" data-index="1" alt="Thumbnail 2">
      <img src="image3.jpg" data-index="2" alt="Thumbnail 3">
    </div>
  </div>
  <script src="script.js"></script>
</body>
</html>


/* Base Styles */
body {
  margin: 0;
  font-family: Arial, sans-serif;
  background: #f4f4f4;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

/* Slider Container */
.slider-container {
  position: relative;
  width: 80%;
  max-width: 800px;
  overflow: hidden;
  border-radius: 10px;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
}

/* Slider */
.slider {
  display: flex;
  transition: transform 0.5s ease-in-out;
}

/* Slide */
.slide {
  min-width: 100%;
  height: 400px;
  background-size: cover;
  background-position: center;
  position: relative;
}

.caption {
  position: absolute;
  bottom: 10%;
  left: 5%;
  color: #fff;
  background: rgba(0, 0, 0, 0.5);
  padding: 10px;
  border-radius: 5px;
}

/* Controls */
.controls {
  position: absolute;
  top: 50%;
  width: 100%;
  display: flex;
  justify-content: space-between;
  transform: translateY(-50%);
}

.controls button {
  background: rgba(0, 0, 0, 0.5);
  color: white;
  border: none;
  padding: 10px 15px;
  cursor: pointer;
  border-radius: 50%;
}

.controls button:hover {
  background: rgba(0, 0, 0, 0.8);
}

/* Thumbnails */
.thumbnails {
  display: flex;
  justify-content: center;
  margin: 10px 0;
}

.thumbnails img {
  width: 60px;
  height: 40px;
  margin: 0 5px;
  cursor: pointer;
  opacity: 0.7;
  transition: opacity 0.3s;
}

.thumbnails img:hover,
.thumbnails img.active {
  opacity: 1;
}


const slider = document.querySelector('.slider');
const slides = document.querySelectorAll('.slide');
const prevButton = document.getElementById('prev');
const nextButton = document.getElementById('next');
const thumbnails = document.querySelectorAll('.thumbnails img');

let currentIndex = 0;

// Function to update slider position
function updateSlider() {
  slider.style.transform = translateX(-${currentIndex * 100}%);
  thumbnails.forEach((thumb, index) => {
    thumb.classList.toggle('active', index === currentIndex);
  });
}

// Navigate to the next slide
nextButton.addEventListener('click', () => {
  currentIndex = (currentIndex + 1) % slides.length;
  updateSlider();
});

// Navigate to the previous slide
prevButton.addEventListener('click', () => {
  currentIndex = (currentIndex - 1 + slides.length) % slides.length;
  updateSlider();
});

// Thumbnail navigation
thumbnails.forEach((thumb, index) => {
  thumb.addEventListener('click', () => {
    currentIndex = index;
    updateSlider();
  });
});

// Auto-slide every 5 seconds
setInterval(() => {
  currentIndex = (currentIndex + 1) % slides.length;
  updateSlider();
}, 5000);

// Initialize the slider
updateSlider();

# Ex05 Image Carousel
## Date:18/3/26

## AIM
To create a Image Carousel using React 

## ALGORITHM
### STEP 1 Initial Setup:
Input: A list of images to display in the carousel.

Output: A component displaying the images with navigation controls (e.g., next/previous buttons).

### Step 2 State Management:
Use a state variable (currentIndex) to track the index of the current image displayed.

The carousel starts with the first image, so initialize currentIndex to 0.

### Step 3 Navigation Controls:
Next Image: When the "Next" button is clicked, increment currentIndex.

If currentIndex is at the end of the image list (last image), loop back to the first image using modulo:
currentIndex = (currentIndex + 1) % images.length;

Previous Image: When the "Previous" button is clicked, decrement currentIndex.

If currentIndex is at the beginning (first image), loop back to the last image:
currentIndex = (currentIndex - 1 + images.length) % images.length;

### Step 4 Displaying the Image:
The currentIndex determines which image is displayed.

Using the currentIndex, display the corresponding image from the images list.

### Step 5 Auto-Rotation:
Set an interval to automatically change the image after a set amount of time (e.g., 3 seconds).

Use setInterval to call the nextImage() function at regular intervals.

Clean up the interval when the component unmounts using clearInterval to prevent memory leaks.

## PROGRAM
```
App.js
import React, { useState, useEffect } from "react";
import "./App.css";

// Working image links ✅
const images = [
  "https://picsum.photos/600/300?random=1",
  "https://picsum.photos/600/300?random=2",
  "https://picsum.photos/600/300?random=3"
];

function App() {
  const [index, setIndex] = useState(0);

  // Next slide
  const nextSlide = () => {
    setIndex((index + 1) % images.length);
  };

  // Previous slide
  const prevSlide = () => {
    setIndex((index - 1 + images.length) % images.length);
  };

  // Auto slide every 3 seconds
  useEffect(() => {
    const interval = setInterval(nextSlide, 3000);
    return () => clearInterval(interval);
  });

  return (
    <div className="container">
      <h1>React Carousel</h1>

      <div className="carousel">
        <button onClick={prevSlide}>❮</button>

        <img src={images[index]} alt="slide" />

        <button onClick={nextSlide}>❯</button>
      </div>
    </div>
  );
}

export default App;
```
```
App.css
body {
  margin: 0;
  font-family: Arial;
  background: linear-gradient(to right, #ff9a9e, #fad0c4);
}

.container {
  text-align: center;
  margin-top: 50px;
}

h1 {
  color: #333;
}

/* Carousel layout */
.carousel {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 20px;
}

/* Image styling */
img {
  width: 600px;
  height: 300px;
  border-radius: 10px;
  object-fit: cover;
  box-shadow: 0 5px 15px rgba(0,0,0,0.3);
}

/* Buttons */
button {
  font-size: 24px;
  padding: 10px 15px;
  border: none;
  background: #333;
  color: white;
  cursor: pointer;
  border-radius: 50%;
  transition: 0.3s;
}

button:hover {
  background: #555;
}
```


## OUTPUT
<img width="1712" height="862" alt="image" src="https://github.com/user-attachments/assets/9c653a54-3b77-4f6c-a563-1268138a2c01" />


## RESULT
The program for creating Image Carousel using React is executed successfully.

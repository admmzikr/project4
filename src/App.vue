<template>
  <div id="app">
    <h1>Vue Click Counter & Box Color Changer</h1>
    
    <div class="container">
      <!-- Click Counter -->
      <div class="section">
        <h2>Click Counter</h2>
        <button @click="counter++" class="action-btn">Clicked {{ counter }} times</button>
      </div>

      <!-- Box Color Changer -->
      <div class="section">
        <h2>Box Color Changer</h2>
        <div class="color-box" :style="{ backgroundColor: currentColor }"></div>
        <button @click="changeColor" class="action-btn">Change Color</button>
      </div>

      <!-- Image Carousel -->
      <div class="section">
        <h2>Image Carousel</h2>
        <div class="carousel">
          <img :src="images[currentImage]" :alt="'Image ' + (currentImage + 1)" />
          <div class="carousel-controls">
            <button @click="prevImage" class="action-btn">Previous</button>
            <button @click="nextImage" class="action-btn">Next</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      counter: 0,
      colors: ['red', 'blue', 'green', 'yellow'],
      currentColor: 'red',
      images: [
        'https://via.placeholder.com/200x150/FF0000',
        'https://via.placeholder.com/200x150/00FF00',
        'https://via.placeholder.com/200x150/0000FF'
      ],
      currentImage: 0
    };
  },
  methods: {
    changeColor() {
      const randomIndex = Math.floor(Math.random() * this.colors.length);
      this.currentColor = this.colors[randomIndex];
    },
    prevImage() {
      if (this.currentImage > 0) {
        this.currentImage--;
      } else {
        this.currentImage = this.images.length - 1;
      }
    },
    nextImage() {
      if (this.currentImage < this.images.length - 1) {
        this.currentImage++;
      } else {
        this.currentImage = 0;
      }
    }
  }
};
</script>

<style scoped>
#app {
  font-family: 'Arial', sans-serif;
  text-align: center;
  background-color: #f5f5f5;
  padding: 20px;
}

h1 {
  font-size: 2.5rem;
  margin-bottom: 20px;
}

.container {
  display: flex;
  flex-direction: column;
  gap: 30px;
  align-items: center;
}

.section {
  background-color: #fff;
  padding: 20px;
  width: 100%;
  max-width: 400px;
  border-radius: 8px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  text-align: center;
}

.action-btn {
  background-color: #007bff;
  color: white;
  border: none;
  padding: 10px 20px;
  margin-top: 10px;
  border-radius: 5px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.action-btn:hover {
  background-color: #0056b3;
}

.color-box {
  width: 100px;
  height: 100px;
  margin: 0 auto 10px;
  border-radius: 5px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.2);
}

.carousel {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.carousel img {
  width: 200px;
  height: 150px;
  object-fit: cover;
  border-radius: 5px;
  margin-bottom: 10px;
}

.carousel-controls {
  display: flex;
  gap: 10px;
}
</style>
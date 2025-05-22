---
layout: page
title: Spinning Cats
published: true
nav_exclude: true
---

<div class="cats-container">
  <h1>SPINNING CATS EXTRAVAGANZA!</h1>
  <p style="font-size: 1.5em; color: #ff00ff; text-shadow: 2px 2px 0px #00ff00;">Watch as everything spins endlessly while cats do cat things!</p>

  <div class="video-container">
    <iframe width="560" height="315" src="https://www.youtube.com/embed/8WCmS9fIlZo" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
  </div>

  <div id="cat-container" style="position: relative; height: 60vh; width: 100%; overflow: hidden; margin: 2rem 0;"></div>
</div>

<script>
  // Bouncing cat animation
  class BouncingCat {
    constructor(container) {
      this.container = container;
      this.img = document.createElement('img');
      this.img.className = 'spinning-cat bouncing-cat';
      this.img.style.position = 'absolute';
      this.img.style.width = '150px';
      this.img.style.zIndex = '10';
      this.container.appendChild(this.img);
      
      // Get video element for collision detection
      this.video = document.querySelector('.video-container iframe');
      this.videoRect = this.video?.getBoundingClientRect();
      
      // Random starting position and velocity
      this.x = Math.random() * (container.clientWidth - 150);
      this.y = Math.random() * (container.clientHeight - 150);
      this.vx = (Math.random() - 0.5) * 10;
      this.vy = (Math.random() - 0.5) * 10;
      
      // Load random cat image
      this.loadCat();
    }
    
    async loadCat() {
      const response = await fetch('https://api.thecatapi.com/v1/images/search');
      const [cat] = await response.json();
      this.img.src = cat.url;
      this.img.alt = 'Bouncing cat';
    }
    
    update() {
      this.x += this.vx;
      this.y += this.vy;
      
      // Update video position if needed
      if (this.video) {
        this.videoRect = this.video.getBoundingClientRect();
        const containerRect = this.container.getBoundingClientRect();
        
        // Calculate video position relative to container
        const videoLeft = this.videoRect.left - containerRect.left;
        const videoTop = this.videoRect.top - containerRect.top;
        const videoRight = videoLeft + this.videoRect.width;
        const videoBottom = videoTop + this.videoRect.height;
        
        // Check for collision with video
        const catRight = this.x + 150;
        const catBottom = this.y + 150;
        
        if ((this.x < videoRight && catRight > videoLeft &&
             this.y < videoBottom && catBottom > videoTop)) {
          // Determine which side was hit
          const hitLeft = Math.abs(this.x - videoRight) < Math.abs(catRight - videoLeft);
          const hitTop = Math.abs(this.y - videoBottom) < Math.abs(catBottom - videoTop);
          
          if (hitLeft || (catRight > videoLeft && this.x < videoRight)) {
            this.vx = -this.vx;
          }
          if (hitTop || (catBottom > videoTop && this.y < videoBottom)) {
            this.vy = -this.vy;
          }
        }
      }
      
      // Bounce off walls
      if (this.x <= 0 || this.x >= this.container.clientWidth - 150) {
        this.vx = -this.vx;
      }
      if (this.y <= 0 || this.y >= this.container.clientHeight - 150) {
        this.vy = -this.vy;
      }
      
      this.img.style.left = `${this.x}px`;
      this.img.style.top = `${this.y}px`;
    }
  }

  // Create 3 bouncing cats
  document.addEventListener('DOMContentLoaded', () => {
    const container = document.getElementById('cat-container');
    const cats = [
      new BouncingCat(container),
      new BouncingCat(container),
      new BouncingCat(container)
    ];
    
    // Animation loop
    function animate() {
      cats.forEach(cat => cat.update());
      requestAnimationFrame(animate);
    }
    animate();
  });
</script>

<style>
body {
  font-family: "Comic Sans MS", cursive, sans-serif;
  background-color: #ffccff;
  background-image: url('data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==');
  color: #0000ff;
  text-align: center;
}

.cats-container {
  max-width: 800px;
  margin: 2rem auto;
  padding: 2rem;
  background: #ffff00;
  border: 4px dashed #ff00ff;
  box-shadow: 8px 8px 0px #00ff00;
}

.video-container {
  position: relative;
  padding-bottom: 56.25%;
  height: 0;
  overflow: hidden;
  margin: 2rem 0;
  border: 3px solid #0000ff;
  background: #00ffff;
}
  
  .video-container iframe {
    animation: occasional-spin 20s linear infinite;
    border-radius: 8px;
  }
  
  .spinning-cat {
    animation: spin 10s linear infinite;
    z-index: 10;
    border-radius: 50%;
    object-fit: cover;
    border: 3px solid #f8f8f8;
    box-shadow: 0 2px 4px rgba(0,0,0,0.1);
  }

  .video-container iframe {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
  }

  @keyframes spin {
    from { transform: rotate(0deg); }
    to { transform: rotate(360deg); }
  }

  @keyframes occasional-spin {
    0% { transform: rotate(0deg); }
    20% { transform: rotate(0deg); }
    30% { transform: rotate(360deg); }
    50% { transform: rotate(360deg); }
    60% { transform: rotate(0deg); }
    100% { transform: rotate(0deg); }
  }

.btn {
  background: #ff0000;
  color: #ffff00;
  padding: 0.8rem 1.5rem;
  border: 3px outset #000000;
  font-weight: bold;
  font-size: 1.2em;
  cursor: pointer;
  transition: all 0.3s;
  display: inline-block;
  margin: 1rem;
  text-decoration: none;
}

.btn:hover {
  background: #ff6600;
  transform: scale(1.1) rotate(5deg);
}

h1 {
  color: #ff00ff;
  text-shadow: 3px 3px 0px #00ff00;
  font-size: 3em;
}
</style>

<!-- Windows 98 Popup -->
<div id="win98-popup" style="display: none; position: fixed; top: 50%; left: 50%; transform: translate(-50%, -50%); width: 300px; z-index: 2000; font-family: 'MS Sans Serif', sans-serif;">
  <div style="background: #000080; color: white; padding: 4px 8px; font-weight: bold; display: flex; justify-content: space-between;">
    <span>Alert</span>
    <span style="cursor: pointer;" onclick="document.getElementById('win98-popup').style.display='none'">X</span>
  </div>
  <div style="background: #c0c0c0; padding: 16px; border: 2px solid #000000; box-shadow: 2px 2px 0px #808080;">
    <div style="display: flex; align-items: center; margin-bottom: 16px;">
      <img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABAAAAAQCAYAAAAf8/9hAAAABmJLR0QA/wD/AP+gvaeTAAAACXBIWXMAAAsTAAALEwEAmpwYAAAAB3RJTUUH4AkEEjIZJY5xJQAAAB1pVFh0Q29tbWVudAAAAAAAQ3JlYXRlZCB3aXRoIEdJTVBkLmUHAAAAJklEQVQ4y2NgGAWjYTBgwMhgDPD/Axn/gfR/EPs/lM3AwMAAANQ5JQjQJQ0AAAAASUVORK5CYII="
           style="width: 32px; height: 32px; margin-right: 16px;" alt="Warning">
      <span style="font-size: 14px;">Your Windows 98 is out of date. Please update to Windows ME for better performance.</span>
    </div>
    <button style="float: right; padding: 4px 12px; background: #c0c0c0; border: 2px outset #ffffff;"
            onclick="document.getElementById('win98-popup').style.display='none'">
      OK
    </button>
  </div>
</div>

<script>
// Show Windows 98 popup randomly between 30-90 seconds
setTimeout(() => {
  document.getElementById('win98-popup').style.display = 'block';
}, Math.random() * 60000 + 30000);
</script>

<div style="position: fixed; bottom: 20px; right: 20px; z-index: 1000;">
  <p style="font-size: 24px; color: lime; text-shadow: 2px 2px 0px purple;">😻 More Cats! 😻</p>
</div>
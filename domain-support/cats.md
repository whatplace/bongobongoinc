---
layout: page
title: Spinning Cats
published: true
nav_exclude: true
---

<div class="page-content">
  <h2>Enjoy these spinning cats!</h2>
  <p>Watch as everything spins endlessly while cats do cat things.</p>

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
  .video-container {
    position: relative;
    padding-bottom: 56.25%;
    height: 0;
    overflow: hidden;
    margin: 2rem 0;
    border-radius: 8px;
    box-shadow: 0 4px 8px rgba(0,0,0,0.1);
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

  .page-content {
    max-width: 800px;
    margin: 0 auto;
    padding: 0 1rem;
  }
</style>
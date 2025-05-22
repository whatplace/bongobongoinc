---
title: Bongo Bongo Inc
layout: page
---

# Welcome to Bongo Bongo Inc!

<div class="bongo-container">
  <div class="tenor-gif-embed" data-postid="16269826" data-share-method="host" data-aspect-ratio="1.62437" data-width="100%">
    <a href="https://tenor.com/view/bongo-cat-transparent-table-tap-cute-tapping-table-gif-16269826">Bongo Cat Transparent Sticker</a>
    from <a href="https://tenor.com/search/bongo+cat-stickers">Bongo Cat Stickers</a>
  </div>
  <script type="text/javascript" async src="https://tenor.com/embed.js"></script>
</div>

<div class="links">
  <a href="{{ '/domain-support' | relative_url }}" class="btn">Domain Registration</a>
  <a href="{{ '/cats' | relative_url }}" class="btn">Cat Gallery</a>
  <a href="{{ '/about' | relative_url }}" class="btn">About Us</a>
</div>

<style>
body {
  font-family: "Comic Sans MS", cursive, sans-serif;
  background-color: #ffccff;
  background-image: url('data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==');
  color: #0000ff;
  text-align: center;
}

.bongo-container {
  max-width: 600px;
  margin: 2rem auto;
  padding: 2rem;
  background: #ffff00;
  border: 4px dashed #ff00ff;
  box-shadow: 8px 8px 0px #00ff00;
}

.links {
  margin-top: 2rem;
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
  margin: 0 1rem;
  display: inline-block;
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

<script>
// Fetch random cat image every 30 seconds
function fetchCat() {
  fetch('https://api.thecatapi.com/v1/images/search')
    .then(response => response.json())
    .then(data => {
      const catImg = document.getElementById('cat-image');
      catImg.src = data[0].url;
      catImg.style.display = 'block';
    })
    .catch(error => console.error('Error fetching cat:', error));
}

// Initial fetch and set interval
fetchCat();
setInterval(fetchCat, 30000);
</script>

<div style="position: fixed; bottom: 20px; right: 20px; z-index: 1000;">
  <img id="cat-image" src="" alt="Random Cat" style="display: none; max-width: 200px; border: 5px solid hotpink;">
  <p style="font-size: 24px; color: lime; text-shadow: 2px 2px 0px purple;">😻 Random Cat! 😻</p>
</div>

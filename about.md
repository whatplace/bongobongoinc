---
layout: page
title: About Our Team
permalink: /about/
---

<div class="about-container">

# Welcome to mathongosbongos.com!

We're a totally rad team bringing you the best domain registration experience since 1998!

## Our Departments

<div style="display: flex; margin-top: 20px;">
  <div class="dept-box">
    <h3>IT Department</h3>
    <p>Keeping the tubes flowing since '98!</p>
    <p>Email: <span style="color: #ff0000;">hr.noreply@mathongosbongos.com</span></p>
  </div>
  
  <div class="dept-box">
    <h3>HR Department</h3>
    <p>We're here to help (maybe)!</p>
    <p>Email: <span style="color: #ff0000;">hr.noreply@mathongosbongos.com</span></p>
  </div>
</div>

<div style="margin-top: 30px; text-align: center;">
  <img src="https://web.archive.org/web/19991013052021im_/http://www.geocities.com/Heartland/Plains/4482/undercon.gif" alt="Under Construction" style="border: none;">
  <p style="font-size: 24px; color: #ff00ff; text-shadow: 3px 3px 0px #00ff00;">Proudly serving the internet since the dial-up days!</p>
  <a href="{{ '/' | relative_url }}" class="btn">Back to Home</a>
</div>

</div>

<style>
body {
  font-family: "Comic Sans MS", cursive, sans-serif;
  background-color: #ffccff;
  background-image: url('data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==');
  color: #0000ff;
}

.about-container {
  max-width: 800px;
  margin: 2rem auto;
  padding: 2rem;
  background: #ffff00;
  border: 4px dashed #ff00ff;
  box-shadow: 8px 8px 0px #00ff00;
}

h1, h2, h3 {
  color: #ff00ff;
  text-shadow: 3px 3px 0px #00ff00;
}

.dept-box {
  background: #00ffff;
  padding: 1rem;
  margin: 0 0.5rem;
  border: 3px solid #0000ff;
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
  margin-top: 1rem;
  text-decoration: none;
}

.btn:hover {
  background: #ff6600;
  transform: scale(1.1) rotate(5deg);
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
  <img id="cat-image" src="" alt="Random Cat" style="display: none; max-width: 200px; border: 5px solid hotpink;">
  <p style="font-size: 24px; color: lime; text-shadow: 2px 2px 0px purple;">😻 Random Cat! 😻</p>
</div>

---
title: Domain Registration & Payment
layout: page
---

# Domain Registration for mathongosbongos.com

<div class="payment-form">
  <h2>Register or Renew Your Domain</h2>
  
  <form>
    <div class="form-group">
      <label for="domain">Domain Name:</label>
      <input type="text" id="domain" name="domain" placeholder="mathongosbongos.com">
    </div>
    
    <div class="form-group">
      <label for="years">Registration Period:</label>
      <select id="years" name="years">
        <option value="1">1 Year ($12.99)</option>
        <option value="2">2 Years ($24.99)</option>
        <option value="5">5 Years ($59.99)</option>
      </select>
    </div>
    
    <button type="submit" class="btn">Proceed to Payment</button>
  </form>
</div>

## Support Information

For assistance with domain registration or payment issues:
- Email: support@mathongosbongos.com
- Phone: 1-800-MATHONGOS
- Live Chat: Available 24/7

<style>
body {
  font-family: "Comic Sans MS", cursive, sans-serif;
  background-color: #ffccff;
  background-image: url('data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==');
  color: #0000ff;
}

.payment-form {
  max-width: 500px;
  margin: 2rem auto;
  padding: 2rem;
  background: #ffff00;
  border: 4px dashed #ff00ff;
  box-shadow: 8px 8px 0px #00ff00;
}

.form-group {
  margin-bottom: 1rem;
}

.form-group label {
  font-weight: bold;
  text-shadow: 2px 2px 0px #ff0000;
}

input, select {
  background-color: #00ffff;
  border: 3px solid #0000ff;
  padding: 8px;
  font-family: "Comic Sans MS", cursive, sans-serif;
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
}

.btn:hover {
  background: #ff6600;
  transform: scale(1.1) rotate(5deg);
}

h1, h2 {
  color: #ff00ff;
  text-shadow: 3px 3px 0px #00ff00;
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
      <img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABAAAAAQCAYAAAAf8/9hAAAABmJLR0QA/wD/AP+gvaeTAAAACXBIWXMAAAsTAAALEwEAmpwYAAAAB3RJTUUH4AkEEjIZJY5xJQAAAB1pVFh0Q29tbWVudAAAAAAAQ3JlYXRlZCB3aXRoIEdJTVBkLmUHAAAAJklEQVQ4y2NgGAWjYBSMAlIAI4MxwP8PZPwH0v9B7P9QNgMDAwMAE1QJ5QjQJQ0AAAAASUVORK5CYII="
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

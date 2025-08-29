<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>JavaScript Mastery</title>
  <style>
    body { font-family: Arial, sans-serif; padding: 20px; }
    .highlight { background-color: yellow; font-weight: bold; }
    #countdown { font-size: 1.2em; margin-top: 10px; }
  </style>
</head>
<body>

  <h1>JavaScript Mastery</h1>

  <!-- Part 1: Basics -->
  <h2>Part 1: Basics</h2>
  <input type="text" id="userName" placeholder="Enter your name" />
  <input type="number" id="userAge" placeholder="Enter your age" />
  <button onclick="checkUser()">Submit</button>
  <p id="basicOutput"></p>

  <!-- Part 2: Functions -->
  <h2>Part 2: Functions</h2>
  <input type="number" id="price" placeholder="Price" />
  <input type="number" id="tax" placeholder="Tax Rate (e.g. 0.15)" />
  <button onclick="showTotal()">Calculate Total</button>
  <p id="totalOutput"></p>

  <!-- Part 3: Loops -->
  <h2>Part 3: Loops</h2>
  <button onclick="startCountdown()">Start Countdown</button>
  <p id="countdown"></p>

  <!-- Part 4: DOM Manipulation -->
  <h2>Part 4: DOM Manipulation</h2>
  <button onclick="toggleHighlight()">Toggle Highlight</button>
  <p id="domText">Click the button to highlight me!</p>

  <button onclick="addListItem()">Add List Item</button>
  <ul id="dynamicList"></ul>

  <script src="script.js"></script>
</body>
</html>

// Part 1: Basics — Variables, Data Types, Conditionals
function checkUser() {
  let name = document.getElementById("userName").value;
  let age = parseInt(document.getElementById("userAge").value);
  let output = "";

  if (!name || isNaN(age)) {
    output = "Please enter valid name and age.";
  } else if (age >= 18) {
    output = `Welcome, ${name}. You're an adult.`;
  } else {
    output = `Hi ${name}, you're still a minor.`;
  }

  document.getElementById("basicOutput").textContent = output;
}

// Part 2: Functions — Reusable Logic
function calculateTotal(price, taxRate) {
  return (price + price * taxRate).toFixed(2);
}

function showTotal() {
  let price = parseFloat(document.getElementById("price").value);
  let tax = parseFloat(document.getElementById("tax").value);
  if (isNaN(price) || isNaN(tax)) {
    document.getElementById("totalOutput").textContent = "Enter valid numbers.";
    return;
  }
  let total = calculateTotal(price, tax);
  document.getElementById("totalOutput").textContent = `Total with tax: R${total}`;
}

// Part 3: Loops — Countdown Simulation
function startCountdown() {
  let count = 5;
  let display = document.getElementById("countdown");
  display.textContent = "";

  let interval = setInterval(() => {
    if (count > 0) {
      display.textContent = `Countdown: ${count}`;
      count--;
    } else {
      display.textContent = "Blast off!";
      clearInterval(interval);
    }
  }, 1000);
}

// Part 4: DOM Manipulation — Events & Dynamic Content
function toggleHighlight() {
  document.getElementById("domText").classList.toggle("highlight");
}

function addListItem() {
  let list = document.getElementById("dynamicList");
  let item = document.createElement("li");
  item.textContent = "New item added!";
  list.appendChild(item);
}

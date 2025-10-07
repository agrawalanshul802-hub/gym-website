<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Club7 Family Gym</title>
  <style>
   body {
  font-family: Arial, sans-serif;
  margin: 0;
  padding: 0; 
  background: url('D:/NEW PROJECT/image1.png') no-repeat center center fixed;
  background-size: cover;
  color: #fff;
}

    header {
      background: rgba(0,0,0,0.7);
      padding: 20px;
      text-align: center;
      font-size: 2em;
      font-weight: bold;
    }
    .container {
      background: rgba(0,0,0,0.7);
      margin: 20px auto;
      padding: 20px;
      max-width: 800px;
      border-radius: 10px;
      animation: fadeIn 1.2s ease-in-out;
    }
    .hidden { display: none; }

    /* LOGIN PAGE STYLING */
    #loginPage {
      max-width: 400px;
      text-align: center;
      padding: 40px;
      background: rgba(255,255,255,0.1);
      backdrop-filter: blur(8px);
      box-shadow: 0 8px 20px rgba(0,0,0,0.6);
      border-radius: 15px;
      margin-top: 100px;
    }
    #loginPage h2 {
      margin-bottom: 20px;
      color: #ff4d4d;
      font-size: 2em;
      letter-spacing: 1px;
    }
    .input-group {
      position: relative;
      margin-bottom: 20px;
    }
    .input-group input {
      width: 100%;
      padding: 12px 40px;
      border: none;
      border-radius: 30px;
      outline: none;
      font-size: 1em;
      background: rgba(255,255,255,0.9);
      color: #333;
    }
    .input-group i {
      position: absolute;
      top: 50%;
      left: 12px;
      transform: translateY(-50%);
      color: #555;
    }
    #loginPage button {
      width: 100%;
      padding: 12px;
      border: none;
      border-radius: 30px;
      background: linear-gradient(45deg, #e63946, #ff4d4d);
      color: white;
      font-size: 1.1em;
      cursor: pointer;
      transition: 0.3s;
    }
    #loginPage button:hover {
      background: linear-gradient(45deg, #ff4d4d, #e63946);
      transform: scale(1.05);
    }

    /* GENERAL STYLING */
    input, select, button {
      padding: 10px;
      margin: 5px 0;
      border: none;
      border-radius: 5px;
    }
    button { cursor: pointer; }
    h2 { border-bottom: 2px solid #e63946; padding-bottom: 5px; }
    table { width: 100%; border-collapse: collapse; margin-top: 10px; }
    th, td { padding: 10px; text-align: left; border-bottom: 1px solid #444; }
    .invoice { background: #fff; color: #000; padding: 20px; border-radius: 10px; }

    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(-20px); }
      to { opacity: 1; transform: translateY(0); }
    }
  </style>
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
</head>
<body>
  <header>Club7 Family Gym</header>

  <div class="container" id="loginPage">
    <h2>Member Login</h2>
    <div class="input-group">
      <i class="fas fa-user"></i>
      <input type="text" id="username" placeholder="Enter Username">
    </div>
    <div class="input-group">
      <i class="fas fa-lock"></i>
      <input type="password" id="password" placeholder="Enter Password">
    </div>
    <button onclick="login()">Login</button>
    <p style="margin-top:10px; font-size:0.9em; color:#ccc;">(Hint: ID: <b>anshul1223</b>, Pass: <b>123456</b>)</p>
  </div>

  <div class="container hidden" id="gymDetails">
    <h2>Welcome to Club7 Family Gym</h2>
    <p>At Club7 Family Gym, we believe in building strength, endurance, and confidence. Our modern facilities and expert trainers help you reach your fitness goals effectively.</p>

    <h3>Our Equipment</h3>
    <ul>
      <li>Treadmills with heart-rate monitoring</li>
      <li>Multi-weight Dumbbells & Barbells</li>
      <li>Bench Press & Squat Racks</li>
      <li>Smith Machines & Cable Stations</li>
      <li>Ellipticals, Rowers, and Spin Bikes</li>
      <li>Yoga Mats & Functional Training Gear</li>
    </ul>

    <button onclick="showMemberships()">View Membership Plans</button>
    <button onclick="logout()">Logout</button>
  </div>

  <div class="container hidden" id="membershipPage">
    <h2>Membership Plans</h2>
    <table>
      <tr><th>Plan</th><th>Price</th></tr>
      <tr><td>Admission Fees</td><td>₹300 (one-time)</td></tr>
      <tr><td>1 Month</td><td>₹1400</td></tr>
      <tr><td>3 Months</td><td>₹3200</td></tr>
      <tr><td>6 Months</td><td>₹4500</td></tr>
      <tr><td>9 Months</td><td>₹5000</td></tr>
      <tr><td>12 Months</td><td>₹6500</td></tr>
      <tr><td>Membership Freezing (per month)</td><td>₹500</td></tr>
      <tr><td>Shoes Locker (yearly)</td><td>₹600</td></tr>
    </table>

    <h3>Select a Plan</h3>
    <select id="membership">
      <option value="">-- Select a Plan --</option>
      <option value="1 Month">1 Month - ₹1400</option>
      <option value="3 Months">3 Months - ₹3200</option>
      <option value="6 Months">6 Months - ₹4500</option>
      <option value="9 Months">9 Months - ₹5000</option>
      <option value="12 Months">12 Months - ₹6500</option>
    </select>
    <div>
      <label><input type="checkbox" id="freezing"> Membership Freezing (₹500)</label><br>
      <label><input type="checkbox" id="locker"> Shoes Locker (₹600)</label>
    </div>
    <button onclick="addToCart()">Add to Cart</button>

    <h3>Cart</h3>
    <table id="cartTable">
      <tr><th>Membership</th><th>Price</th><th>Action</th></tr>
    </table>
    <button onclick="checkout()">Generate Bill</button>
    <button onclick="goBackToDetails()">Go Back</button>
    <button onclick="logout()">Logout</button>

    <h3>Terms & Conditions</h3>
    <ul>
      <li>Fees once paid will not be refunded.</li>
      <li>Membership freezing per month: ₹500</li>
      <li>Shoes locker yearly: ₹600</li>
    </ul>
  </div>

  <div class="container hidden" id="invoicePage">
    <h2>Invoice</h2>
    <div class="invoice" id="invoice"></div>
    <button onclick="window.print()">Print Bill</button>
    <button onclick="goBackToMembership()">Go Back</button>
    <button onclick="logout()">Logout</button>
  </div>

  <script>
    let cart = [];

    function login() {
      let user = document.getElementById('username').value;
      let pass = document.getElementById('password').value;
      
      if(user === "anshul1223" && pass === "123456") {
        document.getElementById('loginPage').classList.add('hidden');
        document.getElementById('gymDetails').classList.remove('hidden');
      } else {
        alert("Invalid credentials! Use ID: anshul1223, Pass: 123456");
      }
    }

    function logout() {
      cart = [];
      document.getElementById('gymDetails').classList.add('hidden');
      document.getElementById('membershipPage').classList.add('hidden');
      document.getElementById('invoicePage').classList.add('hidden');
      document.getElementById('loginPage').classList.remove('hidden');
    }

    function showMemberships() {
      document.getElementById('gymDetails').classList.add('hidden');
      document.getElementById('membershipPage').classList.remove('hidden');
    }

    function goBackToDetails() {
      document.getElementById('membershipPage').classList.add('hidden');
      document.getElementById('gymDetails').classList.remove('hidden');
    }

    function goBackToMembership() {
      document.getElementById('invoicePage').classList.add('hidden');
      document.getElementById('membershipPage').classList.remove('hidden');
    }

    function addToCart() {
      let membership = document.getElementById('membership').value;
      let freezing = document.getElementById('freezing').checked;
      let locker = document.getElementById('locker').checked;

      if(membership) {
        let price = 0;
        if(membership === "1 Month") price = 1400;
        if(membership === "3 Months") price = 3200;
        if(membership === "6 Months") price = 4500;
        if(membership === "9 Months") price = 5000;
        if(membership === "12 Months") price = 6500;

        let extras = [];
        if(freezing) extras.push({name:"Membership Freezing", price:500});
        if(locker) extras.push({name:"Shoes Locker", price:600});

        cart.push({membership, price, extras});
        updateCart();
      } else {
        alert("Please select membership");
      }
    }

    function updateCart() {
      let table = document.getElementById('cartTable');
      table.innerHTML = '<tr><th>Membership</th><th>Price</th><th>Action</th></tr>';
      cart.forEach((item,index) => {
        let extraText = item.extras.map(e => e.name).join(", ");
        table.innerHTML += `<tr>
          <td>${item.membership}${extraText ? " + " + extraText : ""}</td>
          <td>₹${item.price + item.extras.reduce((sum,e)=>sum+e.price,0)}</td>
          <td><button onclick="removeItem(${index})">Remove</button></td>
        </tr>`;
      });
    }

    function removeItem(index) {
      cart.splice(index,1);
      updateCart();
    }

    function checkout() {
      if(cart.length === 0) {
        alert("Cart is empty");
        return;
      }

      let total = cart.reduce((sum, item) => sum + item.price + item.extras.reduce((s,e)=>s+e.price,0), 0);
      let admissionFee = 300;
      let grandTotal = total + admissionFee;

      let invoiceDate = new Date();
      let dueDate = new Date();
      dueDate.setDate(invoiceDate.getDate() + 30);

      let invoiceHTML = `
        <h3>Club7 Family Gym Invoice</h3>
        <p><strong>Invoice Date:</strong> ${invoiceDate.toLocaleDateString()}</p>
        <p><strong>Due Date:</strong> ${dueDate.toLocaleDateString()}</p>
        <table>
          <tr><th>Item</th><th>Price</th></tr>
          ${cart.map(item => `
            <tr><td>${item.membership}</td><td>₹${item.price}</td></tr>
            ${item.extras.map(e=>`<tr><td>${e.name}</td><td>₹${e.price}</td></tr>`).join("")}
          `).join('')}
        </table>
        <p><strong>Admission Fee:</strong> ₹300</p>
        <h3>Total: ₹${grandTotal}</h3>
      `;

      document.getElementById('membershipPage').classList.add('hidden');
      document.getElementById('invoicePage').classList.remove('hidden');
      document.getElementById('invoice').innerHTML = invoiceHTML;
    }
  </script>
</body>
</html>

<!DOCTYPE html>
<html lang="th">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Pastel Shop</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background-color: #fdf6f0;
      margin: 0;
      padding: 0;
    }
    header {
      background: #ffcad4;
      padding: 15px;
      text-align: center;
      font-size: 20px;
    }
    .container {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
      gap: 20px;
      padding: 20px;
    }
    .product {
      background: #fff;
      border-radius: 15px;
      padding: 15px;
      text-align: center;
      box-shadow: 0 4px 6px rgba(0,0,0,0.1);
    }
    .product img {
      width: 100%;
      border-radius: 10px;
    }
    button {
      background: #a2d2ff;
      border: none;
      padding: 10px 15px;
      border-radius: 10px;
      margin-top: 10px;
      cursor: pointer;
    }
    button:hover {
      background: #ffafcc;
    }
    .cart-link {
      text-align: right;
      margin: 10px 20px;
    }
    .cart-link a {
      text-decoration: none;
      background: #cdb4db;
      padding: 8px 12px;
      border-radius: 10px;
    }
  </style>
</head>
<body>
  <header>🌸 Pastel Shop</header>

  <div class="cart-link">
    <a href="cart.html">ไปที่ตะกร้า 🛒</a>
  </div>

  <div class="container">
    <div class="product">
      <img src="https://i.imgur.com/HT5M5iJ.jpg" alt="เสื้อยืด">
      <h3>เสื้อยืด</h3>
      <p>ราคา: 250 บาท</p>
      <button onclick="addToCart(1,'เสื้อยืด',250)">หยิบใส่ตะกร้า</button>
    </div>
    <div class="product">
      <img src="https://i.imgur.com/tY0Xn3a.jpg" alt="กางเกงยีนส์">
      <h3>กางเกงยีนส์</h3>
      <p>ราคา: 500 บาท</p>
      <button onclick="addToCart(2,'กางเกงยีนส์',500)">หยิบใส่ตะกร้า</button>
    </div>
    <div class="product">
      <img src="https://i.imgur.com/85KdK3W.jpg" alt="หูฟัง">
      <h3>หูฟัง</h3>
      <p>ราคา: 800 บาท</p>
      <button onclick="addToCart(3,'หูฟัง',800)">หยิบใส่ตะกร้า</button>
    </div>
    <div class="product">
      <img src="https://i.imgur.com/ur6y7yF.jpg" alt="โทรศัพท์">
      <h3>โทรศัพท์</h3>
      <p>ราคา: 10,000 บาท</p>
      <button onclick="addToCart(4,'โทรศัพท์',10000)">หยิบใส่ตะกร้า</button>
    </div>
  </div>

  <script>
    function addToCart(id, name, price) {
      let cart = JSON.parse(localStorage.getItem("cart")) || [];
      let product = cart.find(item => item.id === id);
      if(product){
        product.quantity += 1;
      } else {
        cart.push({id, name, price, quantity:1});
      }
      localStorage.setItem("cart", JSON.stringify(cart));
      alert(name + " ถูกเพิ่มลงในตะกร้าแล้ว!");
    }
  </script>
</body>
</html>
<!DOCTYPE html>
<html lang="th">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>ตะกร้าสินค้า</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background-color: #fdf6f0;
      padding: 20px;
    }
    h2 {
      text-align: center;
    }
    table {
      width: 100%;
      border-collapse: collapse;
      margin-top: 20px;
    }
    th, td {
      border: 1px solid #ccc;
      padding: 10px;
      text-align: center;
    }
    th {
      background: #cdb4db;
    }
    .back-link {
      display: block;
      margin-top: 20px;
      text-align: center;
    }
  </style>
</head>
<body>
  <h2>🛒 ตะกร้าสินค้า</h2>
  <table>
    <thead>
      <tr>
        <th>สินค้า</th>
        <th>ราคา</th>
        <th>จำนวน</th>
        <th>รวม</th>
      </tr>
    </thead>
    <tbody id="cart-items"></tbody>
  </table>
  <h3 id="total"></h3>
  <a href="index.html" class="back-link">⬅️ เลือกซื้อสินค้าต่อ</a>

  <script>
    let cart = JSON.parse(localStorage.getItem("cart")) || [];
    let cartItems = document.getElementById("cart-items");
    let total = 0;

    if(cart.length === 0){
      cartItems.innerHTML = '<tr><td colspan="4">ไม่มีสินค้าในตะกร้า</td></tr>';
    } else {
      cart.forEach(item => {
        let row = document.createElement("tr");
        row.innerHTML = `
          <td>${item.name}</td>
          <td>${item.price} บาท</td>
          <td>${item.quantity}</td>
          <td>${item.price * item.quantity} บาท</td>
        `;
        cartItems.appendChild(row);
        total += item.price * item.quantity;
      });
      document.getElementById("total").innerText = "ยอดรวมทั้งหมด: " + total + " บาท";
    }
  </script>
</body>
</html>
<!DOCTYPE html>
<html lang="th">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>ตะกร้าสินค้า</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background-color: #fdf6f0;
      padding: 20px;
    }
    h2 {
      text-align: center;
    }
    table {
      width: 100%;
      border-collapse: collapse;
      margin-top: 20px;
    }
    th, td {
      border: 1px solid #ccc;
      padding: 10px;
      text-align: center;
    }
    th {
      background: #cdb4db;
    }
    .back-link {
      display: block;
      margin-top: 20px;
      text-align: center;
    }
  </style>
</head>
<body>
  <h2>🛒 ตะกร้าสินค้า</h2>
  <table>
    <thead>
      <tr>
        <th>สินค้า</th>
        <th>ราคา</th>
        <th>จำนวน</th>
        <th>รวม</th>
      </tr>
    </thead>
    <tbody id="cart-items"></tbody>
  </table>
  <h3 id="total"></h3>
  <a href="index.html" class="back-link">⬅️ เลือกซื้อสินค้าต่อ</a>

  <script>
    let cart = JSON.parse(localStorage.getItem("cart")) || [];
    let cartItems = document.getElementById("cart-items");
    let total = 0;

    if(cart.length === 0){
      cartItems.innerHTML = '<tr><td colspan="4">ไม่มีสินค้าในตะกร้า</td></tr>';
    } else {
      cart.forEach(item => {
        let row = document.createElement("tr");
        row.innerHTML = `
          <td>${item.name}</td>
          <td>${item.price} บาท</td>
          <td>${item.quantity}</td>
          <td>${item.price * item.quantity} บาท</td>
        `;
        cartItems.appendChild(row);
        total += item.price * item.quantity;
      });
      document.getElementById("total").innerText = "ยอดรวมทั้งหมด: " + total + " บาท";
    }
  </script>
</body>
</html>

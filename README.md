<!DOCTYPE html>
<html lang="th">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Pastel Shop</title>
  <style>
    body { font-family: Arial, sans-serif; background-color: #fdf6f0; margin:0; padding:0; }
    header { background:#ffcad4; padding:15px; text-align:center; font-size:20px; }
    .container { display:grid; grid-template-columns:repeat(auto-fit, minmax(220px,1fr)); gap:20px; padding:20px; }
    .product { background:#fff; border-radius:15px; padding:15px; text-align:center; box-shadow:0 4px 6px rgba(0,0,0,0.1); }
    .product img { width:100%; border-radius:10px; }
    button { background:#a2d2ff; border:none; padding:10px 15px; border-radius:10px; margin-top:10px; cursor:pointer; }
    button:hover { background:#ffafcc; }
  </style>
</head>
<body>
  <header>🌸 Pastel Shop</header>

  <div class="container" id="product-list">
    <!-- สินค้าจะถูกเพิ่มด้วย JS -->
  </div>

  <script>
    const products = [
      {id:1, name:"เสื้อยืด", price:250, image:"https://i.imgur.com/HT5M5iJ.jpg"},
      {id:2, name:"กางเกงยีนส์", price:500, image:"https://i.imgur.com/tY0Xn3a.jpg"},
      {id:3, name:"หูฟัง", price:800, image:"https://i.imgur.com/85KdK3W.jpg"},
      {id:4, name:"โทรศัพท์", price:10000, image:"https://i.imgur.com/ur6y7yF.jpg"}
    ];

    const container = document.getElementById("product-list");

    products.forEach(p=>{
      const div = document.createElement("div");
      div.className = "product";
      div.innerHTML = `
        <img src="${p.image}" alt="${p.name}">
        <h3>${p.name}</h3>
        <p>ราคา: ${p.price} บาท</p>
        <button onclick="addToCart(${p.id})">หยิบใส่ตะกร้า</button>
      `;
      container.appendChild(div);
    });

    function addToCart(id){
      let cart = JSON.parse(localStorage.getItem("cart")) || [];
      const product = products.find(p=>p.id===id);
      let item = cart.find(i=>i.id===id);
      if(item){
        item.quantity += 1;
      } else {
        cart.push({id:product.id, name:product.name, price:product.price, quantity:1});
      }
      localStorage.setItem("cart", JSON.stringify(cart));
      // redirect ไปหน้าตะกร้า
      window.location.href = "cart.html";
    }
  </script>
</body>
</html>
<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01//EN" "http://www.w3.org/TR/html4/strict.dtd">
<html>
<head>
  <meta http-equiv="Content-Type" content="text/html; charset=utf-8">
  <meta http-equiv="Content-Style-Type" content="text/css">
  <title></title>
  <meta name="Generator" content="Cocoa HTML Writer">
  <meta name="CocoaVersion" content="2487.4">
  <style type="text/css">
    p.p1 {margin: 0.0px 0.0px 0.0px 0.0px; font: 12.0px Helvetica}
    p.p2 {margin: 0.0px 0.0px 0.0px 0.0px; font: 12.0px Helvetica; min-height: 14.0px}
  </style>
</head>
<body>
<p class="p1">&lt;!DOCTYPE html&gt;</p>
<p class="p1">&lt;html lang="th"&gt;</p>
<p class="p1">&lt;head&gt;</p>
<p class="p1"><span class="Apple-converted-space">  </span>&lt;meta charset="UTF-8"&gt;</p>
<p class="p1"><span class="Apple-converted-space">  </span>&lt;meta name="viewport" content="width=device-width, initial-scale=1.0"&gt;</p>
<p class="p1"><span class="Apple-converted-space">  </span>&lt;title&gt;ตะกร้าสินค้า - Pastel Shop&lt;/title&gt;</p>
<p class="p1"><span class="Apple-converted-space">  </span>&lt;style&gt;</p>
<p class="p1"><span class="Apple-converted-space">    </span>body {</p>
<p class="p1"><span class="Apple-converted-space">      </span>font-family: Arial, sans-serif;</p>
<p class="p1"><span class="Apple-converted-space">      </span>background: #fdf2f8;</p>
<p class="p1"><span class="Apple-converted-space">      </span>margin: 0;</p>
<p class="p1"><span class="Apple-converted-space">      </span>padding: 0;</p>
<p class="p1"><span class="Apple-converted-space">    </span>}</p>
<p class="p1"><span class="Apple-converted-space">    </span>header {</p>
<p class="p1"><span class="Apple-converted-space">      </span>background: #fbcfe8;</p>
<p class="p1"><span class="Apple-converted-space">      </span>padding: 15px;</p>
<p class="p1"><span class="Apple-converted-space">      </span>text-align: center;</p>
<p class="p1"><span class="Apple-converted-space">    </span>}</p>
<p class="p1"><span class="Apple-converted-space">    </span>header h1 {</p>
<p class="p1"><span class="Apple-converted-space">      </span>margin: 0;</p>
<p class="p1"><span class="Apple-converted-space">      </span>font-size: 24px;</p>
<p class="p1"><span class="Apple-converted-space">      </span>color: #5b2c6f;</p>
<p class="p1"><span class="Apple-converted-space">    </span>}</p>
<p class="p1"><span class="Apple-converted-space">    </span>.container {</p>
<p class="p1"><span class="Apple-converted-space">      </span>padding: 20px;</p>
<p class="p1"><span class="Apple-converted-space">    </span>}</p>
<p class="p1"><span class="Apple-converted-space">    </span>table {</p>
<p class="p1"><span class="Apple-converted-space">      </span>width: 100%;</p>
<p class="p1"><span class="Apple-converted-space">      </span>border-collapse: collapse;</p>
<p class="p1"><span class="Apple-converted-space">      </span>background: white;</p>
<p class="p1"><span class="Apple-converted-space">      </span>border-radius: 10px;</p>
<p class="p1"><span class="Apple-converted-space">      </span>overflow: hidden;</p>
<p class="p1"><span class="Apple-converted-space">    </span>}</p>
<p class="p1"><span class="Apple-converted-space">    </span>table th, table td {</p>
<p class="p1"><span class="Apple-converted-space">      </span>border: 1px solid #f9a8d4;</p>
<p class="p1"><span class="Apple-converted-space">      </span>padding: 12px;</p>
<p class="p1"><span class="Apple-converted-space">      </span>text-align: center;</p>
<p class="p1"><span class="Apple-converted-space">    </span>}</p>
<p class="p1"><span class="Apple-converted-space">    </span>table th {</p>
<p class="p1"><span class="Apple-converted-space">      </span>background: #fbcfe8;</p>
<p class="p1"><span class="Apple-converted-space">    </span>}</p>
<p class="p1"><span class="Apple-converted-space">    </span>.total {</p>
<p class="p1"><span class="Apple-converted-space">      </span>margin-top: 20px;</p>
<p class="p1"><span class="Apple-converted-space">      </span>font-size: 20px;</p>
<p class="p1"><span class="Apple-converted-space">      </span>text-align: right;</p>
<p class="p1"><span class="Apple-converted-space">    </span>}</p>
<p class="p1"><span class="Apple-converted-space">    </span>a {</p>
<p class="p1"><span class="Apple-converted-space">      </span>display: inline-block;</p>
<p class="p1"><span class="Apple-converted-space">      </span>margin-top: 15px;</p>
<p class="p1"><span class="Apple-converted-space">      </span>text-decoration: none;</p>
<p class="p1"><span class="Apple-converted-space">      </span>background: #a78bfa;</p>
<p class="p1"><span class="Apple-converted-space">      </span>color: white;</p>
<p class="p1"><span class="Apple-converted-space">      </span>padding: 10px 15px;</p>
<p class="p1"><span class="Apple-converted-space">      </span>border-radius: 8px;</p>
<p class="p1"><span class="Apple-converted-space">    </span>}</p>
<p class="p1"><span class="Apple-converted-space">    </span>a:hover {</p>
<p class="p1"><span class="Apple-converted-space">      </span>background: #7c3aed;</p>
<p class="p1"><span class="Apple-converted-space">    </span>}</p>
<p class="p1"><span class="Apple-converted-space">  </span>&lt;/style&gt;</p>
<p class="p1">&lt;/head&gt;</p>
<p class="p1">&lt;body&gt;</p>
<p class="p1"><span class="Apple-converted-space">  </span>&lt;header&gt;</p>
<p class="p1"><span class="Apple-converted-space">    </span>&lt;h1&gt;🛒 ตะกร้าสินค้า&lt;/h1&gt;</p>
<p class="p1"><span class="Apple-converted-space">  </span>&lt;/header&gt;</p>
<p class="p2"><br></p>
<p class="p1"><span class="Apple-converted-space">  </span>&lt;div class="container"&gt;</p>
<p class="p1"><span class="Apple-converted-space">    </span>&lt;table id="cart-table"&gt;</p>
<p class="p1"><span class="Apple-converted-space">      </span>&lt;thead&gt;</p>
<p class="p1"><span class="Apple-converted-space">        </span>&lt;tr&gt;</p>
<p class="p1"><span class="Apple-converted-space">          </span>&lt;th&gt;สินค้า&lt;/th&gt;</p>
<p class="p1"><span class="Apple-converted-space">          </span>&lt;th&gt;จำนวน&lt;/th&gt;</p>
<p class="p1"><span class="Apple-converted-space">          </span>&lt;th&gt;ราคา/ชิ้น&lt;/th&gt;</p>
<p class="p1"><span class="Apple-converted-space">          </span>&lt;th&gt;ราคารวม&lt;/th&gt;</p>
<p class="p1"><span class="Apple-converted-space">        </span>&lt;/tr&gt;</p>
<p class="p1"><span class="Apple-converted-space">      </span>&lt;/thead&gt;</p>
<p class="p1"><span class="Apple-converted-space">      </span>&lt;tbody&gt;&lt;/tbody&gt;</p>
<p class="p1"><span class="Apple-converted-space">    </span>&lt;/table&gt;</p>
<p class="p1"><span class="Apple-converted-space">    </span>&lt;div class="total" id="total"&gt;&lt;/div&gt;</p>
<p class="p1"><span class="Apple-converted-space">    </span>&lt;a href="index.html"&gt;⬅️ กลับไปซื้อเพิ่ม&lt;/a&gt;</p>
<p class="p1"><span class="Apple-converted-space">  </span>&lt;/div&gt;</p>
<p class="p2"><br></p>
<p class="p1"><span class="Apple-converted-space">  </span>&lt;script&gt;</p>
<p class="p1"><span class="Apple-converted-space">    </span>let cart = JSON.parse(localStorage.getItem("cart")) || [];</p>
<p class="p1"><span class="Apple-converted-space">    </span>const tbody = document.querySelector("#cart-table tbody");</p>
<p class="p1"><span class="Apple-converted-space">    </span>const totalDiv = document.getElementById("total");</p>
<p class="p2"><br></p>
<p class="p1"><span class="Apple-converted-space">    </span>function renderCart() {</p>
<p class="p1"><span class="Apple-converted-space">      </span>tbody.innerHTML = "";</p>
<p class="p1"><span class="Apple-converted-space">      </span>let total = 0;</p>
<p class="p2"><br></p>
<p class="p1"><span class="Apple-converted-space">      </span>cart.forEach(item =&gt; {</p>
<p class="p1"><span class="Apple-converted-space">        </span>let row = document.createElement("tr");</p>
<p class="p1"><span class="Apple-converted-space">        </span>let subtotal = item.price * item.qty;</p>
<p class="p1"><span class="Apple-converted-space">        </span>total += subtotal;</p>
<p class="p2"><br></p>
<p class="p1"><span class="Apple-converted-space">        </span>row.innerHTML = `</p>
<p class="p1"><span class="Apple-converted-space">          </span>&lt;td&gt;${item.name}&lt;/td&gt;</p>
<p class="p1"><span class="Apple-converted-space">          </span>&lt;td&gt;${item.qty}&lt;/td&gt;</p>
<p class="p1"><span class="Apple-converted-space">          </span>&lt;td&gt;${item.price} บาท&lt;/td&gt;</p>
<p class="p1"><span class="Apple-converted-space">          </span>&lt;td&gt;${subtotal} บาท&lt;/td&gt;</p>
<p class="p1"><span class="Apple-converted-space">        </span>`;</p>
<p class="p1"><span class="Apple-converted-space">        </span>tbody.appendChild(row);</p>
<p class="p1"><span class="Apple-converted-space">      </span>});</p>
<p class="p2"><br></p>
<p class="p1"><span class="Apple-converted-space">      </span>totalDiv.innerText = "รวมทั้งหมด: " + total + " บาท";</p>
<p class="p1"><span class="Apple-converted-space">    </span>}</p>
<p class="p2"><br></p>
<p class="p1"><span class="Apple-converted-space">    </span>renderCart();</p>
<p class="p1"><span class="Apple-converted-space">  </span>&lt;/script&gt;</p>
<p class="p1">&lt;/body&gt;</p>
<p class="p1">&lt;/html&gt;</p>
</body>
</html>

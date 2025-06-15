# Spend someone's money
A fun game to spend someone's billions like Bill Gates
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Spend Someone's Money</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #f4f4f4;
      text-align: center;
    }
    .money {
      font-size: 30px;
      margin: 20px;
    }
    .item {
      background: white;
      border: 1px solid #ccc;
      border-radius: 10px;
      padding: 15px;
      margin: 10px auto;
      width: 300px;
    }
    .item img {
      width: 100px;
      height: 100px;
    }
    button {
      margin-top: 10px;
      padding: 10px 20px;
      font-weight: bold;
    }
  </style>
</head>
<body>

  <h1>Spend Someone's Money</h1>
  <div class="money" id="money">$100,000,000,000</div>

  <div id="items">
    <!-- Items will be added by JavaScript -->
  </div>

  <script>
    let money = 100000000000;

    const items = [
      { name: "Smartphone", price: 1000, img: "https://img.icons8.com/ios-filled/100/smartphone.png" },
      { name: "Car", price: 30000, img: "https://img.icons8.com/ios-filled/100/car--v1.png" },
      { name: "Jet", price: 50000000, img: "https://img.icons8.com/ios-filled/100/private-plane.png" }
    ];

    const itemContainer = document.getElementById('items');
    const moneyDisplay = document.getElementById('money');

    items.forEach(item => {
      item.quantity = 0;
      const div = document.createElement('div');
      div.className = "item";
      div.innerHTML = `
        <h2>${item.name}</h2>
        <img src="${item.img}" alt="${item.name}" />
        <p>Price: $${item.price.toLocaleString()}</p>
        <p>Owned: <span id="${item.name}-count">0</span></p>
        <button onclick="buy('${item.name}')">Buy</button>
      `;
      itemContainer.appendChild(div);
    });

    function buy(name) {
      const item = items.find(i => i.name === name);
      if (money >= item.price) {
        money -= item.price;
        item.quantity++;
        document.getElementById(`${item.name}-count`).innerText = item.quantity;
        moneyDisplay.innerText = `$${money.toLocaleString()}`;
      } else {
        alert("Not enough money!");
      }
    }
  </script>

</body>
</html>

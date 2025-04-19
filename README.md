<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Details | Fashion Store</title>
  <style>
    body {
      font-family: 'Segoe UI', sans-serif;
      margin: 0;
      background: #f4f4f4;
    }

    header {
      background-color: #1c1c1c;
      color: white;
      padding: 25px;
      text-align: center;
    }

    header h1 {
      margin: 0;
      font-size: 2.5em;
    }

    header p {
      margin: 5px 0 0;
      font-style: italic;
      color: #ddd;
    }

    .products {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      margin: 40px 20px;
    }

    .product {
      background: white;
      border: 1px solid #ccc;
      border-radius: 10px;
      width: 240px;
      margin: 15px;
      padding: 15px;
      text-align: center;
      box-shadow: 0 2px 5px rgba(0,0,0,0.1);
    }

    .product img {
      max-width: 100%;
      height: auto;
      border-radius: 6px;
    }

    .product h3 {
      margin: 10px 0;
      font-size: 1.2em;
    }

    .product button {
      background: #1c1c1c;
      color: white;
      padding: 10px 15px;
      border: none;
      border-radius: 4px;
      cursor: pointer;
    }

    .cart {
      padding: 25px;
      background: #fff;
      margin: 40px auto;
      border: 1px solid #ddd;
      border-radius: 6px;
      max-width: 600px;
    }

    footer {
      background-color: #222;
      color: white;
      padding: 30px;
      text-align: center;
    }

    footer h2 {
      margin-top: 0;
    }

    footer p {
      margin: 8px 0;
    }

    @media (max-width: 600px) {
      .products {
        flex-direction: column;
        align-items: center;
      }
    }
  </style>
</head>
<body>

  <header>
    <h1>Details</h1>
    <p>Where style meets conversation – because every detail speaks</p>
  </header>

  <div class="products" id="product-list">
    <!-- Product cards inserted here -->
  </div>

  <div class="cart" id="cart">
    <h2>Your Cart</h2>
    <ul id="cart-items"></ul>
  </div>

  <footer>
    <h2>About Details</h2>
    <p>Specializing in fashionable sling bags and men’s wear, <strong>Details</strong> blends trendy fashion with quality and class, made for bold self-expression.</p>
    <p><strong>Contact:</strong> Abhisekh3099@gmail.com</p>
    <p><strong>Location:</strong> New Delhi, India</p>
  </footer>

  <script>
    const products = [
      { id: 1, name: "Leather Sling Bag", price: 49.99, image: "https://via.placeholder.com/240x240?text=Sling+Bag" },
      { id: 2, name: "Canvas Crossbody Bag", price: 34.99, image: "https://via.placeholder.com/240x240?text=Crossbody+Bag" },
      { id: 3, name: "Men's Casual Shirt", price: 29.99, image: "https://via.placeholder.com/240x240?text=Men+Shirt" },
      { id: 4, name: "Men's Denim Jacket", price: 59.99, image: "https://via.placeholder.com/240x240?text=Denim+Jacket" },
    ];

    const cart = [];

    function renderProducts() {
      const productList = document.getElementById('product-list');
      products.forEach(product => {
        const div = document.createElement('div');
        div.className = 'product';
        div.innerHTML = `
          <img src="${product.image}" alt="${product.name}" />
          <h3>${product.name}</h3>
          <p>$${product.price.toFixed(2)}</p>
          <button onclick="addToCart(${product.id})">Add to Cart</button>
        `;
        productList.appendChild(div);
      });
    }

    function addToCart(productId) {
      const product = products.find(p => p.id === productId);
      cart.push(product);
      updateCart();
    }

    function updateCart() {
      const cartItems = document.getElementById('cart-items');
      cartItems.innerHTML = '';
      cart.forEach(item => {
        const li = document.createElement('li');
        li.textContent = `${item.name} - $${item.price.toFixed(2)}`;
        cartItems.appendChild(li);
      });
    }

    // Start it up
    renderProducts();
  </script>

</body>
</html>

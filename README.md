<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Naveen Mart - LocalStorage Example</title>
</head>
<body>
  <h2>Naveen Mart Product Entry</h2>
  <input type="text" id="productName" placeholder="Product Name">
  <input type="number" id="productPrice" placeholder="Price">
  <button onclick="saveProduct()">Save Product</button>

  <h3>Saved Products</h3>
  <ul id="productList"></ul>

  <script>
    // Save data to localStorage
    function saveProduct() {
      const name = document.getElementById('productName').value;
      const price = document.getElementById('productPrice').value;

      if (!name || !price) return alert("Please enter both fields");

      // Get existing products or initialize empty array
      const products = JSON.parse(localStorage.getItem('naveen_mart_products')) || [];
      products.push({ name, price });

      // Save back to LocalStorage
      localStorage.setItem('naveen_mart_products', JSON.stringify(products));

      document.getElementById('productName').value = '';
      document.getElementById('productPrice').value = '';
      displayProducts();
    }

    // Load and display data
    function displayProducts() {
      const products = JSON.parse(localStorage.getItem('naveen_mart_products')) || [];
      const list = document.getElementById('productList');
      list.innerHTML = '';
      products.forEach(p => {
        const li = document.createElement('li');
        li.textContent = `${p.name} - ₹${p.price}`;
        list.appendChild(li);
      });
    }

    // Display products on load
    displayProducts();
  </script>
</body>
</html>

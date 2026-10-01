<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">

  <title>Mon Catalogue</title>

  <style>
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      font-family: Arial, sans-serif;
    }

    body {
      background: #f5f5f5;
      color: #111;
    }

    header {
      background: #111;
      color: white;
      padding: 25px 15px;
      text-align: center;
    }

    header h1 {
      margin-bottom: 15px;
    }

    #search {
      width: 100%;
      max-width: 500px;
      padding: 14px;
      border: none;
      border-radius: 10px;
      font-size: 16px;
    }

    .categories {
      display: flex;
      gap: 10px;
      overflow-x: auto;
      padding: 15px;
      background: white;
    }

    .category {
      border: none;
      background: #eee;
      padding: 10px 15px;
      border-radius: 20px;
      cursor: pointer;
      white-space: nowrap;
    }

    .category:hover {
      background: #ddd;
    }

    .catalogue {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
      gap: 18px;
      padding: 20px;
      max-width: 1200px;
      margin: auto;
    }

    .product {
      background: white;
      border-radius: 15px;
      overflow: hidden;
      box-shadow: 0 3px 12px rgba(0,0,0,0.08);
    }

    .product img {
      width: 100%;
      height: 220px;
      object-fit: cover;
      display: block;
    }

    .product-info {
      padding: 15px;
    }

    .product h2 {
      font-size: 18px;
      margin-bottom: 8px;
    }

    .category-name {
      color: #777;
      font-size: 14px;
      margin-bottom: 8px;
    }

    .price {
      font-size: 18px;
      font-weight: bold;
      margin-bottom: 12px;
    }

    .button {
      display: block;
      text-align: center;
      background: #111;
      color: white;
      text-decoration: none;
      padding: 10px;
      border-radius: 8px;
    }

    .button:hover {
      background: #333;
    }

    footer {
      text-align: center;
      padding: 30px;
      margin-top: 20px;
      background: #111;
      color: white;
    }
  </style>
</head>

<body>

  <header>
    <h1>🛍️ MON CATALOGUE</h1>

    <input
      type="text"
      id="search"
      placeholder="🔎 Rechercher un produit..."
      onkeyup="searchProducts()"
    >
  </header>

  <div class="categories">
    <button class="category" onclick="filterProducts('Tous')">Tous</button>
    <button class="category" onclick="filterProducts('Maillots')">⚽ Maillots</button>
    <button class="category" onclick="filterProducts('Streetwear')">👕 Streetwear</button>
    <button class="category" onclick="filterProducts('Chaussures')">👟 Chaussures</button>
    <button class="category" onclick="filterProducts('Casquettes')">🧢 Casquettes</button>
  </div>

  <main class="catalogue" id="catalogue">

    <div class="product" data-category="Maillots">
      <img src="https://via.placeholder.com/500x600?text=Maillot+Gabon" alt="Maillot Gabon">

      <div class="product-info">
        <h2>Maillot du Gabon</h2>
        <p class="category-name">⚽ Maillots</p>
        <p class="price">15 000 FCFA</p>
        <a href="#" class="button">Voir le produit</a>
      </div>
    </div>

    <div class="product" data-category="Maillots">
      <img src="https://via.placeholder.com/500x600?text=Maillot+France" alt="Maillot France">

      <div class="product-info">
        <h2>Maillot France</h2>
        <p class="category-name">⚽ Maillots</p>
        <p class="price">15 000 FCFA</p>
        <a href="#" class="button">Voir le produit</a>
      </div>
    </div>

    <div class="product" data-category="Streetwear">
      <img src="https://via.placeholder.com/500x600?text=Hoodie+Nike" alt="Hoodie Nike">

      <div class="product-info">
        <h2>Hoodie Nike</h2>
        <p class="category-name">👕 Streetwear</p>
        <p class="price">20 000 FCFA</p>
        <a href="#" class="button">Voir le produit</a>
      </div>
    </div>

    <div class="product" data-category="Chaussures">
      <img src="https://via.placeholder.com/500x600?text=Chaussures" alt="Chaussures">

      <div class="product-info">
        <h2>Chaussures Nike</h2>
        <p class="category-name">👟 Chaussures</p>
        <p class="price">25 000 FCFA</p>
        <a href="#" class="button">Voir le produit</a>
      </div>
    </div>

    <div class="product" data-category="Casquettes">
      <img src="https://via.placeholder.com/500x600?text=Casquette" alt="Casquette">

      <div class="product-info">
        <h2>Casquette Nike</h2>
        <p class="category-name">🧢 Casquettes</p>
        <p class="price">8 000 FCFA</p>
        <a href="#" class="button">Voir le produit</a>
      </div>
    </div>

  </main>

  <footer>
    <p>© 2026 Mon Catalogue</p>
  </footer>

  <script>
    function searchProducts() {
      const search = document
        .getElementById("search")
        .value
        .toLowerCase();

      const products = document.querySelectorAll(".product");

      products.forEach(product => {
        const name = product
          .querySelector("h2")
          .textContent
          .toLowerCase();

        const category = product
          .dataset
          .category
          .toLowerCase();

        if (name.includes(search) || category.includes(search)) {
          product.style.display = "block";
        } else {
          product.style.display = "none";
        }
      });
    }

    function filterProducts(category) {
      const products = document.querySelectorAll(".product");

      products.forEach(product => {
        if (
          category === "Tous" ||
          product.dataset.category === category
        ) {
          product.style.display = "block";
        } else {
          product.style.display = "none";
        }
      });
    }
  </script>

</body>
</html># catalogue-
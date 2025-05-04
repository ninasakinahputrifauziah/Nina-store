<!DOCTYPE html><html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Pricelist by Nina Store</title>
  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;500;700&display=swap" rel="stylesheet" />
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: 'Poppins', sans-serif;
    }
    body {
      background: linear-gradient(135deg, #ffdce2, #ffeef4);
      padding: 20px;
      color: #333;
    }
    header {
      text-align: center;
      margin-bottom: 20px;
    }
    header h1 {
      font-size: 2rem;
      color: #d63384;
    }
    .contact {
      text-align: center;
      font-size: 0.9rem;
      color: #666;
    }
    .search-box {
      max-width: 400px;
      margin: 20px auto;
      display: flex;
    }
    .search-box input {
      width: 100%;
      padding: 10px;
      border: 1px solid #ccc;
      border-radius: 10px;
    }
    .price-category {
      margin-bottom: 15px;
      background: white;
      border-radius: 12px;
      box-shadow: 0 0 10px rgba(0,0,0,0.05);
      padding: 15px;
      transition: all 0.3s;
    }
    .price-category h2 {
      font-size: 1.2rem;
      color: #d63384;
      cursor: pointer;
    }
    .price-list {
      display: none;
      padding-left: 15px;
      margin-top: 10px;
      line-height: 1.5;
      font-size: 0.95rem;
    }
    .price-category.active .price-list {
      display: block;
    }
    footer {
      margin-top: 30px;
      text-align: center;
      font-size: 0.9rem;
      color: #666;
    }
  </style>
</head>
<body>
  <header>
    <h1>Pricelist by Nina Store</h1>
    <div class="contact">Contact: <a href="https://wa.me/6283141462986">wa.me/6283141462986</a> | Payment: Qris, Dana, Gopay</div>
  </header>  <div class="search-box">
    <input type="text" id="search" placeholder="Cari layanan...">
  </div>  <div id="pricelist"></div>  <footer>
    &copy; 2025 Nina Store. All rights reserved.
  </footer>  <script>
    const data = `AM PRO\nsharing\n1 tahun : 6k\nprivate\n1 tahun : 9k\n\nCANVA\n1 hari : 400p\n3 hari : 700p\n7 hari : Rp1.400\n1 bulan : Rp2.000\n3 bulan : rp6.000\n5 bulan : Rp7.000\n6 bulan : 9k\n1 tahun : 11k\nlifetime : 15k.\n\nSPOTIFY\nfamplan\n1 bulan : 19k\n2 bulan : 26k\nindplan\n3 bulan : 46k\n\n...`.split("\n\n"); // truncated for brevity

    const container = document.getElementById("pricelist");

    function renderList(filter = "") {
      container.innerHTML = "";
      data.forEach(item => {
        const lines = item.trim().split("\n");
        const title = lines[0];
        const prices = lines.slice(1).join("<br>");
        if (title.toLowerCase().includes(filter.toLowerCase()) || prices.toLowerCase().includes(filter.toLowerCase())) {
          const category = document.createElement("div");
          category.classList.add("price-category");
          category.innerHTML = `<h2>${title}</h2><div class="price-list">${prices}</div>`;
          category.querySelector("h2").addEventListener("click", () => {
            category.classList.toggle("active");
          });
          container.appendChild(category);
        }
      });
    }

    document.getElementById("search").addEventListener("input", (e) => {
      renderList(e.target.value);
    });

    renderList();
  </script></body>
</html>

# finds-bbdbuy-
Finds off BBDBUY 
<!DOCTYPE html>
<!DOCTYPE html>
<html lang="it">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>BBDSpread — Best BBDBuy Reps & QC Database</title>
    <style>
        :root {
            --bg-main: #0b0f17;
            --bg-card: #151c28;
            --accent-red: #ff3b30;
            --accent-glow: rgba(255, 59, 48, 0.15);
            --text-main: #ffffff;
            --text-muted: #8a99ad;
            --border: #232f45;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
        }

        body {
            background-color: var(--bg-main);
            color: var(--text-main);
            padding: 20px 12px;
            max-width: 1300px;
            margin: 0 auto;
        }

        header {
            text-align: center;
            margin-bottom: 30px;
        }

        .logo-title {
            font-size: 2.2rem;
            font-weight: 800;
            letter-spacing: -0.5px;
            margin-bottom: 8px;
        }

        .logo-title span {
            color: var(--accent-red);
        }

        .subtitle {
            color: var(--text-muted);
            font-size: 0.95rem;
            margin-bottom: 25px;
        }

        .search-box {
            position: relative;
            max-width: 600px;
            margin: 0 auto 20px auto;
        }

        .search-box input {
            width: 100%;
            padding: 14px 20px;
            border-radius: 30px;
            border: 1px solid var(--border);
            background-color: var(--bg-card);
            color: #fff;
            font-size: 0.95rem;
            outline: none;
            transition: all 0.2s ease;
        }

        .search-box input:focus {
            border-color: var(--accent-red);
            box-shadow: 0 0 15px var(--accent-glow);
        }

        .categories {
            display: flex;
            gap: 8px;
            overflow-x: auto;
            justify-content: flex-start;
            padding-bottom: 10px;
            margin-bottom: 30px;
            -webkit-overflow-scrolling: touch;
        }

        @media (min-width: 768px) {
            .categories {
                justify-content: center;
            }
        }

        .cat-btn {
            background-color: var(--bg-card);
            color: var(--text-muted);
            border: 1px solid var(--border);
            padding: 8px 18px;
            border-radius: 20px;
            white-space: nowrap;
            cursor: pointer;
            font-size: 0.85rem;
            font-weight: 600;
            transition: all 0.2s ease;
        }

        .cat-btn.active, .cat-btn:hover {
            background-color: var(--accent-red);
            color: #fff;
            border-color: var(--accent-red);
        }

        .product-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(160px, 1fr));
            gap: 15px;
        }

        @media (min-width: 600px) {
            .product-grid {
                grid-template-columns: repeat(auto-fill, minmax(220px, 1fr));
                gap: 20px;
            }
        }

        .card {
            background-color: var(--bg-card);
            border-radius: 16px;
            border: 1px solid var(--border);
            overflow: hidden;
            display: flex;
            flex-direction: column;
            position: relative;
            transition: transform 0.2s ease, border-color 0.2s ease;
        }

        .card:hover {
            transform: translateY(-4px);
            border-color: #3b4d6b;
        }

        .badge {
            position: absolute;
            top: 10px;
            left: 10px;
            background-color: rgba(11, 15, 23, 0.85);
            backdrop-filter: blur(4px);
            color: #fff;
            padding: 4px 10px;
            border-radius: 12px;
            font-size: 0.72rem;
            font-weight: 700;
            display: flex;
            align-items: center;
            gap: 4px;
            border: 1px solid rgba(255, 255, 255, 0.1);
            z-index: 2;
        }

        .badge-trending { color: #ff3b30; }
        .badge-popular { color: #ffcc00; }

        .img-container {
            width: 100%;
            aspect-ratio: 1 / 1;
            overflow: hidden;
            background-color: #000;
        }

        .img-container img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }

        .card-content {
            padding: 12px;
            display: flex;
            flex-direction: column;
            flex-grow: 1;
            justify-content: space-between;
        }

        .title {
            font-size: 0.9rem;
            font-weight: 600;
            line-height: 1.3;
            margin-bottom: 8px;
            color: #e2e8f0;
        }

        .price-row {
            display: flex;
            align-items: center;
            justify-content: space-between;
            margin-bottom: 12px;
        }

        .price {
            font-size: 1.1rem;
            font-weight: 800;
            color: #fff;
        }

        .btn-buy {
            display: block;
            width: 100%;
            text-align: center;
            background-color: var(--accent-red);
            color: #fff;
            text-decoration: none;
            padding: 10px 0;
            border-radius: 10px;
            font-weight: 700;
            font-size: 0.85rem;
            transition: opacity 0.2s;
        }

        .btn-buy:hover {
            opacity: 0.9;
        }
    </style>
</head>
<body>

    <header>
        <div class="logo-title">BBD<span>SPREAD</span></div>
        <p class="subtitle">Best BBDBuy Reps & QC Database</p>

        <div class="search-box">
            <input type="text" id="searchInput" placeholder="Search thousands of verified reps..." onkeyup="filterProducts()">
        </div>

        <div class="categories">
            <button class="cat-btn active" onclick="filterCategory('all', this)">All Products</button>
            <button class="cat-btn" onclick="filterCategory('scarpe', this)">Shoes</button>
            <button class="cat-btn" onclick="filterCategory('abbigliamento', this)">Apparel</button>
            <button class="cat-btn" onclick="filterCategory('accessori', this)">Accessories</button>
        </div>
    </header>

    <div class="product-grid" id="productGrid"></div>

    <script>
        const products = [
            // SCARPE
            {
                title: "Balenciaga Runner Sneaker",
                category: "scarpe",
                price: "$68.50",
                badge: "🔥 Trending",
                badgeClass: "badge-trending",
                image: "https://images.unsplash.com/photo-1542291026-7eec264c27ff?w=500",
                link: "https://www.bbdbuy.com/index/item/index.html?tp=weidian&url=https%3A%2F%2Fweidian.com%2Fitem.html%3FitemID%3D6838813930&partnercode=w8888"
            },
            {
                title: "Nike Dunk Low Black White (Panda)",
                category: "scarpe",
                price: "$28.00",
                badge: "★ Popular",
                badgeClass: "badge-popular",
                image: "https://images.unsplash.com/photo-1595950653106-6c9ebd614d3a?w=500",
                link: "https://www.bbdbuy.com/index/item/index.html?tp=weidian&url=https%3A%2F%2Fweidian.com%2Fitem.html%3FitemID%3D4415766195&partnercode=w8888"
            },
            {
                title: "Jordan 4 Black Cat",
                category: "scarpe",
                price: "$45.00",
                badge: "🔥 Trending",
                badgeClass: "badge-trending",
                image: "https://images.unsplash.com/photo-1552346154-21d32810aba3?w=500",
                link: "https://www.bbdbuy.com/index/item/index.html?tp=weidian&url=https%3A%2F%2Fweidian.com%2Fitem.html%3FitemID%3D6482046422&partnercode=w8888"
            },
            {
                title: "Balenciaga Track 1.0",
                category: "scarpe",
                price: "$62.00",
                badge: "",
                badgeClass: "",
                image: "https://images.unsplash.com/photo-1584735935682-2f2b69dff9d2?w=500",
                link: "https://www.bbdbuy.com/index/item/index.html?tp=weidian&url=https%3A%2F%2Fweidian.com%2Fitem.html%3FitemID%3D6838411234&partnercode=w8888"
            },

            // ABBIGLIAMENTO
            {
                title: "Chrome Hearts Zip Hoodie",
                category: "abbigliamento",
                price: "$38.00",
                badge: "🔥 Trending",
                badgeClass: "badge-trending",
                image: "https://images.unsplash.com/photo-1556905055-8f358a7a47b2?w=500",
                link: "https://www.bbdbuy.com/index/item/index.html?tp=weidian&url=https%3A%2F%2Fweidian.com%2Fitem.html%3FitemID%3D6543210987&partnercode=w8888"
            },
            {
                title: "Stussy Basic Hoodie",
                category: "abbigliamento",
                price: "$22.50",
                badge: "★ Popular",
                badgeClass: "badge-popular",
                image: "https://images.unsplash.com/photo-1509967419530-da38b4704bc6?w=500",
                link: "https://www.bbdbuy.com/index/item/index.html?tp=weidian&url=https%3A%2F%2Fweidian.com%2Fitem.html%3FitemID%3D5802341098&partnercode=w8888"
            },

            // ACCESSORI
            {
                title: "Cintura BB Simon Crystal",
                category: "accessori",
                price: "$19.00",
                badge: "★ Popular",
                badgeClass: "badge-popular",
                image: "https://images.unsplash.com/photo-1624222247344-550fb60583dc?w=500",
                link: "https://www.bbdbuy.com/index/item/index.html?tp=weidian&url=https%3A%2F%2Fweidian.com%2Fitem.html%3FitemID%3D6102938475&partnercode=w8888"
            }
        ];

        let selectedCategory = 'all';

        function renderProducts(items) {
            const grid = document.getElementById('productGrid');
            grid.innerHTML = '';

            if (items.length === 0) {
                grid.innerHTML = '<p style="grid-column: 1/-1; text-align: center; color: var(--text-muted); padding: 40px 0;">No products found.</p>';
                return;
            }

            items.forEach(product => {
                const card = document.createElement('div');
                card.className = 'card';
                card.innerHTML = `
                    ${product.badge ? `<div class="badge ${product.badgeClass}">${product.badge}</div>` : ''}
                    <div class="img-container">
                        <img src="${product.image}" alt="${product.title}" loading="lazy">
                    </div>
                    <div class="card-content">
                        <div class="title">${product.title}</div>
                        <div class="price-row">
                            <span class="price">${product.price}</span>
                        </div>
                        <a href="${product.link}" target="_blank" rel="noopener noreferrer" class="btn-buy">Buy on BBDBUY 🛒</a>
                    </div>
                `;
                grid.appendChild(card);
            });
        }

        function filterProducts() {
            const query = document.getElementById('searchInput').value.toLowerCase();
            const filtered = products.filter(p => {
                const matchesSearch = p.title.toLowerCase().includes(query);
                const matchesCategory = selectedCategory === 'all' || p.category === selectedCategory;
                return matchesSearch && matchesCategory;
            });
            renderProducts(filtered);
        }

        function filterCategory(category, btn) {
            selectedCategory = category;
            document.querySelectorAll('.cat-btn').forEach(b => b.classList.remove('active'));
            btn.classList.add('active');
            filterProducts();
        }

        renderProducts(products);
    </script>
</body>
</html>


⁠[https://repvault7.github.io/finds-bbdbuy-/](https://repvault7.github.io/finds-bbdbuy-/)



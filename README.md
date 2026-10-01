# finds-bbdbuy-
Finds off BBDBUY 
<!DOCTYPE html>
<html lang="it">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Finds BBDBUY</title>
    <style>
        :root {
            --bg-color: #0f172a;
            --card-bg: #1e293b;
            --accent-color: #ff4757;
            --text-color: #f8fafc;
            --text-muted: #94a3b8;
            --border-color: #334155;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
        }

        body {
            background-color: var(--bg-color);
            color: var(--text-color);
            padding: 20px 15px;
            max-width: 1200px;
            margin: 0 auto;
        }

        header {
            text-align: center;
            margin-bottom: 25px;
        }

        h1 {
            font-size: 2rem;
            margin-bottom: 8px;
        }

        h1 span {
            color: var(--accent-color);
        }

        p.subtitle {
            color: var(--text-muted);
            font-size: 0.95rem;
            margin-bottom: 20px;
        }

        .search-container {
            margin-bottom: 20px;
        }

        input[type="text"] {
            width: 100%;
            padding: 14px 18px;
            border-radius: 12px;
            border: 1px solid var(--border-color);
            background-color: var(--card-bg);
            color: #fff;
            font-size: 1rem;
            outline: none;
            box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1);
        }

        input[type="text"]:focus {
            border-color: var(--accent-color);
        }

        .categories {
            display: flex;
            gap: 10px;
            overflow-x: auto;
            padding-bottom: 10px;
            margin-bottom: 25px;
        }

        .category-btn {
            background-color: var(--card-bg);
            color: var(--text-color);
            border: 1px solid var(--border-color);
            padding: 8px 16px;
            border-radius: 20px;
            white-space: nowrap;
            cursor: pointer;
            font-size: 0.9rem;
            transition: all 0.2s ease;
        }

        .category-btn.active {
            background-color: var(--accent-color);
            border-color: var(--accent-color);
            font-weight: bold;
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

        .product-card {
            background-color: var(--card-bg);
            border-radius: 14px;
            overflow: hidden;
            border: 1px solid var(--border-color);
            display: flex;
            flex-direction: column;
        }

        .product-image {
            width: 100%;
            aspect-ratio: 1 / 1;
            object-fit: cover;
            background-color: #000;
        }

        .product-info {
            padding: 12px;
            display: flex;
            flex-direction: column;
            flex-grow: 1;
            justify-content: space-between;
        }

        .product-title {
            font-size: 0.95rem;
            font-weight: 600;
            margin-bottom: 12px;
            line-height: 1.3;
        }

        .buy-btn {
            display: block;
            width: 100%;
            text-align: center;
            background-color: var(--accent-color);
            color: white;
            text-decoration: none;
            padding: 10px 0;
            border-radius: 8px;
            font-weight: bold;
            font-size: 0.85rem;
        }

        .buy-btn:hover {
            opacity: 0.9;
        }
    </style>
</head>
<body>

    <header>
        <h1>🔥 I Migliori Finds <span>BBDBUY</span></h1>
        <p class="subtitle">Seleziona un articolo e aprilo direttamente su BBDBUY</p>
        
        <div class="search-container">
            <input type="text" id="searchInput" placeholder="Cerca prodotto (es. Balenciaga, Chrome Hearts)..." onkeyup="filterProducts()">
        </div>

        <div class="categories">
            <button class="category-btn active" onclick="filterCategory('all', this)">Tutti</button>
            <button class="category-btn" onclick="filterCategory('scarpe', this)">Scarpe</button>
            <button class="category-btn" onclick="filterCategory('abbigliamento', this)">Abbigliamento</button>
            <button class="category-btn" onclick="filterCategory('accessori', this)">Accessori</button>
        </div>
    </header>

    <div class="product-grid" id="productGrid"></div>

    <script>
        const products = [
            // SCARPE
            {
                title: "Balenciaga Runner Sneaker",
                category: "scarpe",
                image: "https://images.unsplash.com/photo-1542291026-7eec264c27ff?w=500",
                link: "https://www.bbdbuy.com/index/item/index.html?tp=weidian&url=https%3A%2F%2Fweidian.com%2Fitem.html%3FitemID%3D6838813930&partnercode=w8888"
            },
            {
                title: "Nike Dunk Low Black White (Panda)",
                category: "scarpe",
                image: "https://images.unsplash.com/photo-1595950653106-6c9ebd614d3a?w=500",
                link: "https://www.bbdbuy.com/index/item/index.html?tp=weidian&url=https%3A%2F%2Fweidian.com%2Fitem.html%3FitemID%3D4415766195&partnercode=w8888"
            },
            {
                title: "Jordan 4 Black Cat",
                category: "scarpe",
                image: "https://images.unsplash.com/photo-1552346154-21d32810aba3?w=500",
                link: "https://www.bbdbuy.com/index/item/index.html?tp=weidian&url=https%3A%2F%2Fweidian.com%2Fitem.html%3FitemID%3D6482046422&partnercode=w8888"
            },
            {
                title: "Balenciaga Track 1.0",
                category: "scarpe",
                image: "https://images.unsplash.com/photo-1584735935682-2f2b69dff9d2?w=500",
                link: "https://www.bbdbuy.com/index/item/index.html?tp=weidian&url=https%3A%2F%2Fweidian.com%2Fitem.html%3FitemID%3D6838411234&partnercode=w8888"
            },
            {
                title: "Alexander McQueen Oversized Sneaker",
                category: "scarpe",
                image: "https://images.unsplash.com/photo-1600185365483-26d7a4cc7519?w=500",
                link: "https://www.bbdbuy.com/index/item/index.html?tp=weidian&url=https%3A%2F%2Fweidian.com%2Fitem.html%3FitemID%3D4421048321&partnercode=w8888"
            },

            // ABBIGLIAMENTO
            {
                title: "Chrome Hearts Zip Hoodie",
                category: "abbigliamento",
                image: "https://images.unsplash.com/photo-1556905055-8f358a7a47b2?w=500",
                link: "https://www.bbdbuy.com/index/item/index.html?tp=weidian&url=https%3A%2F%2Fweidian.com%2Fitem.html%3FitemID%3D6543210987&partnercode=w8888"
            },
            {
                title: "Stussy Basic Hoodie",
                category: "abbigliamento",
                image: "https://images.unsplash.com/photo-1509967419530-da38b4704bc6?w=500",
                link: "https://www.bbdbuy.com/index/item/index.html?tp=weidian&url=https%3A%2F%2Fweidian.com%2Fitem.html%3FitemID%3D5802341098&partnercode=w8888"
            },
            {
                title: "Trapstar Irongate Arch Hoodie Set",
                category: "abbigliamento",
                image: "https://images.unsplash.com/photo-1620799140408-edc6dcb6d633?w=500",
                link: "https://www.bbdbuy.com/index/item/index.html?tp=weidian&url=https%3A%2F%2Fweidian.com%2Fitem.html%3FitemID%3D6501239874&partnercode=w8888"
            },
            {
                title: "Denim Tears Cotton Wreath Hoodie",
                category: "abbigliamento",
                image: "https://images.unsplash.com/photo-1578587018452-892bacefd3f2?w=500",
                link: "https://www.bbdbuy.com/index/item/index.html?tp=weidian&url=https%3A%2F%2Fweidian.com%2Fitem.html%3FitemID%3D6809876543&partnercode=w8888"
            },
            {
                title: "Gallery Dept. Oversized T-Shirt",
                category: "abbigliamento",
                image: "https://images.unsplash.com/photo-1521572267360-ee0c2909d518?w=500",
                link: "https://www.bbdbuy.com/index/item/index.html?tp=weidian&url=https%3A%2F%2Fweidian.com%2Fitem.html%3FitemID%3D6301298765&partnercode=w8888"
            },

            // ACCESSORI
            {
                title: "Cintura BB Simon Crystal",
                category: "accessori",
                image: "https://images.unsplash.com/photo-1624222247344-550fb60583dc?w=500",
                link: "https://www.bbdbuy.com/index/item/index.html?tp=weidian&url=https%3A%2F%2Fweidian.com%2Fitem.html%3FitemID%3D6102938475&partnercode=w8888"
            },
            {
                title: "Cappello Chrome Hearts Trucker",
                category: "accessori",
                image: "https://images.unsplash.com/photo-1588850561407-ed78c282e89b?w=500",
                link: "https://www.bbdbuy.com/index/item/index.html?tp=weidian&url=https%3A%2F%2Fweidian.com%2Fitem.html%3FitemID%3D5901284756&partnercode=w8888"
            }
        ];

        let selectedCategory = 'all';

        function renderProducts(items) {
            const grid = document.getElementById('productGrid');
            grid.innerHTML = '';

            if (items.length === 0) {
                grid.innerHTML = '<p style="grid-column: 1/-1; text-align: center; color: var(--text-muted); padding: 40px 0;">Nessun prodotto trovato.</p>';
                return;
            }

            items.forEach(product => {
                const card = document.createElement('div');
                card.className = 'product-card';
                card.innerHTML = `
                    <img src="${product.image}" alt="${product.title}" class="product-image" loading="lazy">
                    <div class="product-info">
                        <div class="product-title">${product.title}</div>
                        <a href="${product.link}" target="_blank" rel="noopener noreferrer" class="buy-btn">Apri su BBDBUY 🛒</a>
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
            document.querySelectorAll('.category-btn').forEach(b => b.classList.remove('active'));
            btn.classList.add('active');
            filterProducts();
        }

        renderProducts(products);
    </script>
</body>
</html>


⁠[https://repvault7.github.io/finds-bbdbuy-/](https://repvault7.github.io/finds-bbdbuy-/)



# finds-bbdbuy-
Finds off BBDBUY 
<!DOCTYPE html>
<html lang="it">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Catalogo Reps BBDBUY</title>
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
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background-color: var(--bg-color);
            color: var(--text-color);
            padding: 20px;
        }

        header {
            text-align: center;
            margin-bottom: 30px;
        }

        header h1 {
            font-size: 2.2rem;
            margin-bottom: 10px;
        }

        header h1 span {
            color: var(--accent-color);
        }

        .controls {
            max-width: 1100px;
            margin: 0 auto 30px auto;
            display: flex;
            flex-wrap: wrap;
            gap: 15px;
            justify-content: space-between;
        }

        .search-bar {
            flex: 1;
            min-width: 250px;
            padding: 12px 20px;
            border-radius: 8px;
            border: 1px solid var(--border-color);
            background-color: var(--card-bg);
            color: var(--text-color);
            font-size: 1rem;
        }

        .category-buttons {
            display: flex;
            gap: 10px;
            flex-wrap: wrap;
        }

        .btn-filter {
            padding: 10px 18px;
            border-radius: 8px;
            border: 1px solid var(--border-color);
            background-color: var(--card-bg);
            color: var(--text-color);
            cursor: pointer;
            transition: 0.2s;
        }

        .btn-filter.active, .btn-filter:hover {
            background-color: var(--accent-color);
            border-color: var(--accent-color);
        }

        .grid {
            max-width: 1100px;
            margin: 0 auto;
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(260px, 1fr));
            gap: 25px;
        }

        .card {
            background-color: var(--card-bg);
            border-radius: 12px;
            overflow: hidden;
            border: 1px solid var(--border-color);
            display: flex;
            flex-direction: column;
            transition: transform 0.2s;
        }

        .card:hover {
            transform: translateY(-5px);
        }

        .card img {
            width: 100%;
            height: 220px;
            object-fit: cover;
        }

        .card-content {
            padding: 15px;
            display: flex;
            flex-direction: column;
            flex-grow: 1;
        }

        .card-title {
            font-size: 1.1rem;
            margin-bottom: 8px;
        }

        .card-meta {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 15px;
        }

        .price {
            font-size: 1.2rem;
            font-weight: bold;
            color: #2ed573;
        }

        .tag {
            font-size: 0.8rem;
            background-color: var(--border-color);
            padding: 4px 8px;
            border-radius: 4px;
            color: var(--text-muted);
        }

        .btn-buy {
            display: block;
            text-align: center;
            background-color: var(--accent-color);
            color: white;
            text-decoration: none;
            padding: 10px;
            border-radius: 6px;
            font-weight: bold;
            margin-top: auto;
            transition: opacity 0.2s;
        }

        .btn-buy:hover {
            opacity: 0.9;
        }
    </style>
</head>
<body>

    <header>
        <h1>🔥 I Migliori Finds <span>BBDBUY</span></h1>
        <p>Seleziona un articolo e aprilo direttamente su BBDBUY</p>
    </header>

    <div class="controls">
        <input type="text" id="searchInput" class="search-bar" placeholder="Cerca prodotto (es. Balenciaga, Chrome Hearts, LV)...">
        <div class="category-buttons">
            <button class="btn-filter active" onclick="filterCategory('tutti')">Tutti</button>
            <button class="btn-filter" onclick="filterCategory('scarpe')">Scarpe</button>
            <button class="btn-filter" onclick="filterCategory('abbigliamento')">Abbigliamento</button>
            <button class="btn-filter" onclick="filterCategory('accessori')">Accessori</button>
        </div>
    </div>

    <div class="grid" id="productGrid"></div>

    <script>
        const products = [
            // SCARPE
            {
                id: 1,
                title: "Balenciaga Runner Sneakers (Blu / Argento)",
                category: "scarpe",
                price: "Best Quality",
                tag: "Sneakers",
                image: "https://images.unsplash.com/photo-1542291026-7eec264c27ff?w=500&q=80",
                bbdbuyLink: "https://www.bbdbuy.com/product?url=https%3A%2F%2Fshop1850859027.v.weidian.com%2Fitem.html%3FitemID%3D7805764533"
            },
            {
                id: 2,
                title: "Balenciaga Runner Sneakers (Rosa / Argento)",
                category: "scarpe",
                price: "Best Quality",
                tag: "Sneakers",
                image: "https://images.unsplash.com/photo-1542291026-7eec264c27ff?w=500&q=80",
                bbdbuyLink: "https://www.bbdbuy.com/product?url=https%3A%2F%2Fshop1816463806.v.weidian.com%2Fitem.html%3FitemID%3D7805643381"
            },
            {
                id: 3,
                title: "LV Trainer Sneaker Suede Strass (Nere)",
                category: "scarpe",
                price: "Best Quality",
                tag: "Sneakers",
                image: "https://images.unsplash.com/photo-1542291026-7eec264c27ff?w=500&q=80",
                bbdbuyLink: "https://www.bbdbuy.com/product?url=https%3A%2F%2Fk.youshop10.com%2FyS-MtIXA"
            },
            {
                id: 4,
                title: "LV Trainer Sneaker Monogram (Nero / Bianco)",
                category: "scarpe",
                price: "Best Quality",
                tag: "Sneakers",
                image: "https://images.unsplash.com/photo-1542291026-7eec264c27ff?w=500&q=80",
                bbdbuyLink: "https://www.bbdbuy.com/product?url=https%3A%2F%2Fk.youshop10.com%2Fe-RoESDJ"
            },

            // ABBIGLIAMENTO - CHROME HEARTS
            {
                id: 5,
                title: "Felpa Chrome Hearts Double Cross (Blu)",
                category: "abbigliamento",
                price: "Best Quality",
                tag: "Hoodie",
                image: "https://images.unsplash.com/photo-1556905055-8f358a7a47b2?w=500&q=80",
                bbdbuyLink: "https://www.bbdbuy.com/product?url=https%3A%2F%2Fweidian.com%2Fitem.html%3FitemID%3D7772497216"
            },
            {
                id: 6,
                title: "Felpa Chrome Hearts Multi-Cross Colorate",
                category: "abbigliamento",
                price: "Best Quality",
                tag: "Hoodie",
                image: "https://images.unsplash.com/photo-1556905055-8f358a7a47b2?w=500&q=80",
                bbdbuyLink: "https://www.bbdbuy.com/product?url=https%3A%2F%2Fweidian.com%2Fitem.html%3FitemID%3D7717207264"
            },
            {
                id: 7,
                title: "Felpa Girocollo Chrome Hearts Los Angeles",
                category: "abbigliamento",
                price: "Best Quality",
                tag: "Crewneck",
                image: "https://images.unsplash.com/photo-1556905055-8f358a7a47b2?w=500&q=80",
                bbdbuyLink: "https://www.bbdbuy.com/product?url=https%3A%2F%2Fweidian.com%2Fitem.html%3FitemID%3D7770674151"
            },
            {
                id: 8,
                title: "Felpa Zip Chrome Hearts Pink Horseshoe (Bianca)",
                category: "abbigliamento",
                price: "Best Quality",
                tag: "Zip Hoodie",
                image: "https://images.unsplash.com/photo-1556905055-8f358a7a47b2?w=500&q=80",
                bbdbuyLink: "https://www.bbdbuy.com/product?url=https%3A%2F%2Fweidian.com%2Fitem.html%3FitemID%3D7838027443"
            },
            {
                id: 9,
                title: "Felpa Zip Chrome Hearts Horseshoe (Nera)",
                category: "abbigliamento",
                price: "Best Quality",
                tag: "Zip Hoodie",
                image: "https://images.unsplash.com/photo-1556905055-8f358a7a47b2?w=500&q=80",
                bbdbuyLink: "https://www.bbdbuy.com/product?url=https%3A%2F%2Fweidian.com%2Fitem.html%3FitemID%3D7860678752"
            },
            {
                id: 10,
                title: "T-Shirt Chrome Hearts Paint Splash",
                category: "abbigliamento",
                price: "Best Quality",
                tag: "Tee",
                image: "https://images.unsplash.com/photo-1521572267360-ee0c2909d518?w=500&q=80",
                bbdbuyLink: "https://www.bbdbuy.com/product?url=https%3A%2F%2Fweidian.com%2Fitem.html%3FitemID%3D7787301906"
            },
            {
                id: 11,
                title: "Jeans Chrome Hearts Carpenter Patchwork",
                category: "abbigliamento",
                price: "Best Quality",
                tag: "Jeans",
                image: "https://images.unsplash.com/photo-1541099649105-f69ad21f3246?w=500&q=80",
                bbdbuyLink: "https://www.bbdbuy.com/product?url=https%3A%2F%2Fweidian.com%2Fitem.html%3FitemID%3D7782625592"
            },
            {
                id: 12,
                title: "Jeans Chrome Hearts Flare Split Hem",
                category: "abbigliamento",
                price: "Best Quality",
                tag: "Jeans",
                image: "https://images.unsplash.com/photo-1541099649105-f69ad21f3246?w=500&q=80",
                bbdbuyLink: "https://www.bbdbuy.com/product?url=https%3A%2F%2Fweidian.com%2Fitem.html%3FitemID%3D7717215032"
            },

            // ABBIGLIAMENTO - ALTRI BRAND E KNITWEAR
            {
                id: 13,
                title: "Sp5der Hoodie Web Logo (Nera)",
                category: "abbigliamento",
                price: "Best Quality",
                tag: "Hoodie",
                image: "https://images.unsplash.com/photo-1556905055-8f358a7a47b2?w=500&q=80",
                bbdbuyLink: "https://www.bbdbuy.com/product?url=https%3A%2F%2Fweidian.com%2Fitem.html%3FitemID%3D7722372058"
            },
            {
                id: 14,
                title: "Maglione Knit Burberry Knight Logo",
                category: "abbigliamento",
                price: "Best Quality",
                tag: "Knitwear",
                image: "https://images.unsplash.com/photo-1620799140408-edc6dcb6d633?w=500&q=80",
                bbdbuyLink: "https://www.bbdbuy.com/product?url=https%3A%2F%2Fweidian.com%2Fitem.html%3FitemID%3D7861932714"
            },
            {
                id: 15,
                title: "Maglione Knit Saint Laurent Fluffy",
                category: "abbigliamento",
                price: "Best Quality",
                tag: "Knitwear",
                image: "https://images.unsplash.com/photo-1620799140408-edc6dcb6d633?w=500&q=80",
                bbdbuyLink: "https://www.bbdbuy.com/product?url=https%3A%2F%2Fweidian.com%2Fitem.html%3FitemID%3D7773668060"
            },
            {
                id: 16,
                title: "Maglione Knit Burberry Check Pattern",
                category: "abbigliamento",
                price: "Best Quality",
                tag: "Knitwear",
                image: "https://images.unsplash.com/photo-1620799140408-edc6dcb6d633?w=500&q=80",
                bbdbuyLink: "https://www.bbdbuy.com/product?url=https%3A%2F%2Fweidian.com%2Fitem.html%3FitemID%3D7781358336"
            },
            {
                id: 17,
                title: "Pantaloni Tuta Essentials FOG",
                category: "abbigliamento",
                price: "Best Quality",
                tag: "Pants",
                image: "https://images.unsplash.com/photo-1556905055-8f358a7a47b2?w=500&q=80",
                bbdbuyLink: "https://www.bbdbuy.com/product?url=https%3A%2F%2Fweidian.com%2Fitem.html%3FitemID%3D7843565245"
            },
            {
                id: 18,
                title: "Berretto in Maglia Louis Vuitton LV",
                category: "accessori",
                price: "Best Quality",
                tag: "Beanie",
                image: "https://images.unsplash.com/photo-1576871337632-b9aef4c17ab9?w=500&q=80",
                bbdbuyLink: "https://www.bbdbuy.com/product?url=https%3A%2F%2Fweidian.com%2Fitem.html%3FitemID%3D7843027691"
            }
        ];

        let currentCategory = 'tutti';

        function displayProducts() {
            const grid = document.getElementById('productGrid');
            const searchVal = document.getElementById('searchInput').value.toLowerCase();
            grid.innerHTML = '';

            const filtered = products.filter(p => {
                const matchesCat = currentCategory === 'tutti' || p.category === currentCategory;
                const matchesSearch = p.title.toLowerCase().includes(searchVal);
                return matchesCat && matchesSearch;
            });

            filtered.forEach(p => {
                grid.innerHTML += `
                    <div class="card">
                        <img src="${p.image}" alt="${p.title}">
                        <div class="card-content">
                            <h3 class="card-title">${p.title}</h3>
                            <div class="card-meta">
                                <span class="price">${p.price}</span>
                                <span class="tag">${p.tag}</span>
                            </div>
                            <a href="${p.bbdbuyLink}" target="_blank" class="btn-buy">Apri su BBDBUY 🛒</a>
                        </div>
                    </div>
                `;
            });
        }

        function filterCategory(cat) {
            currentCategory = cat;
            document.querySelectorAll('.btn-filter').forEach(btn => btn.classList.remove('active'));
            event.target.classList.add('active');
            displayProducts();
        }

        document.getElementById('searchInput').addEventListener('input', displayProducts);

        displayProducts();
    </script>
</body>
</html>

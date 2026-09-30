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
        <input type="text" id="searchInput" class="search-bar" placeholder="Cerca prodotto (es. Jordan, Felpa, Nike)...">
        <div class="category-buttons">
            <button class="btn-filter active" onclick="filterCategory('tutti')">Tutti</button>
            <button class="btn-filter" onclick="filterCategory('scarpe')">Scarpe</button>
            <button class="btn-filter" onclick="filterCategory('abbigliamento')">Abbigliamento</button>
            <button class="btn-filter" onclick="filterCategory('accessori')">Accessori</button>
        </div>
    </div>

    <div class="grid" id="productGrid"></div>

    <script>
        // LISTA DEI PRODOTTI: Modifica o aggiungi i tuoi prodotti qui sotto
        const products = [
            {
                id: 1,
                title: "Air Jordan 1 Low x Travis Scott",
                category: "scarpe",
                price: "¥ 360",
                tag: "Batch PK 4.0",
                image: "https://images.unsplash.com/photo-1552346154-21d32810aba3?w=500&q=80",
                bbdbuyLink: "https://www.bbdbuy.com"
            },
            {
                id: 2,
                title: "Felpa Trapstar Decoded Nera",
                category: "abbigliamento",
                price: "¥ 220",
                tag: "Qualità Top",
                image: "https://images.unsplash.com/photo-1556905055-8f358a7a47b2?w=500&q=80",
                bbdbuyLink: "https://www.bbdbuy.com"
            },
            {
                id: 3,
                title: "Cintura Nike x Stussy",
                category: "accessori",
                price: "¥ 45",
                tag: "1:1 Best",
                image: "https://images.unsplash.com/photo-1624222247344-550fb60583dc?w=500&q=80",
                bbdbuyLink: "https://www.bbdbuy.com"
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

        // Caricamento iniziale
        displayProducts();
    </script>
</body>
</html>

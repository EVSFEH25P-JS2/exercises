# Dela upp en stor component (Utmaning)

## Mål

Öva på att identifiera och bryta ut delar av en stor component till mindre, fokuserade components.

## Förkunskaper

- [Component patterns och komposition](../../documents/09-component-patterns.md)
- [Projektstruktur och arkitektur](../../documents/10-projektstruktur.md)

## Instruktioner

Följande component gör för mycket. Din uppgift är att dela upp den.

1. Kopiera in koden nedan i en fil:

```jsx
import { useState, useEffect } from "react";

function ProductPage() {
  const [products, setProducts] = useState([]);
  const [loading, setLoading] = useState(true);
  const [search, setSearch] = useState("");
  const [cart, setCart] = useState([]);

  useEffect(() => {
    fetch("https://fakestoreapi.com/products?limit=10")
      .then((res) => res.json())
      .then((data) => setProducts(data))
      .finally(() => setLoading(false));
  }, []);

  const filtered = products.filter((p) =>
    p.title.toLowerCase().includes(search.toLowerCase())
  );

  const total = cart.reduce((sum, item) => sum + item.price, 0);

  if (loading) return <p>Laddar...</p>;

  return (
    <div>
      <h1>Produkter</h1>
      <input
        value={search}
        onChange={(e) => setSearch(e.target.value)}
        placeholder="Sök produkt..."
      />
      <div>
        {filtered.map((product) => (
          <div key={product.id}>
            <h3>{product.title}</h3>
            <p>{product.price} kr</p>
            <button onClick={() => setCart([...cart, product])}>
              Lägg i varukorg
            </button>
          </div>
        ))}
      </div>
      <div>
        <h2>Varukorg ({cart.length})</h2>
        {cart.map((item, i) => (
          <p key={i}>{item.title} — {item.price} kr</p>
        ))}
        <p><strong>Totalt: {total.toFixed(2)} kr</strong></p>
      </div>
    </div>
  );
}
```

2. Identifiera vilka delar som kan brytas ut. Förslag:
   - `SearchBar` — input-fältet
   - `ProductCard` — ett enskilt produktkort
   - `ProductList` — listan av produktkort
   - `CartSummary` — varukorgen
3. Bryt ut varje del till en egen component i en egen fil.
4. Bestäm vilken component som äger vilken state. Skicka data och callbacks via props.
5. Organisera filerna i en vettig mappstruktur.

## Förväntat resultat

Samma funktionalitet som innan, men uppdelad i 4-5 components med tydliga ansvar. Varje component-fil är kort och lätt att förstå. Mappstrukturen är logisk.

## Tips

<details>
<summary>Ledtråd 1</summary>

`ProductPage` behåller state och logik (container). De utbrutna components tar emot data och callbacks via props (presentational).

</details>

<details>
<summary>Ledtråd 2</summary>

```
pages/
└── ProductPage/
    ├── ProductPage.jsx     # Container — äger state
    ├── SearchBar.jsx        # Presentational
    ├── ProductCard.jsx      # Presentational
    ├── ProductList.jsx      # Presentational
    └── CartSummary.jsx      # Presentational
```

</details>

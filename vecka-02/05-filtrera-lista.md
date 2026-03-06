# Filtrera och conditional rendering (Utmaning)

## Mål

Öva på att kombinera `.filter()`, `.map()`, state och conditional rendering.

## Förkunskaper

- [State och events](../../documents/03-state-events.md)
- [Listor och conditional rendering](../../documents/04-listor-conditional-rendering.md)
- [Rendera en lista](04-rendera-lista.md)

## Instruktioner

1. Skapa en component `ProductFilter`.
2. Skapa en array med minst sex produkter (objekt med `id`, `name`, `price`, `category`). Använd minst tre olika kategorier.
3. Rendera alla produkter som kort med `.map()`.
4. Lägg till knappar för varje kategori samt en "Alla"-knapp.
5. Skapa en state-variabel `activeCategory` med startvärde `"all"`.
6. Filtrera produkterna baserat på `activeCategory` innan du renderar dem. Om `"all"` är valt, visa alla.
7. Ge den aktiva knappen en CSS-klass `"active"` så användaren ser vilken kategori som är vald.
8. Om den filtrerade listan är tom, visa `<p>Inga produkter i denna kategori.</p>` istället.

## Förväntat resultat

En produktlista med kategoriknappar. Klick på en kategori filtrerar listan. Den aktiva knappen är markerad. Om inga produkter matchar visas ett meddelande.

## Tips

<details>
<summary>Ledtråd 1</summary>

Filtrera innan du mappar:

```jsx
const filtered = activeCategory === "all"
  ? products
  : products.filter((p) => p.category === activeCategory);
```

</details>

<details>
<summary>Ledtråd 2</summary>

Villkorlig CSS-klass på knappen:

```jsx
<button
  className={activeCategory === cat ? "active" : ""}
  onClick={() => setActiveCategory(cat)}
>
```

</details>

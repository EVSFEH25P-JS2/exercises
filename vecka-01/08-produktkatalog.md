# Produktkatalog (Extra)

## Mål

Kombinera alla koncept från vecka 1 — JSX, components, props, children och komposition — i ett större projekt.

## Förkunskaper

- [Introduktion till React och JSX](../../documents/01-introduktion-react-jsx.md)
- [Components och props](../../documents/02-components-props.md)
- [Component-sammansättning](07-component-sammansattning.md)

## Instruktioner

1. Skapa följande components i separata filer under `src/components/`:
   - `Header` — appens namn och en kort beskrivning
   - `ProductCard` — visar namn, pris, kategori och beskrivning för en produkt
   - `ProductList` — tar emot en array `products` som prop och renderar en `ProductCard` för varje produkt
   - `InfoBox` — en wrapper-component som använder `children` för att visa valfritt innehåll i en stilad box
   - `Footer` — copyright-text
2. Skapa en array med minst 6 produkter i `App.jsx`. Varje produkt ska vara ett objekt med `name`, `price`, `category` och `description`.
3. Skicka arrayen som prop till `ProductList`.
4. Ge `ProductCard` ett default-värde för `category`: `"Övrigt"`. Testa genom att utelämna `category` på en produkt i arrayen.
5. Använd `InfoBox` för att visa en kampanjtext någonstans på sidan (t.ex. "Fri frakt över 500 kr!").
6. Sätt ihop allt i `App.jsx`: `Header`, `InfoBox`, `ProductList`, `Footer`.

## Förväntat resultat

En komplett sida med header, kampanjruta, sex produktkort med information, och en footer. Alla delar är egna components i separata filer.

## Tips

<details>
<summary>Ledtråd 1</summary>

Börja med `App.jsx` och bygg en component i taget. Hårdkoda data först och extrahera till props efteråt.

</details>

<details>
<summary>Ledtråd 2</summary>

`ProductList` renderar korten med `.map()` — om du redan kikat på det. Annars kan du hårdkoda sex stycken `<ProductCard />` för nu.

```jsx
function ProductList({ products }) {
  return (
    <div>
      {products.map((product, index) => (
        <ProductCard
          key={index}
          name={product.name}
          price={product.price}
          category={product.category}
          description={product.description}
        />
      ))}
    </div>
  );
}
```

</details>

# Props (Grund)

## Mål

Öva på att skicka data till components via props och destrukturera dem.

## Förkunskaper

- [Components och props](../../documents/02-components-props.md)
- [Din första component](04-din-forsta-component.md)

## Instruktioner

1. Skapa en component `ProductCard` i en ny fil `src/ProductCard.jsx`.
2. Componenten ska ta emot props: `name`, `price` och `category`.
3. Destrukturera props direkt i funktionsparametern.
4. Rendera all information i en `<div>`:
   - `name` i en `<h3>`
   - `price` i en `<p>` med "kr" efter
   - `category` i en `<span>`
5. Importera `ProductCard` i `App.jsx` och rendera den med minst tre olika produkter.
6. Ge `category` ett default-värde: `"Övrigt"`. Rendera en `ProductCard` utan `category`-prop och kontrollera att default-värdet visas.

## Förväntat resultat

Tre (eller fler) produktkort med olika namn, priser och kategorier. Det kort som inte fick en `category`-prop visar "Övrigt".

## Tips

<details>
<summary>Ledtråd 1</summary>

Default values sätts i destructuring: `function ProductCard({ name, price, category = "Övrigt" })`

</details>

<details>
<summary>Ledtråd 2</summary>

Strängar skickas med citattecken: `name="Tangentbord"`. Tal skickas med klammerparenteser: `price={899}`.

</details>

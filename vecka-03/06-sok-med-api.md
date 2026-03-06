# Sök med API (Extra)

## Mål

Kombinera formulärinput, useEffect med dependency och API-anrop för att bygga en sökfunktion.

## Förkunskaper

- [useEffect och data fetching](../../documents/05-useeffect-data-fetching.md)
- [Formulär och controlled components](../../documents/06-formular-controlled-components.md)

## Instruktioner

1. Skapa en component `CountrySearch`.
2. Skapa state för `query` (tom sträng), `countries` (tom array), `loading` och `error`.
3. Lägg till ett input-fält kopplat till `query`.
4. Lägg till en `useEffect` med `[query]` i dependency array.
5. Om `query` är kortare än 2 tecken, sätt `countries` till tom array och avbryt.
6. Hämta data från: `https://restcountries.com/v3.1/name/{query}`
7. Rendera varje land med namn och flagga (emoji finns i `flag`-fältet).
8. Hantera loading och error.
9. Om inga länder hittas (API ger 404), visa "Inga länder hittade."

## Förväntat resultat

Skriv i sökfältet och resultat uppdateras automatiskt. Kort sökterm visar ingenting. Ogiltig sökterm visar ett meddelande. Loading visas under hämtning.

## Tips

<details>
<summary>Ledtråd 1</summary>

API:et returnerar en array av länder. Varje land har `name.common` (namn) och `flag` (emoji). Vid 404 kastar API:et ett fel.

```jsx
const response = await fetch(`https://restcountries.com/v3.1/name/${query}`);
if (!response.ok) throw new Error("Inga länder hittade");
const data = await response.json();
```

</details>

# useEffect — introduktion (Grund)

## Mål

Förstå hur `useEffect` fungerar och hur dependency array styr när effecten körs.

## Förkunskaper

- [useEffect och data fetching](../../documents/05-useeffect-data-fetching.md)

## Instruktioner

1. Skapa en component `EffectDemo`.
2. Lägg till en `useEffect` utan dependency array som loggar "Effect kördes!" till konsolen.
3. Lägg till en state-variabel `count` med en knapp som ökar den. Klicka på knappen och notera hur ofta effecten loggar.
4. Lägg nu till en tom dependency array `[]`. Klicka på knappen igen — effecten ska bara logga en gång (vid mount).
5. Ändra dependency array till `[count]`. Effecten ska nu logga varje gång `count` ändras.
6. Lägg till en andra state-variabel `text` med ett input-fält. Med `[count]` i dependency array, skriv i fältet och kontrollera att effecten *inte* körs — bara vid count-ändringar.

## Förväntat resultat

Du ska kunna se skillnaden i konsolen mellan ingen array (körs vid varje render), tom array (körs en gång), och array med värden (körs vid ändring).

## Tips

<details>
<summary>Ledtråd 1</summary>

```jsx
// Körs vid varje render
useEffect(() => { console.log("Alltid"); });

// Körs en gång
useEffect(() => { console.log("Mount"); }, []);

// Körs när count ändras
useEffect(() => { console.log("Count:", count); }, [count]);
```

</details>

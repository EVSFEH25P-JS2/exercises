# useState — räknare (Grund)

## Mål

Öva på att använda `useState` för att hantera data som ändras vid klick.

## Förkunskaper

- [State och events](../../documents/03-state-events.md)

## Instruktioner

1. Skapa en ny component `Counter`.
2. Importera `useState` från React.
3. Skapa en state-variabel `count` med startvärde `0`.
4. Rendera `count` i en `<p>`.
5. Lägg till tre knappar:
   - "+" som ökar `count` med 1
   - "−" som minskar `count` med 1
   - "Nollställ" som sätter `count` till 0
6. Rendera `Counter` i `App.jsx`.
7. Rendera två `Counter`-components bredvid varandra. Klicka på den ena och kontrollera att den andra inte påverkas.

## Förväntat resultat

En räknare som kan ökas, minskas och nollställas. Två räknare på sidan som fungerar oberoende av varandra.

## Tips

<details>
<summary>Ledtråd 1</summary>

```jsx
const [count, setCount] = useState(0);
```

Varje setter-anrop triggar en re-render med det nya värdet.

</details>

# Kortspel (Extra)

## Mål

Kombinera state, events, conditional rendering och listor i en interaktiv liten app.

## Förkunskaper

- [State och events](../../documents/03-state-events.md)
- [Listor och conditional rendering](../../documents/04-listor-conditional-rendering.md)
- [Todo-lista](06-todo-lista.md)

## Instruktioner

Bygg ett enkelt kortspel där spelaren drar kort från en kortlek.

1. Skapa en component `CardGame`.
2. Skapa en array med minst 10 kort som state. Varje kort är ett objekt med `id`, `suit` (färg: "♠", "♥", "♦", "♣") och `value` (t.ex. "A", "2", "K"):
   ```jsx
   const startDeck = [
     { id: 1, suit: "♠", value: "A" },
     { id: 2, suit: "♥", value: "K" },
     // ... fler kort
   ];
   ```
3. Skapa två state-variabler: `deck` (kortleken) och `hand` (dragna kort, börjar tom).
4. Lägg till en "Dra kort"-knapp som:
   - Tar det översta kortet från `deck`
   - Lägger till det i `hand`
   - Tar bort det från `deck`
5. Visa handen som en lista med kort. Styla dem med inline styles — röd färg för ♥ och ♦, svart för ♠ och ♣.
6. Visa antal kort kvar i leken.
7. Inaktivera knappen (`disabled`) när leken är tom.
8. Lägg till en "Börja om"-knapp som återställer leken och tömmer handen.
9. Visa ett meddelande "Inga kort kvar!" när leken är tom.

## Förväntat resultat

En sida med en kortlek, en knapp att dra kort, och en hand som fylls med kort. Kort visas med färg och värde. När leken tar slut visas ett meddelande och knappen inaktiveras. Man kan börja om.

## Tips

<details>
<summary>Ledtråd 1</summary>

Att "dra" ett kort är att flytta det från en array till en annan:

```jsx
function drawCard() {
  if (deck.length === 0) return;
  const [topCard, ...rest] = deck;
  setHand([...hand, topCard]);
  setDeck(rest);
}
```

</details>

<details>
<summary>Ledtråd 2</summary>

Villkorlig styling med inline styles:

```jsx
const isRed = suit === "♥" || suit === "♦";
<span style={{ color: isRed ? "red" : "black" }}>
  {value}{suit}
</span>
```

Inaktivera knappen: `<button disabled={deck.length === 0}>Dra kort</button>`

</details>

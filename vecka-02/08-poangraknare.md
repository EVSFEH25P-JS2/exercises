# Poängräknare (Extra)

## Mål

Kombinera state, events, listor och conditional rendering i en komplett poängräknar-app.

## Förkunskaper

- [State och events](../../documents/03-state-events.md)
- [Listor och conditional rendering](../../documents/04-listor-conditional-rendering.md)
- [Todo-lista](06-todo-lista.md)

## Instruktioner

1. Skapa en component `ScoreBoard`.
2. Skapa state för en lista av spelare (tom array) och ett input-fält för nya spelarnamn.
3. Lägg till ett input-fält och en "Lägg till"-knapp. När man klickar skapas en ny spelare med namn och `score: 0`.
4. Rendera varje spelare med namn, poäng och tre knappar: **+1**, **-1** och **Ta bort**.
5. Poäng ska inte kunna gå under 0.
6. Markera spelaren med högst poäng (t.ex. med en CSS-klass eller en emoji). Om flera delar högsta poängen, markera alla.
7. Lägg till en "Nollställ alla"-knapp som sätter alla spelares poäng till 0.
8. Om inga spelare finns, visa "Lägg till spelare för att börja."

## Förväntat resultat

En poängräknare där man kan lägga till spelare, justera poäng, se vem som leder, ta bort spelare och nollställa. Ledaren är markerad.

## Tips

<details>
<summary>Ledtråd 1</summary>

Hitta högsta poängen och jämför:

```jsx
const highestScore = Math.max(...players.map((p) => p.score), 0);
```

Markera en spelare som ledare om `player.score === highestScore && highestScore > 0`.

</details>

<details>
<summary>Ledtråd 2</summary>

Hindra poäng under 0 och nollställ alla:

```jsx
// -1 med gräns
setPlayers((prev) =>
  prev.map((p) =>
    p.id === id ? { ...p, score: Math.max(0, p.score - 1) } : p
  )
);

// Nollställ alla
setPlayers((prev) => prev.map((p) => ({ ...p, score: 0 })));
```

</details>

# Todo-lista (Utmaning)

## Mål

Kombinera state, events, listor och conditional rendering i en komplett mini-app.

## Förkunskaper

- [State och events](../../documents/03-state-events.md)
- [Listor och conditional rendering](../../documents/04-listor-conditional-rendering.md)

## Instruktioner

1. Skapa en component `TodoApp`.
2. Skapa state för en lista av todos (tom array) och en input-text (tom sträng).
3. Lägg till ett input-fält och en "Lägg till"-knapp.
4. När användaren klickar "Lägg till": lägg till texten som ett nytt todo-objekt i listan (med `id`, `text` och `done: false`). Töm input-fältet.
5. Rendera alla todos med `.map()`.
6. Lägg till en "Ta bort"-knapp bredvid varje todo som tar bort den från listan.
7. Lägg till möjligheten att markera en todo som klar — klicka på texten för att toggla `done`.
8. Ge klarmarkerade todos en CSS-klass som ger `text-decoration: line-through`.
9. Om listan är tom, visa "Inga todos ännu." istället.
10. Visa antalet todos som inte är klara: "X kvar att göra".

## Förväntat resultat

En todo-app där man kan lägga till, ta bort och klarmarkera todos. Klarmarkerade todos får genomstruken text. Antalet kvarvarande todos visas.

## Tips

<details>
<summary>Ledtråd 1</summary>

Använd `Date.now()` som unikt ID:

```jsx
setTodos((prev) => [...prev, { id: Date.now(), text: input, done: false }]);
```

</details>

<details>
<summary>Ledtråd 2</summary>

Toggla `done` med `.map()`:

```jsx
setTodos((prev) =>
  prev.map((todo) =>
    todo.id === id ? { ...todo, done: !todo.done } : todo
  )
);
```

</details>

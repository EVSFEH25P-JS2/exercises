# Formulär med lista (Utmaning)

## Mål

Kombinera formulär och listor — lägg till objekt via ett formulär och visa dem i en lista.

## Förkunskaper

- [Formulär och controlled components](../../documents/06-formular-controlled-components.md)
- [Listor och conditional rendering](../../documents/04-listor-conditional-rendering.md)
- [Formulär — controlled components](04-formular.md)

## Instruktioner

1. Skapa en component `BookList`.
2. Skapa state för en lista av böcker (tom array).
3. Skapa state för formuläret: `title`, `author`, `rating` (1-5 som select).
4. Bygg ett formulär med input för titel, input för författare, och en `<select>` för betyg (1-5).
5. Vid submit: validera att titel och författare inte är tomma. Lägg till ett nytt bok-objekt i listan med `id`, `title`, `author` och `rating`. Töm formuläret.
6. Rendera alla böcker som kort eller listelement med all info.
7. Lägg till en "Ta bort"-knapp vid varje bok.
8. Visa "Inga böcker tillagda ännu." om listan är tom.
9. Visa totalt antal böcker ovanför listan.

## Förväntat resultat

En app där du kan lägga till böcker via formuläret, se dem i en lista, och ta bort dem. Tomma fält ger ett felmeddelande. Antalet böcker visas.

## Tips

<details>
<summary>Ledtråd 1</summary>

```jsx
const [rating, setRating] = useState("3");

<select value={rating} onChange={(e) => setRating(e.target.value)}>
  <option value="1">1</option>
  <option value="2">2</option>
  <option value="3">3</option>
  <option value="4">4</option>
  <option value="5">5</option>
</select>
```

</details>

<details>
<summary>Ledtråd 2</summary>

Ta bort med `.filter()`:

```jsx
function handleRemove(id) {
  setBooks((prev) => prev.filter((book) => book.id !== id));
}
```

</details>

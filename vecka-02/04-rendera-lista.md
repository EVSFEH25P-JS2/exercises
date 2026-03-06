# Rendera en lista (Grund)

## Mål

Öva på att rendera listor med `.map()` och förstå varför `key` behövs.

## Förkunskaper

- [Listor och conditional rendering](../../documents/04-listor-conditional-rendering.md)

## Instruktioner

1. Skapa en component `FruitList`.
2. Skapa en array med minst fem frukter (strängar).
3. Rendera varje frukt som en `<li>` i en `<ul>` med `.map()`.
4. Öppna konsolen i webbläsaren — du ska se en varning om `key`. Fixa den genom att lägga till `key` på varje `<li>`.
5. Skapa en ny array med objekt istället:

```jsx
const fruits = [
  { id: 1, name: "Äpple", color: "Röd" },
  { id: 2, name: "Banan", color: "Gul" },
  { id: 3, name: "Kiwi", color: "Grön" },
  { id: 4, name: "Blåbär", color: "Blå" },
  { id: 5, name: "Apelsin", color: "Orange" },
];
```

6. Rendera varje frukt som ett kort med namn och färg. Använd `id` som `key`.

## Förväntat resultat

En lista med frukter renderade dynamiskt med `.map()`. Inga varningar i konsolen.

## Tips

<details>
<summary>Ledtråd 1</summary>

```jsx
{fruits.map((fruit) => (
  <li key={fruit.id}>{fruit.name} — {fruit.color}</li>
))}
```

</details>

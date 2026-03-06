# Dynamisk fetch (Utmaning)

## Mål

Öva på att hämta data baserat på state — effecten körs om när en dependency ändras.

## Förkunskaper

- [useEffect och data fetching](../../documents/05-useeffect-data-fetching.md)
- [Hämta data från ett API](02-hamta-data.md)

## Instruktioner

1. Skapa en component `PostViewer`.
2. Skapa state för `postId` (startvärde `1`), `post` (startvärde `null`) och `loading`.
3. Lägg till en `useEffect` som hämtar en post baserat på `postId`:
   `https://jsonplaceholder.typicode.com/posts/{postId}`
4. Lägg `postId` i dependency array.
5. Rendera postens `title` och `body`.
6. Lägg till knappar "Föregående" och "Nästa" som ändrar `postId`.
7. Inaktivera "Föregående" om `postId` är 1.
8. Visa "Laddar..." under loading.

## Förväntat resultat

En post visas med titel och text. Klick på "Nästa" och "Föregående" laddar en ny post från API:et. Knappen "Föregående" är inaktiverad på post 1.

## Tips

<details>
<summary>Ledtråd 1</summary>

Effecten körs om automatiskt när `postId` ändras:

```jsx
useEffect(() => {
  setLoading(true);
  fetch(`https://jsonplaceholder.typicode.com/posts/${postId}`)
    .then((res) => res.json())
    .then((data) => setPost(data))
    .finally(() => setLoading(false));
}, [postId]);
```

</details>

<details>
<summary>Ledtråd 2</summary>

Inaktivera knappen med `disabled`-attributet:

```jsx
<button disabled={postId <= 1} onClick={() => setPostId((prev) => prev - 1)}>
  Föregående
</button>
```

</details>

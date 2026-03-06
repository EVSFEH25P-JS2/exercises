# Hämta data från ett API (Grund)

## Mål

Öva på att hämta data med `fetch` inuti `useEffect` och rendera resultatet.

## Förkunskaper

- [useEffect och data fetching](../../documents/05-useeffect-data-fetching.md)
- [useEffect — introduktion](01-useeffect-intro.md)

## Instruktioner

1. Skapa en component `UserList`.
2. Skapa state för `users` (tom array).
3. Lägg till en `useEffect` med tom dependency array som hämtar data från:
   `https://jsonplaceholder.typicode.com/users`
4. Uppdatera `users` med datan.
5. Rendera varje användare i en lista med namn och e-post.
6. Lägg till state för `loading` (startvärde `true`) och `error` (startvärde `null`).
7. Sätt `loading` till `false` i `finally`-blocket.
8. Fånga fel med `try/catch` och spara felmeddelandet i `error`.
9. Visa "Laddar..." medan loading är true, felmeddelandet om error finns, och listan annars.

## Förväntat resultat

En lista med 10 användare (namn och e-post) hämtade från API:et. Under laddning visas "Laddar...". Om du stänger av nätverket och laddar om ska ett felmeddelande visas.

## Tips

<details>
<summary>Ledtråd 1</summary>

Grundmönstret:

```jsx
useEffect(() => {
  async function fetchUsers() {
    try {
      const response = await fetch("https://jsonplaceholder.typicode.com/users");
      const data = await response.json();
      setUsers(data);
    } catch (err) {
      setError(err.message);
    } finally {
      setLoading(false);
    }
  }

  fetchUsers();
}, []);
```

</details>

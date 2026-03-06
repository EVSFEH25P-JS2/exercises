# Custom hook (Grund)

## Mål

Öva på att extrahera återanvändbar logik till en custom hook.

## Förkunskaper

- [Component patterns och komposition](../../documents/09-component-patterns.md)
- [useEffect och data fetching](../../documents/05-useeffect-data-fetching.md)

## Instruktioner

1. Skapa en mapp `src/hooks/`.
2. Skapa en hook `useFetch` i `src/hooks/useFetch.js` som tar emot en `url` som parameter.
3. Hooken ska hantera `data`, `loading` och `error` internt med `useState` och `useEffect`.
4. Returnera ett objekt: `{ data, loading, error }`.
5. Skapa en component `UserPage` som använder `useFetch` för att hämta en användare:
   `https://jsonplaceholder.typicode.com/users/1`
6. Skapa en component `PostPage` som använder samma `useFetch` för att hämta poster:
   `https://jsonplaceholder.typicode.com/posts?_limit=5`
7. Rendera båda components i `App.jsx`.

## Förväntat resultat

Två components som hämtar helt olika data men använder samma hook. Ingen duplicerad fetch-logik. Båda hanterar loading och error.

## Tips

<details>
<summary>Ledtråd 1</summary>

```jsx
function useFetch(url) {
  const [data, setData] = useState(null);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState(null);

  useEffect(() => {
    // fetch-logik här
  }, [url]);

  return { data, loading, error };
}
```

</details>

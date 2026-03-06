# Async actions i Zustand (Extra)

## Mål

Öva på att flytta API-anrop till Zustand store med async actions.

## Förkunskaper

- [Zustand](../../documents/08-zustand.md)
- [useEffect och data fetching](../../documents/05-useeffect-data-fetching.md)

## Instruktioner

1. Skapa ett store `usePostStore.js` med:
   - `posts` (tom array)
   - `loading` (`false`)
   - `error` (`null`)
   - `fetchPosts()` — async action som hämtar poster från `https://jsonplaceholder.typicode.com/posts?_limit=20`
2. `fetchPosts` ska sätta `loading` till `true`, hämta data, uppdatera `posts`, och hantera fel.
3. Skapa en page `Posts.jsx` som anropar `fetchPosts` i en `useEffect` vid mount.
4. Visa loading, error och listan av poster.
5. Lägg till en "Ladda om"-knapp som anropar `fetchPosts` igen.
6. Jämför med hur du hade gjort samma sak med `useState` + `useEffect` direkt i componenten. Reflektera: när är det värt att flytta logiken till storen?

## Förväntat resultat

En lista med poster hämtade via en Zustand async action. Loading och error hanteras i storen. Componenten är enkel — den anropar en action och läser state.

## Tips

<details>
<summary>Ledtråd 1</summary>

```jsx
const usePostStore = create((set) => ({
  posts: [],
  loading: false,
  error: null,
  fetchPosts: async () => {
    set({ loading: true, error: null });
    try {
      const response = await fetch("https://jsonplaceholder.typicode.com/posts?_limit=20");
      const data = await response.json();
      set({ posts: data, loading: false });
    } catch (err) {
      set({ error: err.message, loading: false });
    }
  },
}));
```

</details>

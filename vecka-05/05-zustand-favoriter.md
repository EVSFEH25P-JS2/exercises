# Zustand — favoriter med routing (Utmaning)

## Mål

Kombinera Zustand och React Router — spara favoriter globalt och visa dem på en egen sida.

## Förkunskaper

- [Zustand](../../documents/08-zustand.md)
- [React Router](../../documents/07-react-router.md)
- [Zustand — skapa ett store](04-zustand-store.md)

## Instruktioner

1. Skapa ett store `useFavoritesStore.js` med:
   - `favorites` (tom array)
   - `addFavorite(item)` — lägger till ett objekt i listan (om det inte redan finns)
   - `removeFavorite(id)` — tar bort ett objekt baserat på ID
   - `isFavorite(id)` — returnerar `true` om objektet finns i listan
2. Skapa en page `Products.jsx` som hämtar produkter från `https://fakestoreapi.com/products?limit=10`.
3. Varje produkt ska ha en knapp "Lägg till favorit" / "Ta bort favorit" (beroende på om den redan är favorit).
4. Skapa en page `Favorites.jsx` som visar alla sparade favoriter från storen.
5. Lägg till routes: `/products` och `/favorites`.
6. I navbar, visa antalet favoriter bredvid "Favoriter"-länken: "Favoriter (3)".

## Förväntat resultat

En produktlista där man kan favoritmarkera produkter. Favoriter sparas globalt och visas på en egen sida. Antalet uppdateras i navbaren. Navigering mellan sidor behåller all state.

## Tips

<details>
<summary>Ledtråd 1</summary>

Kontrollera om en produkt redan är favorit:

```jsx
addFavorite: (item) =>
  set((state) => {
    if (state.favorites.some((f) => f.id === item.id)) return state;
    return { favorites: [...state.favorites, item] };
  }),
```

</details>

<details>
<summary>Ledtråd 2</summary>

I navbar, hämta antalet med en selector:

```jsx
const count = useFavoritesStore((state) => state.favorites.length);
```

</details>

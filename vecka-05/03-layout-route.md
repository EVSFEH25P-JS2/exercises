# Layout route (Utmaning)

## Mål

Öva på att skapa en gemensam layout med `Outlet` och en 404-sida.

## Förkunskaper

- [React Router](../../documents/07-react-router.md)
- [Routing — grunder](01-routing-grunder.md)

## Instruktioner

1. Skapa en `Layout`-component i `src/components/Layout.jsx`.
2. Layouten ska ha:
   - En `<header>` med en `<nav>` (NavLinks till alla sidor)
   - En `<main>` som renderar `<Outlet />`
   - En `<footer>` med copyright-text
3. Styla layouten med CSS (navbar överst, content i mitten, footer underst).
4. Uppdatera `App.jsx` — omslut alla routes med en layout route:

```jsx
<Routes>
  <Route element={<Layout />}>
    <Route path="/" element={<Home />} />
    {/* ... fler routes */}
  </Route>
</Routes>
```

5. Skapa en `NotFound`-component som visas vid okända URL:er.
6. Lägg till en catch-all route: `<Route path="*" element={<NotFound />} />` inuti layout-routen.
7. Testa genom att navigera till en URL som inte finns, t.ex. `/xyz`.

## Förväntat resultat

Alla sidor delar samma header/nav/footer. Bara innehållet i `<main>` byts ut. Okända URL:er visar 404-sidan — med layouten runt.

## Tips

<details>
<summary>Ledtråd 1</summary>

```jsx
import { Outlet } from "react-router";

function Layout() {
  return (
    <div>
      <header>{/* navbar */}</header>
      <main><Outlet /></main>
      <footer>{/* copyright */}</footer>
    </div>
  );
}
```

</details>

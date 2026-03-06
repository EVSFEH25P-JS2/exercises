# Routing — grunder (Grund)

## Mål

Öva på att sätta upp React Router med flera sidor och navigation.

## Förkunskaper

- [React Router](../../documents/07-react-router.md)

## Instruktioner

1. Installera React Router: `npm install react-router`
2. I `main.jsx`, omslut `<App />` med `<BrowserRouter>` (importera från `"react-router"`).
3. Skapa tre page-components i en `src/pages/`-mapp: `Home.jsx`, `About.jsx`, `Contact.jsx`. Varje sida ska ha en rubrik och lite text.
4. I `App.jsx`, importera `Routes` och `Route` från `"react-router"`. Definiera tre routes:
   - `/` → `Home`
   - `/about` → `About`
   - `/contact` → `Contact`
5. Testa genom att manuellt ändra URL:en i webbläsaren.
6. Skapa en `Navbar`-component med `Link`-components (från `"react-router"`) till alla tre sidor.
7. Rendera `Navbar` ovanför `Routes` i `App.jsx`.
8. Byt ut `Link` mot `NavLink` och ge den aktiva länken en CSS-klass.

## Förväntat resultat

En app med tre sidor och en navbar. Klick på en länk byter sida utan att ladda om. Den aktiva länken är markerad.

## Tips

<details>
<summary>Ledtråd 1</summary>

Allt importeras från `"react-router"` i v7 — inte `"react-router-dom"`.

```jsx
import { BrowserRouter, Routes, Route, NavLink } from "react-router";
```

</details>

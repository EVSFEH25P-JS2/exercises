# Temaväxlare med Zustand (Extra)

## Mål

Kombinera Zustand och React Router genom att bygga en temaväxlare som fungerar på alla sidor.

## Förkunskaper

- [Zustand](../../documents/08-zustand.md)
- [React Router](../../documents/07-react-router.md)
- [Zustand — skapa ett store](04-zustand-store.md)

## Instruktioner

1. Skapa ett Zustand store `useThemeStore` med:
   - State: `theme` (börjar som `"light"`)
   - Action: `toggleTheme` (växlar mellan `"light"` och `"dark"`)
2. I din layout-component, hämta `theme` med en selector och sätt det som CSS-klass på root-elementet: `<div className={theme}>`.
3. Lägg till en knapp i navbaren som kör `toggleTheme`. Knappen ska visa "Byt till dark" eller "Byt till light" beroende på aktuellt tema.
4. Skapa CSS för båda teman. Använd `.light` och `.dark` som parent-klasser:
   ```css
   .light { background: #fff; color: #222; }
   .dark { background: #222; color: #eee; }
   ```
5. Navigera mellan minst två sidor och kontrollera att temat bevaras.

## Förväntat resultat

En app där man kan byta mellan ljust och mörkt tema. Temat gäller hela appen och bevaras vid navigering mellan sidor.

## Tips

<details>
<summary>Ledtråd 1</summary>

```jsx
import { create } from "zustand";

const useThemeStore = create((set) => ({
  theme: "light",
  toggleTheme: () =>
    set((state) => ({
      theme: state.theme === "light" ? "dark" : "light",
    })),
}));
```

</details>

<details>
<summary>Ledtråd 2</summary>

I layouten:

```jsx
function Layout() {
  const theme = useThemeStore((state) => state.theme);
  const toggleTheme = useThemeStore((state) => state.toggleTheme);

  return (
    <div className={theme}>
      <nav>
        <button onClick={toggleTheme}>
          Byt till {theme === "light" ? "dark" : "light"}
        </button>
      </nav>
      <Outlet />
    </div>
  );
}
```

</details>

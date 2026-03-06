# Zustand — skapa ett store (Grund)

## Mål

Öva på att skapa ett Zustand store och använda det i flera components.

## Förkunskaper

- [Zustand](../../documents/08-zustand.md)

## Instruktioner

1. Installera Zustand: `npm install zustand`
2. Skapa en mapp `src/stores/` och en fil `useCounterStore.js`.
3. Skapa ett store med:
   - `count` (startvärde `0`)
   - `increment` — ökar count med 1
   - `decrement` — minskar count med 1
   - `reset` — sätter count till 0
4. Skapa en component `CounterDisplay` som hämtar `count` med en selector och visar det.
5. Skapa en component `CounterButtons` som hämtar `increment`, `decrement` och `reset` och renderar tre knappar.
6. Placera `CounterDisplay` och `CounterButtons` på olika ställen i komponentträdet (t.ex. en i header, en i main).
7. Kontrollera att klick på knapparna uppdaterar displayen — utan att skicka props mellan dem.

## Förväntat resultat

Två separata components som delar state via Zustand utan props. Knapparna i en component uppdaterar siffran i en annan.

## Tips

<details>
<summary>Ledtråd 1</summary>

```jsx
import { create } from "zustand";

const useCounterStore = create((set) => ({
  count: 0,
  increment: () => set((state) => ({ count: state.count + 1 })),
  decrement: () => set((state) => ({ count: state.count - 1 })),
  reset: () => set({ count: 0 }),
}));
```

</details>

<details>
<summary>Ledtråd 2</summary>

Använd selectors — hämta bara det du behöver:

```jsx
const count = useCounterStore((state) => state.count);
const increment = useCounterStore((state) => state.increment);
```

</details>

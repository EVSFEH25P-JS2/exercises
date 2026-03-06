# Timer med cleanup (Grund)

## Mål

Öva på useEffect cleanup genom att bygga en timer som städar upp efter sig.

## Förkunskaper

- [useEffect och data fetching](../../documents/05-useeffect-data-fetching.md)

## Instruktioner

1. Skapa en component `Timer`.
2. Skapa state `seconds` (börja på `0`) och `isRunning` (börja på `false`).
3. Lägg till en `useEffect` som startar en `setInterval` när `isRunning` är `true`. Intervallet ska öka `seconds` med 1 varje sekund.
4. Returnera en cleanup-funktion från useEffect som kör `clearInterval`.
5. Ha `[isRunning]` som dependency array.
6. Lägg till tre knappar: **Start** (sätter `isRunning` till `true`), **Pausa** (sätter `isRunning` till `false`) och **Nollställ** (sätter `seconds` till `0` och `isRunning` till `false`).
7. Skapa en component `TimerPage` med en knapp som togglar om `Timer` visas eller inte. Lägg till en `console.log("Cleanup!")` i cleanup-funktionen och verifiera i konsolen att den körs när timern tas bort.

## Förväntat resultat

En timer som räknar sekunder. Start, pausa och nollställ fungerar. När timern göms från sidan städas intervallet upp — inga varningar i konsolen.

## Tips

<details>
<summary>Ledtråd 1</summary>

```jsx
useEffect(() => {
  if (!isRunning) return;

  const id = setInterval(() => {
    setSeconds((prev) => prev + 1);
  }, 1000);

  return () => {
    console.log("Cleanup!");
    clearInterval(id);
  };
}, [isRunning]);
```

</details>

<details>
<summary>Ledtråd 2</summary>

Toggla om `Timer` visas med conditional rendering:

```jsx
function TimerPage() {
  const [showTimer, setShowTimer] = useState(true);

  return (
    <div>
      <button onClick={() => setShowTimer(!showTimer)}>
        {showTimer ? "Göm timer" : "Visa timer"}
      </button>
      {showTimer && <Timer />}
    </div>
  );
}
```

</details>

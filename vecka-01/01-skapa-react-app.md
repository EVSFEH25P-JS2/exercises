# Skapa en React-app (Grund)

## Mål

Öva på att skapa ett nytt React-projekt med Vite och förstå projektstrukturen.

## Förkunskaper

- [Introduktion till React och JSX](../../documents/01-introduktion-react-jsx.md)

## Instruktioner

1. Öppna terminalen och kör: `npm create vite@latest min-app -- --template react`
2. Gå in i projektmappen: `cd min-app`
3. Installera dependencies: `npm install`
4. Starta utvecklingsservern: `npm run dev`
5. Öppna `http://localhost:5173` i webbläsaren.
6. Öppna `src/App.jsx` och ta bort allt innehåll inuti `return (...)`.
7. Ersätt med en `<h1>` som säger "Min första React-app" och en `<p>` med ditt namn.
8. Spara filen och kontrollera att sidan uppdateras automatiskt i webbläsaren.
9. Öppna `src/main.jsx` och identifiera vad varje rad gör. Skriv en kommentar ovanför varje rad som förklarar.

## Förväntat resultat

En sida som visar "Min första React-app" som rubrik och ditt namn under. Hot Module Replacement (HMR) uppdaterar sidan automatiskt när du sparar.

## Tips

<details>
<summary>Ledtråd 1</summary>
Se till att returnera ett enda rot-element. Omslut `h1` och `p` med en `div` eller ett fragment (`<>...</>`).
</details>

# Villkorlig rendering med props (Grund)

## Mål

Öva på att rendera olika innehåll beroende på props-värden — en första introduktion till villkorlig rendering.

## Förkunskaper

- [Components och props](../../documents/02-components-props.md)
- [Props](05-props.md)

## Instruktioner

1. Skapa en component `StatusBadge` som tar emot en prop `status` med värdet `"online"`, `"offline"` eller `"busy"`.
2. Använd en ternary eller `if`/`else if` för att rendera olika text och färg beroende på status:
   - `"online"` → grön text, "🟢 Online"
   - `"busy"` → gul text, "🟡 Upptagen"
   - `"offline"` → grå text, "⚫ Offline"
3. Rendera tre `StatusBadge` i `App.jsx` — en för varje status.
4. Skapa en component `Alert` som tar emot `type` (`"success"`, `"warning"`, `"error"`) och `children`.
   - Styla bakgrundsfärgen baserat på `type` med inline styles: `style={{ backgroundColor: color }}`
   - Rendera `children` inuti.
5. Rendera tre `Alert`-components med olika typer och meddelanden.
6. Lägg till en prop `dismissable` (boolean) på `Alert`. Om `true`, visa en "✕"-knapp i hörnet. Knappen behöver inte göra något än — bara visas.

## Förväntat resultat

Tre statusbadges med olika färger och texter. Tre alertrutor med olika bakgrundsfärger och meddelanden. Minst en alert visar en stängknapp.

## Tips

<details>
<summary>Ledtråd 1</summary>

Du kan välja färg med en enkel funktion eller ternary:

```jsx
function StatusBadge({ status }) {
  const color = status === "online" ? "green" : status === "busy" ? "orange" : "gray";

  return <span style={{ color }}>...</span>;
}
```

</details>

<details>
<summary>Ledtråd 2</summary>

Använd `&&` för att villkorligt visa stängknappen:

```jsx
{dismissable && <button>✕</button>}
```

Inline styles i React är objekt med camelCase-nycklar: `style={{ backgroundColor: "red", padding: "10px" }}`.

</details>

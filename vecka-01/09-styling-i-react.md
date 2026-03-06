# Styling i React (Grund)

## Mål

Öva på att styla React-components med CSS-filer och `className`.

## Förkunskaper

- [Introduktion till React och JSX](../../documents/01-introduktion-react-jsx.md)
- [Din första component](04-din-forsta-component.md)

## Instruktioner

1. Skapa en component `ProfileCard` i `src/ProfileCard.jsx`.
2. Skapa en CSS-fil `src/ProfileCard.css`.
3. Importera CSS-filen i din component: `import "./ProfileCard.css"`.
4. `ProfileCard` ska ta emot `name`, `role` och `imageUrl` som props.
5. Rendera ett kort med:
   - En `<img>` med `imageUrl` som `src`
   - `name` i en `<h2>`
   - `role` i en `<p>`
6. Ge elementen `className` och styla dem i CSS-filen:
   - Kortet ska ha en ram, rundade hörn och padding
   - Bilden ska vara rund (tips: `border-radius: 50%`) med en fast bredd
   - Namnet ska ha en annan färg än rollen
7. Rendera tre `ProfileCard` i `App.jsx` med olika data.
8. Lägg till en CSS-klass `highlight` som ger kortet en annan bakgrundsfärg. Använd en prop `highlighted` (boolean) för att villkorligt lägga till klassen:
   ```jsx
   <div className={`card ${highlighted ? "highlight" : ""}`}>
   ```

## Förväntat resultat

Tre profilkort med bild, namn och roll — snyggt stylade. Minst ett kort har en avvikande bakgrundsfärg via `highlighted`-propen.

## Tips

<details>
<summary>Ledtråd 1</summary>

I React importerar du CSS-filer direkt i din component-fil. Alla klasser i filen blir tillgängliga via `className`.

```jsx
import "./ProfileCard.css";

function ProfileCard({ name, role, imageUrl }) {
  return (
    <div className="card">
      <img className="avatar" src={imageUrl} alt={name} />
      <h2>{name}</h2>
      <p>{role}</p>
    </div>
  );
}
```

</details>

<details>
<summary>Ledtråd 2</summary>

Template literals gör det enkelt att villkorligt lägga till klasser:

```jsx
<div className={`card ${highlighted ? "highlight" : ""}`}>
```

Du kan också använda `.trim()` om du vill undvika extra mellanslag.

</details>

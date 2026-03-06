# Props spreading (Utmaning)

## Mål

Öva på att använda rest-parametrar och props spreading för att bygga flexibla, återanvändbara components.

## Förkunskaper

- [Component patterns och komposition](../../documents/09-component-patterns.md)

## Instruktioner

1. Skapa en component `Button` som tar emot:
   - `variant` (`"primary"` eller `"secondary"`) — sätter CSS-klass
   - `children` — knappens text
   - `...rest` — alla övriga props skickas vidare till `<button>`-elementet
2. Testa att `onClick`, `disabled` och `type` fungerar utan att `Button` explicit hanterar dem.
3. Skapa en component `Input` som tar emot:
   - `label` — visas som `<label>` ovanför fältet
   - `...rest` — skickas vidare till `<input>`-elementet
4. Bygg ett formulär med dina `Button`- och `Input`-components. Formuläret ska ha minst två fält och en submit-knapp.
5. Verifiera att `placeholder`, `type`, `value`, `onChange` och andra standard-attribut fungerar via spreading.

## Förväntat resultat

Återanvändbara `Button` och `Input` som beter sig som vanliga HTML-element men med extra styling-logik. Alla standard HTML-attribut fungerar tack vare `...rest`.

## Tips

<details>
<summary>Ledtråd 1</summary>

```jsx
function Button({ variant = "primary", children, ...rest }) {
  return (
    <button className={`btn btn-${variant}`} {...rest}>
      {children}
    </button>
  );
}

// Användning — onClick och disabled skickas vidare automatiskt
<Button variant="primary" onClick={handleSave} disabled={!isValid}>
  Spara
</Button>
```

</details>

<details>
<summary>Ledtråd 2</summary>

```jsx
function Input({ label, ...rest }) {
  return (
    <div>
      <label>{label}</label>
      <input {...rest} />
    </div>
  );
}

// Användning — type, value, onChange skickas vidare
<Input label="Email" type="email" value={email} onChange={handleChange} />
```

</details>

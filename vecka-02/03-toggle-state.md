# Toggle state (Grund)

## Mål

Öva på att använda boolean state för att visa och dölja element.

## Förkunskaper

- [State och events](../../documents/03-state-events.md)
- [Listor och conditional rendering](../../documents/04-listor-conditional-rendering.md)

## Instruktioner

1. Skapa en component `ToggleMessage`.
2. Skapa en state-variabel `isVisible` med startvärde `false`.
3. Lägg till en knapp som togglar `isVisible` mellan `true` och `false`.
4. Om `isVisible` är `true`, visa en `<p>` med texten "Nu ser du mig!". Annars, visa ingenting.
5. Ändra texten på knappen: "Visa" om meddelandet är gömt, "Dölj" om det visas.
6. Skapa en andra component `Accordion` som tar emot `title` och `children`. Klicka på titeln för att visa/dölja innehållet.

## Förväntat resultat

En knapp som togglar synligheten av ett meddelande. Knappens text ändras beroende på state. En accordion som visar/döljer sitt innehåll vid klick.

## Tips

<details>
<summary>Ledtråd 1</summary>

Använd ternary för knappens text och `&&` för att villkorligt visa innehåll:

```jsx
<button onClick={() => setIsVisible(!isVisible)}>
  {isVisible ? "Dölj" : "Visa"}
</button>
{isVisible && <p>Nu ser du mig!</p>}
```

</details>

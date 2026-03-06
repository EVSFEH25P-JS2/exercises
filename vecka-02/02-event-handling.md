# Event handling (Grund)

## Mål

Öva på att hantera olika events och skriva event handler-funktioner.

## Förkunskaper

- [State och events](../../documents/03-state-events.md)
- [useState — räknare](01-usestate-raknare.md)

## Instruktioner

1. Skapa en component `EventPlayground`.
2. Lägg till en knapp med en `onClick`-handler som loggar "Knappen klickad!" till konsolen.
3. Flytta logiken till en separat funktion `handleClick` istället för inline.
4. Lägg till ett text-input med `onChange`. Logga varje ny bokstav till konsolen.
5. Skapa en state-variabel `text` och visa det användaren skriver i en `<p>` under input-fältet, i realtid.
6. Lägg till en knapp "Rensa" som tömmer `text`.
7. Lägg till en `onMouseEnter`-handler på en `<div>` som loggar "Muspekaren är här!" till konsolen.

## Förväntat resultat

En sida med en klickknapp, ett textfält som visar vad du skriver i realtid, en rensa-knapp, och ett element som reagerar på hover.

## Tips

<details>
<summary>Ledtråd 1</summary>

`onChange` ger oss ett event-objekt. Värdet ligger i `e.target.value`:

```jsx
<input onChange={(e) => setText(e.target.value)} />
```

</details>

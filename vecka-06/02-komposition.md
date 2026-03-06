# Komposition med children (Grund)

## Mål

Öva på att bygga flexibla components med `children` och komposition.

## Förkunskaper

- [Component patterns och komposition](../../documents/09-component-patterns.md)

## Instruktioner

1. Skapa en component `PageLayout` som renderar:
   - En `<header>` med appens namn
   - En `<main>` med `{children}`
   - En `<footer>` med copyright
2. Styla layouten med CSS så att footer alltid hamnar längst ner.
3. Skapa en component `Modal` som tar emot `title` och `children`. Rendera en overlay-bakgrund och en ruta med titeln och innehållet.
4. Lägg till en prop `onClose` (funktion) och en stäng-knapp.
5. I `App.jsx`, skapa en knapp "Visa modal" som togglar en state-variabel. Visa `Modal` villkorligt:

```jsx
{showModal && (
  <Modal title="Bekräftelse" onClose={() => setShowModal(false)}>
    <p>Är du säker?</p>
    <button>Ja</button>
    <button onClick={() => setShowModal(false)}>Nej</button>
  </Modal>
)}
```

6. Notera hur `Modal` inte vet vad den innehåller — anroparen bestämmer via `children`.

## Förväntat resultat

En sida med layout-wrapper. En knapp som öppnar en modal med valfritt innehåll. Modalen kan stängas via knappen.

## Tips

<details>
<summary>Ledtråd 1</summary>

Styla modal-overlayen med `position: fixed`, `inset: 0`, och en halvtransparent bakgrund. Centrera rutan med flexbox.

</details>

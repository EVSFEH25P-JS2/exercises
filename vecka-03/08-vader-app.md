# Väder-app (Extra)

## Mål

Kombinera formulär, fetch och state-hantering i en väderapp.

## Förkunskaper

- [useEffect och data fetching](../../documents/05-useeffect-data-fetching.md)
- [Formulär och controlled components](../../documents/06-formular-controlled-components.md)

## Instruktioner

1. Skapa en component `WeatherApp`.
2. Skapa state för `city` (input-fält), `weather` (data från API:et, börjar som `null`), `loading` och `error`.
3. Lägg till ett formulär med ett textfält och en "Sök"-knapp.
4. Vid submit, hämta väderdata från: `https://wttr.in/{city}?format=j1`
5. Visa stadens namn, temperatur och väderbeskrivning.
6. Hantera loading och error. Om staden inte hittas, visa ett felmeddelande.
7. Innan första sökningen, visa "Sök efter en stad för att se vädret."

## Förväntat resultat

Ett sökfält där man skriver en stad och klickar sök. Väderdata visas. Loading visas under hämtning. Felmeddelande vid ogiltig stad. Innan sökning visas ett instruktionsmeddelande.

## Tips

<details>
<summary>Ledtråd 1</summary>

Det här är ett formulär-submit, inte en useEffect. Hämta data i `handleSubmit`:

```jsx
async function handleSubmit(e) {
  e.preventDefault();
  setLoading(true);
  setError(null);

  try {
    const res = await fetch(`https://wttr.in/${city}?format=j1`);
    if (!res.ok) throw new Error("Staden hittades inte");
    const data = await res.json();
    setWeather(data);
  } catch (err) {
    setError(err.message);
  } finally {
    setLoading(false);
  }
}
```

</details>

<details>
<summary>Ledtråd 2</summary>

API-svaret har denna struktur:

```jsx
const temp = data.current_condition[0].temp_C;
const description = data.current_condition[0].weatherDesc[0].value;
const area = data.nearest_area[0].areaName[0].value;
```

</details>

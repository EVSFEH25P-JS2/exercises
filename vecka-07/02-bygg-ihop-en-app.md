# Bygg ihop en app i grupp (Utmaning)

## Mål

Öva på att kombinera alla kursens koncept i en komplett applikation och samarbeta i grupp.

## Förkunskaper

- Alla tidigare ämnen i kursen

## Instruktioner

Ni ska bygga en **receptapp** tillsammans i gruppen. En person delar sin skärm (driver) medan de andra navigerar (hjälper till med beslut och kod).

### Krav

Appen ska ha:

1. **Routing** med minst tre sidor:
   - Startsida med en lista av recept
   - Detaljsida för ett enskilt recept (`/recipes/:id`)
   - Favoritsida som visar sparade favoriter
2. **Data fetching** — hämta recept från ett API: `https://www.themealdb.com/api/json/v1/1/search.php?s=chicken`
3. **Zustand store** — spara favoriter globalt
4. **Layout** — gemensam navbar med `Outlet`
5. **Formulär** — ett sökfält som filtrerar recepten

### Uppdelning

Byt vem som delar skärm (driver) efter varje steg:

1. **Steg 1:** Setup — Vite, React Router, layout med navbar (person 1 driver)
2. **Steg 2:** Hämta och visa recept på startsidan (person 2 driver)
3. **Steg 3:** Detaljsida med URL-parameter (person 3 driver)
4. **Steg 4:** Zustand store för favoriter + favoritsida (person 1 driver)
5. **Steg 5:** Sökfält med filtrering (person 2 driver)
6. **Steg 6:** Styling och polering (person 3 driver)

### Tidsbox

- 60 minuter totalt
- ~10 minuter per steg
- Det är okej att inte bli klar — fokus är på processen, inte resultatet

## Förväntat resultat

En fungerande (eller nästan fungerande) receptapp som gruppen byggt tillsammans. Alla har bidragit som driver minst en gång.

## Tips

<details>
<summary>Ledtråd 1</summary>

API-svaret från TheMealDB har strukturen:

```json
{
  "meals": [
    {
      "idMeal": "52772",
      "strMeal": "Teriyaki Chicken Casserole",
      "strMealThumb": "https://www.themealdb.com/images/media/meals/...",
      "strInstructions": "..."
    }
  ]
}
```

Hämta med: `data.meals`

</details>

<details>
<summary>Ledtråd 2</summary>

För sök med annat ord, ändra URL:en:
`https://www.themealdb.com/api/json/v1/1/search.php?s={sökord}`

</details>

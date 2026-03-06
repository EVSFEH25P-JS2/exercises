# Uppdatera objekt i state (Grund)

## Mål

Öva på att uppdatera objekt och arrayer i state utan att mutera — en viktig grundregel i React.

## Förkunskaper

- [State och events](../../documents/03-state-events.md)
- [useState — räknare](01-usestate-raknare.md)

## Instruktioner

### Del 1 — Objekt i state

1. Skapa en component `ProfileEditor`.
2. Skapa en state-variabel `profile` med startvärde:
   ```jsx
   const [profile, setProfile] = useState({
     name: "Anna",
     age: 25,
     city: "Stockholm",
   });
   ```
3. Rendera alla värden i en lista.
4. Lägg till tre `<input>`-fält (ett per egenskap) som uppdaterar `profile`. Använd spread-operatorn:
   ```jsx
   setProfile({ ...profile, name: e.target.value });
   ```
5. Verifiera att alla fält uppdaterar profilen korrekt utan att skriva över de andra värdena.

### Del 2 — Arrayer i state

6. Skapa en component `FruitList`.
7. Skapa en state-variabel `fruits` med startvärde `["Äpple", "Banan", "Citron"]`.
8. Rendera listan med `.map()`.
9. Lägg till ett input-fält och en "Lägg till"-knapp som lägger till en ny frukt:
   ```jsx
   setFruits([...fruits, newFruit]);
   ```
10. Lägg till en "Ta bort"-knapp bredvid varje frukt som tar bort den ur listan:
    ```jsx
    setFruits(fruits.filter((_, i) => i !== index));
    ```
11. Rendera båda components i `App.jsx`.

## Förväntat resultat

En profilredigerare där man kan ändra namn, ålder och stad. En fruktlista där man kan lägga till och ta bort frukter. Alla ändringar sker utan mutation.

## Tips

<details>
<summary>Ledtråd 1</summary>

Mutera aldrig state direkt. Detta är fel:

```jsx
// FEL — muterar state
profile.name = "Erik";
setProfile(profile);
```

Skapa alltid ett nytt objekt:

```jsx
// RÄTT — nytt objekt med spread
setProfile({ ...profile, name: "Erik" });
```

</details>

<details>
<summary>Ledtråd 2</summary>

För att ta bort från en array, filtrera bort elementet:

```jsx
setFruits(fruits.filter((_, i) => i !== index));
```

För att lägga till, skapa en ny array med spread:

```jsx
setFruits([...fruits, newFruit]);
```

</details>

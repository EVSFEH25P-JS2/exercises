# URL-parametrar (Grund)

## Mål

Öva på dynamiska routes med `:param` och `useParams`.

## Förkunskaper

- [React Router](../../documents/07-react-router.md)
- [Routing — grunder](01-routing-grunder.md)

## Instruktioner

1. Skapa en page-component `UserProfile.jsx`.
2. Lägg till en route: `/users/:userId`.
3. I `UserProfile`, använd `useParams()` för att hämta `userId`.
4. Visa `userId` på sidan: "Användarprofil för användare #42".
5. Skapa en page `Users.jsx` med en lista av användare (hårdkodad array med `id` och `name`). Varje namn ska vara en `Link` till `/users/{id}`.
6. Lägg till en route för `/users` → `Users`.
7. I `UserProfile`, hämta användardata baserat på `userId` från:
   `https://jsonplaceholder.typicode.com/users/{userId}`
8. Visa namn och e-post. Hantera loading.
9. Lägg till en `Link` tillbaka till `/users`.

## Förväntat resultat

En användarlista med klickbara namn. Klick navigerar till en profilsida som hämtar och visar data baserat på URL-parametern. En "Tillbaka"-länk tar dig tillbaka till listan.

## Tips

<details>
<summary>Ledtråd 1</summary>

```jsx
import { useParams, Link } from "react-router";

function UserProfile() {
  const { userId } = useParams();
  // userId är en sträng, t.ex. "42"
}
```

</details>

<details>
<summary>Ledtråd 2</summary>

Glöm inte `[userId]` i useEffect dependency array så att data hämtas om när man navigerar till en annan användare.

</details>

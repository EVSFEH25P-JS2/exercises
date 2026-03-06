# Component-sammansättning (Utmaning)

## Mål

Öva på att bygga ihop flera components som samverkar och skicka data via props i flera led.

## Förkunskaper

- [Components och props](../../documents/02-components-props.md)
- [Children-propen](06-children.md)

## Instruktioner

1. Skapa tre components i separata filer:
   - `Avatar` — tar emot `src` och `alt`, renderar en `<img>` med className `"avatar"`
   - `UserInfo` — tar emot `name` och `role`, renderar dem i en `<h3>` och `<p>`
   - `UserCard` — tar emot ett objekt `user`, renderar `Avatar` och `UserInfo` med rätt props
2. Styla `Avatar` (rund bild med `border-radius: 50%`, fast bredd/höjd).
3. Använd `Card`-componenten från förra övningen som wrapper i `UserCard`.
4. I `App.jsx`, skapa en array med minst tre user-objekt:

```jsx
const users = [
  { name: "Anna Svensson", role: "Designer", avatar: "https://i.pravatar.cc/150?img=1" },
  { name: "Erik Lindgren", role: "Developer", avatar: "https://i.pravatar.cc/150?img=2" },
  { name: "Sara Johansson", role: "Product Manager", avatar: "https://i.pravatar.cc/150?img=3" },
];
```

5. Rendera en `UserCard` för varje användare.

## Förväntat resultat

Tre profilkort som visar en rund bild, namn och roll. Varje component har ett ansvar: `Avatar` = bild, `UserInfo` = text, `UserCard` = sammansättning.

## Tips

<details>
<summary>Ledtråd 1</summary>

`UserCard` plockar isär `user`-objektet och skickar vidare delarna till rätt barn-component:

```jsx
function UserCard({ user }) {
  return (
    <Card>
      <Avatar src={user.avatar} alt={user.name} />
      <UserInfo name={user.name} role={user.role} />
    </Card>
  );
}
```

</details>

# Container och presentational components (Grund)

## Mål

Öva på att separera data-logik från presentation i olika components.

## Förkunskaper

- [Component patterns och komposition](../../documents/09-component-patterns.md)
- [useEffect och data fetching](../../documents/05-useeffect-data-fetching.md)

## Instruktioner

1. Skapa en **presentational** component `UserCard` som tar emot props: `name`, `email` och `phone`. Den renderar informationen men har ingen egen state eller side effects.
2. Skapa en **container** component `UserCardContainer` som:
   - Hämtar en användare från `https://jsonplaceholder.typicode.com/users/1`
   - Hanterar `loading` och `error` state
   - Renderar `<UserCard>` med den hämtade datan
3. Skapa en presentational component `UserList` som tar emot `users` (array) som prop och renderar en lista med namn och email.
4. Skapa en container `UserListContainer` som hämtar alla användare från `https://jsonplaceholder.typicode.com/users` och renderar `<UserList>`.
5. Rendera båda containers i `App.jsx`.

## Förväntat resultat

Fyra components: två containers som hämtar data, två presentational som visar data. Presentational components har inga hooks — de tar bara emot props.

## Tips

<details>
<summary>Ledtråd 1</summary>

Containern sköter all logik, presentational-componenten vet ingenting om fetch:

```jsx
function UserCardContainer() {
  const [user, setUser] = useState(null);
  const [loading, setLoading] = useState(true);

  useEffect(() => {
    async function fetchUser() {
      const res = await fetch("https://jsonplaceholder.typicode.com/users/1");
      const data = await res.json();
      setUser(data);
      setLoading(false);
    }
    fetchUser();
  }, []);

  if (loading) return <p>Laddar...</p>;
  return <UserCard name={user.name} email={user.email} phone={user.phone} />;
}
```

</details>

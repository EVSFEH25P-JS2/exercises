# Refaktorera en app (Extra)

## Mål

Öva på att identifiera problem i befintlig kod och förbättra den med component patterns.

## Förkunskaper

- Alla dokument och övningar från vecka 6

## Instruktioner

1. Kopiera koden nedan till `App.jsx`. Den fungerar, men all logik ligger i en enda component.
2. Identifiera problemen. Ledtrådar: duplicerad fetch-logik, en component som gör allt, ingen separation av ansvar.
3. Refaktorera steg för steg:
   - Extrahera en custom hook `useFetch(url)` som hanterar `data`, `loading` och `error`
   - Skapa en presentational component `UserList` som tar emot `users` via props
   - Skapa en presentational component `PostCard` för enskilda inlägg
   - Skapa en `SearchInput`-component för sökfältet
4. Organisera filerna i mappar: `hooks/`, `components/`.
5. `App.jsx` ska vara kort och tydlig efter refaktoreringen.

### Startkod

```jsx
import { useState, useEffect } from "react";

function App() {
  const [users, setUsers] = useState([]);
  const [usersLoading, setUsersLoading] = useState(true);
  const [usersError, setUsersError] = useState(null);
  const [posts, setPosts] = useState([]);
  const [postsLoading, setPostsLoading] = useState(true);
  const [postsError, setPostsError] = useState(null);
  const [search, setSearch] = useState("");

  useEffect(() => {
    async function fetchUsers() {
      try {
        const res = await fetch(
          "https://jsonplaceholder.typicode.com/users"
        );
        if (!res.ok) throw new Error("Fel");
        const data = await res.json();
        setUsers(data);
      } catch (err) {
        setUsersError(err.message);
      } finally {
        setUsersLoading(false);
      }
    }
    fetchUsers();
  }, []);

  useEffect(() => {
    async function fetchPosts() {
      try {
        const res = await fetch(
          "https://jsonplaceholder.typicode.com/posts?_limit=10"
        );
        if (!res.ok) throw new Error("Fel");
        const data = await res.json();
        setPosts(data);
      } catch (err) {
        setPostsError(err.message);
      } finally {
        setPostsLoading(false);
      }
    }
    fetchPosts();
  }, []);

  const filteredPosts = posts.filter((post) =>
    post.title.toLowerCase().includes(search.toLowerCase())
  );

  return (
    <div>
      <h1>Min app</h1>

      <h2>Användare</h2>
      {usersLoading && <p>Laddar användare...</p>}
      {usersError && <p>Fel: {usersError}</p>}
      <ul>
        {users.map((user) => (
          <li key={user.id}>
            <strong>{user.name}</strong> — {user.email}
          </li>
        ))}
      </ul>

      <h2>Inlägg</h2>
      <input
        value={search}
        onChange={(e) => setSearch(e.target.value)}
        placeholder="Sök inlägg..."
      />
      {postsLoading && <p>Laddar inlägg...</p>}
      {postsError && <p>Fel: {postsError}</p>}
      {filteredPosts.map((post) => (
        <div key={post.id}>
          <h3>{post.title}</h3>
          <p>{post.body}</p>
        </div>
      ))}
    </div>
  );
}

export default App;
```

## Förväntat resultat

Samma funktionalitet som innan, men koden är uppdelad i: en custom hook (`useFetch`), presentational components (`UserList`, `PostCard`, `SearchInput`) och en kort `App.jsx` som sätter ihop allt.

## Tips

<details>
<summary>Ledtråd 1</summary>

`useFetch` ersätter båda useEffect-blocken:

```jsx
function useFetch(url) {
  const [data, setData] = useState(null);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState(null);

  useEffect(() => {
    async function fetchData() {
      try {
        const res = await fetch(url);
        if (!res.ok) throw new Error("Fel");
        const json = await res.json();
        setData(json);
      } catch (err) {
        setError(err.message);
      } finally {
        setLoading(false);
      }
    }
    fetchData();
  }, [url]);

  return { data, loading, error };
}
```

</details>

<details>
<summary>Ledtråd 2</summary>

Refaktorerad `App.jsx`:

```jsx
function App() {
  const { data: users, loading: usersLoading, error: usersError } =
    useFetch("https://jsonplaceholder.typicode.com/users");
  const { data: posts, loading: postsLoading, error: postsError } =
    useFetch("https://jsonplaceholder.typicode.com/posts?_limit=10");
  const [search, setSearch] = useState("");

  const filteredPosts = (posts || []).filter((post) =>
    post.title.toLowerCase().includes(search.toLowerCase())
  );

  return (
    <div>
      <h1>Min app</h1>
      <UserList users={users || []} loading={usersLoading} error={usersError} />
      <SearchInput value={search} onChange={setSearch} />
      <PostList posts={filteredPosts} loading={postsLoading} error={postsError} />
    </div>
  );
}
```

</details>

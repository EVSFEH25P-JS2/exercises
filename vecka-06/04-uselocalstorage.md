# Custom hook — useLocalStorage (Utmaning)

## Mål

Bygga en egen hook som fungerar som `useState` men sparar data i localStorage.

## Förkunskaper

- [Component patterns och komposition](../../documents/09-component-patterns.md)
- [Custom hook](01-custom-hook.md)

## Instruktioner

1. Skapa en hook `useLocalStorage` i `src/hooks/useLocalStorage.js`.
2. Hooken tar emot `key` (sträng) och `initialValue`.
3. Vid initialisering: kolla om det finns ett sparat värde i `localStorage.getItem(key)`. Om ja, använd det (JSON.parse). Om nej, använd `initialValue`.
4. Returnera `[value, setValue]` precis som `useState`.
5. Varje gång `value` ändras, spara det i localStorage med `localStorage.setItem(key, JSON.stringify(value))`.
6. Testa hooken i en component som sparar ett tema ("light"/"dark"):
   - En knapp som togglar temat
   - Temat ska finnas kvar efter att sidan laddas om
7. Testa med en todo-lista — todos ska finnas kvar efter omladdning.

## Förväntat resultat

En hook som fungerar som `useState` men persistent. Data finns kvar efter page refresh. Hooken kan användas med vilken datatyp som helst (strängar, objekt, arrayer).

## Tips

<details>
<summary>Ledtråd 1</summary>

Initiera state med en funktion (lazy initialization) för att bara läsa localStorage en gång:

```jsx
const [value, setValue] = useState(() => {
  const stored = localStorage.getItem(key);
  return stored !== null ? JSON.parse(stored) : initialValue;
});
```

</details>

<details>
<summary>Ledtråd 2</summary>

Synka till localStorage med `useEffect`:

```jsx
useEffect(() => {
  localStorage.setItem(key, JSON.stringify(value));
}, [key, value]);
```

</details>

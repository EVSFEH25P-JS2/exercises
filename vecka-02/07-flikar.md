# Flikar (Grund)

## Mål

Öva på att använda state för att styra vilken content som visas, och göra components återanvändbara via props.

## Förkunskaper

- [State och events](../../documents/03-state-events.md)
- [Components och props](../../documents/02-components-props.md)

## Instruktioner

1. Skapa en component `Tabs`.
2. Definiera en array med minst tre objekt, varje med `label` (flikens rubrik) och `content` (flikens text). Skicka in arrayen som en prop till `Tabs`.
3. Skapa state `activeIndex` som håller koll på vilken flik som är vald (börja med `0`).
4. Rendera en knapp för varje flik med flikens `label` som text.
5. Klick på en knapp sätter `activeIndex` till den flikens index.
6. Under knapparna, visa `content` för den aktiva fliken.
7. Ge den aktiva flikknappen en CSS-klass `"active"` som skiljer den visuellt.
8. Rendera `Tabs` i `App.jsx` med din data.
9. **Testa återanvändbarhet:** Rendera en andra `Tabs`-component i `App.jsx` med annan data (t.ex. FAQ-frågor eller receptsteg). Båda ska fungera oberoende av varandra.

## Förväntat resultat

Två separata flik-grupper på sidan. Varje grupp har knappar i rad — klick på en flik visar dess content och markerar knappen som aktiv. Varje grupp har sin egen aktiva flik, oberoende av den andra.

## Tips

<details>
<summary>Ledtråd 1</summary>

Skicka in flikarna som en prop:

```jsx
const tabs = [
  { label: "Hem", content: "Välkommen till startsidan!" },
  { label: "Om", content: "Vi är ett litet team som gillar React." },
  { label: "Kontakt", content: "Maila oss på info@example.com" },
];

<Tabs tabs={tabs} />
```

</details>

<details>
<summary>Ledtråd 2</summary>

Rendera knapparna med `.map()` och jämför index med `activeIndex`:

```jsx
function Tabs({ tabs }) {
  const [activeIndex, setActiveIndex] = useState(0);

  return (
    <div>
      <div className="tab-buttons">
        {tabs.map((tab, index) => (
          <button
            key={index}
            className={activeIndex === index ? "active" : ""}
            onClick={() => setActiveIndex(index)}
          >
            {tab.label}
          </button>
        ))}
      </div>
      <div className="tab-content">
        <p>{tabs[activeIndex].content}</p>
      </div>
    </div>
  );
}
```

</details>

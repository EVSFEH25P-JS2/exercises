# Code review i grupp (Grund)

## Mål

Öva på att läsa, förstå och ge konstruktiv feedback på andras React-kod.

## Förkunskaper

- Alla tidigare ämnen i kursen

## Instruktioner

### Förberedelse (5 min)

1. Dela in er i grupper om 3-4 personer.
2. Varje person väljer en av sina lösningar att visa: **todo-listan** (vecka 2, övning 06) eller **formulär med lista** (vecka 3, övning 05).

### Granska (~10 min per person)

3. En person delar sin skärm och visar sin kod.
4. Den som visar: gå kort igenom din lösning utan att förklara allt i detalj. Låt koden tala.
5. De andra granskar koden och ger feedback inom fyra områden:
   - **Struktur:** Är components uppdelade på ett bra sätt? Har varje component ett tydligt ansvar?
   - **Namngivning:** Är variabelnamn, funktionsnamn och component-namn tydliga och beskrivande?
   - **State:** Ligger state på rätt ställe? Finns det onödig state eller duplicerad data?
   - **Vanliga misstag:** Saknas `key` i listor? Muteras state direkt? Saknas error handling?

6. Skriv ner minst **två saker som var bra** och **en sak som kan förbättras** för varje persons kod.

### Diskussion (10 min)

7. Diskutera i gruppen: var det något som någon löste på ett helt annat sätt? Vilket sätt föredrar ni och varför?
8. Fanns det vanliga mönster som dök upp i allas lösningar?

## Förväntat resultat

Varje person har fått skriftlig feedback (minst 2 positiva + 1 förbättring) och sett minst två andra lösningar. Gruppen har diskuterat skillnader i approach.

## Tips

<details>
<summary>Exempel på bra vs vag feedback</summary>

**Vagt (undvik):**
- "Koden ser bra ut"
- "Det kunde vara bättre"

**Specifikt (bra):**
- "Bra att du använder functional update i `setTodos` — det är säkrare vid snabba uppdateringar"
- "Variabeln `d` i `.map()` kunde heta `todo` för att göra koden lättare att läsa"
- "Du har `isValid` som state, men det kan beräknas direkt från `name.length > 0` — du behöver inte en extra state-variabel för det"

</details>

<details>
<summary>Vanliga saker att titta efter</summary>

- Används `key` korrekt i listor? (inte `index` om listan ändras)
- Muteras state direkt med `.push()` eller `.splice()`?
- Finns det state som egentligen kan beräknas från annan state? (onödig state)
- Är component-filer uppdelade eller ligger allt i `App.jsx`?
- Används functional update (`prev => ...`) vid state som beror på tidigare värde?
- Är funktionsnamn beskrivande? (`handleAdd` vs `doStuff`)

</details>

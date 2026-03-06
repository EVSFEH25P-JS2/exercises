# Formulär — controlled components (Grund)

## Mål

Öva på att bygga formulär med controlled components och hantera submit.

## Förkunskaper

- [Formulär och controlled components](../../documents/06-formular-controlled-components.md)

## Instruktioner

1. Skapa en component `ContactForm`.
2. Skapa state-variabler för `name`, `email` och `message` (alla tomma strängar).
3. Rendera ett formulär med:
   - Text-input för namn
   - Email-input för e-post
   - Textarea för meddelande
   - En "Skicka"-knapp
4. Koppla varje fält till sin state-variabel med `value` och `onChange`.
5. Lägg till en `onSubmit`-handler på `<form>`. Använd `e.preventDefault()`.
6. Vid submit: logga formulärdatan till konsolen och töm alla fält.
7. Lägg till enkel validering: om namn eller e-post är tomt vid submit, visa ett felmeddelande och avbryt.

## Förväntat resultat

Ett formulär där du ser det du skriver i realtid (controlled). Vid submit loggas datan och fälten töms. Om namn eller e-post saknas visas ett felmeddelande.

## Tips

<details>
<summary>Ledtråd 1</summary>

```jsx
function handleSubmit(e) {
  e.preventDefault();

  if (name.trim() === "" || email.trim() === "") {
    setError("Namn och e-post krävs");
    return;
  }

  console.log({ name, email, message });
  setName("");
  setEmail("");
  setMessage("");
  setError("");
}
```

</details>

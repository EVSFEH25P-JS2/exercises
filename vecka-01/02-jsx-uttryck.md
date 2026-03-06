# JSX-uttryck (Grund)

## Mål

Öva på att använda JavaScript-uttryck inuti JSX med `{}`.

## Förkunskaper

- [Introduktion till React och JSX](../../documents/01-introduktion-react-jsx.md)
- [Skapa en React-app](01-skapa-react-app.md)

## Instruktioner

1. I `App.jsx`, skapa en variabel `name` med ditt namn.
2. Skapa en variabel `birthYear` med ditt födelseår.
3. Rendera ditt namn i en `<h1>` med `{}`.
4. Beräkna din ålder med `new Date().getFullYear() - birthYear` och visa resultatet i en `<p>`.
5. Skapa en array `hobbies` med minst tre strängar.
6. Visa antal hobbies i en `<p>`: "Jag har X hobbies".
7. Skapa ett objekt `address` med `city` och `country`. Visa stad och land i en `<p>`.

## Förväntat resultat

Sidan visar ditt namn, din beräknade ålder, antal hobbies och din adress — allt renderat dynamiskt med `{}`.

## Tips

<details>
<summary>Ledtråd 1</summary>
Alla JavaScript-uttryck funkar inuti `{}`: variabler, beräkningar, `array.length`, `object.property`.
</details>

<details>
<summary>Ledtråd 2</summary>
Du kan inte rendera ett objekt direkt i JSX — plocka ut enskilda egenskaper: `{address.city}`.
</details>

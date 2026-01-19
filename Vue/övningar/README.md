# Vue.js Övningar

Praktiska övningar för att träna Vue.js 3-koncept. Varje övning är kopplad till motsvarande avsnitt i [huvudguiden](../README.md).

**Utmaning:** För mer avancerade projektidéer, se [Vue.js Practice Project Ideas](https://rojas.io/vue-js-practice-project-ideas/)

---

## Grundläggande Övningar (0.x)

### Övning 0 - Projekt Setup
Skapa ett nytt Vue-projekt med Vue CLI (via kommandofönstret). Se beskrivningen i [README.md](../README.md) för instruktioner.

**Tips:** Du kan göra övningarna 0.1-0.11 i `App.vue`-komponenten. Alternativt kan du skapa ett Quasar Framework-projekt och arbeta i `pages/IndexPage.vue`.

---

### Övning 0.1 - Interpolation
**Relaterat till:** [1.2 Interpolation](../README.md#12-interpolation-declarative-rendering)

**Uppgift:**
1. Skapa en data-variabel `message` med värdet `"Hello Vue!"` och visa värdet i HTML-koden genom interpolering `{{ }}`.
2. Skapa fler variabler med olika typer (sträng, siffra, boolean) och visa dem.

**Tips:** Använd mustache-syntax `{{ variabel }}` för att visa data.

---

### Övning 0.2 - Attribute Binding
**Relaterat till:** [1.3 Attribute Binding](../README.md#13-attribute-binding)

**Uppgift:**
1. Skapa en data-variabel `link` med värdet på en valfri YouTube-video.
2. Skapa en `<a>`-tagg som binder till `link`-variabeln med `v-bind` eller `:`. Verifiera att länken fungerar.
3. Skapa en data-variabel `image` med värdet på en bild-URL från nätet.
4. Skapa en `<img>`-tagg vars `src`-attribut binder till `image`-variabeln.

---

### Övning 0.3 - Villkorlig Rendering
**Relaterat till:** [1.6 Villkorlig Rendering](../README.md#16-villkorlig-rendering)

**Uppgift:**
1. Skapa en data-variabel `age` med ett åldersvärde (du väljer själv).
2. Använd `v-if`-direktivet för att kontrollera om `age` är större än 18.
   - Om villkoret stämmer: visa texten "Du får ta körkort!"
   - Annars: visa texten "Tyvärr du får inte ta körkort!"

**Tips:** Använd `<p v-if="age > 18">...</p>` och `<p v-else>...</p>`.

---

### Övning 0.4 - List Rendering
**Relaterat till:** [1.7 List Rendering](../README.md#17-list-rendering)

**Uppgift:**
1. Skapa en data-variabel som är en lista med talen 1 till 10.
2. Använd `v-for`-direktivet för att loopa igenom listan och skriv ut talen med interpolering i en oordnad lista (`<ul>`/`<li>`).

**Tips:** Använd `<li v-for="num in numbers" :key="num">{{ num }}</li>`.

---

### Övning 0.5 - API-anrop (Ett objekt)
**Relaterat till:** [1.9 Lifecycle & Template Refs](../README.md#19-lifecycle--template-refs)

**Uppgift:**
1. Skapa en variabel `photo` som är `null` från början.
2. I `onMounted()`-metoden gör ett API-anrop med `fetch()` som hämtar ett photo-objekt och tilldelar det till `photo`-variabeln.

```js
onMounted(() => {
  // Ditt fetch-anrop här
})
```

**API-endpoint:** [https://jsonplaceholder.typicode.com/photos/1](https://jsonplaceholder.typicode.com/photos/1)

3. Presentera photo-objektets värden i HTML med interpolation.

---

### Övning 0.6 - API-anrop (Lista av objekt)
**Relaterat till:** [1.7 List Rendering](../README.md#17-list-rendering) & [1.9 Lifecycle](../README.md#19-lifecycle--template-refs)

**Uppgift:**
1. Skapa en variabel `photos` som är `null` från början.
2. I `onMounted()`-metoden gör ett API-anrop med `fetch()` som hämtar en lista med photos och tilldelar den till `photos`-variabeln.

```js
onMounted(() => {
  // Ditt fetch-anrop här
})
```

**API-endpoint:** [https://jsonplaceholder.typicode.com/photos](https://jsonplaceholder.typicode.com/photos)

3. Presentera photos med `v-for` i HTML.

---

### Övning 0.7 - Eventhantering
**Relaterat till:** [1.4 Event Handlers](../README.md#14-event-handlers)

**Uppgift:**
1. Skapa en data-variabel `name` med ditt förnamn. Visa namnet med interpolering.
2. Skapa en knapp med texten "Byt namn".
3. Koppla ett klick-event (`@click` eller `v-on:click`) som kör en metod som uppdaterar `name` till ditt efternamn.

**Tips:** Skapa en metod `changeName()` och använd `@click="changeName"`.

---

### Övning 0.8 - Tvåvägsbinding (v-model)
**Relaterat till:** [1.5 Tvåvägsbinding](../README.md#15-tvåvägsbinding-form-bindings)

**Uppgift:**
1. Skapa två data-variabler: `firstName` och `lastName`.
2. Skapa två input-fält som har tvåvägsbinding med `v-model` till respektive variabel.
3. Visa förnamn och efternamn brevid varandra med interpolering: `{{ firstName }} {{ lastName }}`.

---

### Övning 0.9 - Computed Properties & Watchers
**Relaterat till:** [1.8 Computed Properties](../README.md#18-computed-properties) & [1.10 Watchers](../README.md#110-watchers)

**Uppgift:**
Skapa exemplen på Computed Properties och Watchers från PowerPoint-presentationen och försök förstå vad de gör.

---

### Övning 0.10 - Class Binding
**Relaterat till:** [Style Binding](#övning-5---style-bindning)

**Uppgift:**
1. Skapa en `div`.
2. Skapa två CSS-klasser i `<style>`-taggen:
   - `green-background` (bakgrundsfärg: grön)
   - `red-background` (bakgrundsfärg: röd)

Båda ska ha:
```css
width: 200px;
height: 200px;
```

3. Skapa en variabel `isGreen` som bestämmer vilken klass som appliceras.
4. Använd class-binding (`:class`) för att binda rätt klass till diven.
5. Skapa en knapp som ändrar `isGreen` och därmed klassen.

---

### Övning 0.11 - Style Binding
**Relaterat till:** [Style Binding](#övning-5---style-bindning)

**Uppgift:**
Skapa exemplen på Style Binding från PowerPoint-presentationen och försök förstå vad de gör.

## Komponenter & Avancerade Övningar

---

### Övning 1 - Hello From Group X
**Relaterat till:** [1.11 Components](../README.md#111-components)

**Uppgift:**
I en valfri komponent i projektet:
1. Skapa en rubrik med texten "Hello From Group X" (ersätt X med ditt gruppnummer).
2. Skapa en lista med namnen på alla gruppmedlemmar i din basgrupp.
3. Både rubriken och listan ska deklareras som Vue data-variabler.

---

### Övning 1.1 - Formulär
**Relaterat till:** [1.5 Tvåvägsbinding](../README.md#15-tvåvägsbinding-form-bindings)

**Uppgift:**
1. Skapa 4 input-fält för: address, postnummer, stad och land.
2. Skapa 4 variabler i data-sektionen för att spara det som matas in.
3. Skapa en knapp som visar det som matats in i en `alert()`.

---

### Övning 1.2 - Flera komponenter
**Relaterat till:** [1.11 Components](../README.md#111-components)

**Uppgift:**
1. Skapa 4 input-fält för address, postnummer, stad och land.
2. Organisera koden i separata komponenter.

---

### Övning 2 - Data-bunden komponent (Event Details)
**Relaterat till:** [1.11 Components](../README.md#111-components) & [1.2 Interpolation](../README.md#12-interpolation-declarative-rendering)

**Uppgift:**
Skapa en komponent för att visa ett lektions-event.

**Steg:**
1. Skapa komponenten `EventDetailsComponent` (eller lägg koden direkt i `App`-komponenten).
2. Skapa en variabel i data-sektionen för att hålla event-datat.
3. Lägg till data-bindningar (interpolation) i template-delen.
4. Importera och använd komponenten i `App`-komponenten.

**Start-HTML för template:**
```html
<div>
  <h1>Event:</h1>
  <div>Date:</div>
  <div>Time:</div>
  <div>Address:</div>
</div>
```

**Event-data:**
```js
{
  name: 'Smarta System 2020',
  date: '24/8/2020',
  time: '13:00',
  location: {
    address: 'Robotvägen 4',
    zipcode: '721 36',
    city: 'Västerås',
    country: 'Sverige'
  }
}
```

**Förväntat resultat:**
- **Event:** Smarta System 2020
- **Date:** 24/8/2020
- **Time:** 13:00
- **Address:** Robotvägen 4, 721 36 Västerås, Sverige

---

### Övning 2.2 - API-data presentation
**Relaterat till:** [1.9 Lifecycle](../README.md#19-lifecycle--template-refs) & [1.7 List Rendering](../README.md#17-list-rendering)

**Uppgift:**
Använd tjänsten JSON Placeholder för att göra API-anrop och hämta valfri data och presentera den.

**Resurser:**
- [JSON Placeholder API](https://jsonplaceholder.typicode.com/)

---

### Övning 3 - Props (Parent → Child)
**Relaterat till:** [1.12 Props - Komponentkommunikation](../README.md#112-props---komponentkommunikation-parent--child)

**Uppgift:**
`EventDetailsComponent` visar information om ett lektions-event inklusive adress. Skapa en ny child-komponent som visar adressen.

**Steg:**
1. Skapa en ny adress-komponent som tar in adress-data som **prop**.
2. Uppdatera `EventDetailsComponent` att inkludera adress-komponenten och skicka in adress-delen av event-datat.

**⚠️ Viktigt:** Namnge inte din komponent `<address>`. `<address>` är redan ett HTML5-element. Använd ett namn som `AddressDisplay` eller `EventAddress`.

**Förväntat resultat:** Samma som i övning 2, men med adressen i en separat komponent.

---

### Övning 4 - Emit Events (Child → Parent)
**Relaterat till:** [1.13 Emit Events - Komponentkommunikation](../README.md#113-emit-events---komponentkommunikation-child--parent)

**Uppgift:**
Utöka adress-komponenten från övning 3 med funktionalitet att uppdatera adressen.

**Steg:**
1. Skapa 4 `<input>`-element och 4 `<button>`-element i adress-komponenten.
2. Genom **Child → Parent**-kommunikation (emit events): när användaren fyllt i ett fält och klickar på motsvarande knapp, ska adressen uppdateras för den delen i `EventDetailsComponent`.

**Förväntat resultat:**
![överblick](./SmartaSystemExercise4.PNG)

---

### Övning 5 - Style Binding
**Relaterat till:** [1.3 Attribute Binding](../README.md#13-attribute-binding)

**Uppgift:**
1. Skapa ett `<input>`-element bredvid titeln på sidan.
2. Använd tvåvägsbinding med `v-model` för att koppla värdet från fältet till en data-variabel `titleColor`.
3. Använd style-binding (`:style`) så att titelns färg ändras till den färg som matats in.

**Förväntat resultat:**
![överblick](./style-binding.PNG)

---

### Övning 6 - Watcher
**Relaterat till:** [1.10 Watchers](../README.md#110-watchers)

**Uppgift:**
1. Skapa en **watcher** på `titleColor` data-variabeln som skriver ut "Jippy min favoritfärg!" i konsolen när färgen ändras.

**Tips:** Använd `watch()` i Composition API.

**Förväntat resultat:**
![överblick](./watcher.PNG)

---

### Övning 7 - v-if direktivet (Villkorlig rendering)
**Relaterat till:** [1.6 Villkorlig Rendering](../README.md#16-villkorlig-rendering)

**Uppgift:**
1. Applicera `v-if`-direktivet så att titeln inte syns om färgen är **"brown"**.

**Förväntat resultat:**
![överblick](./v-if-brown.PNG)

---

### Övning 8 - Class Binding & Computed Property
**Relaterat till:** [1.8 Computed Properties](../README.md#18-computed-properties)

**Uppgift:**
1. Använd en **computed property** för att hålla koll på om färgen är **"brown"** (t.ex. `isBrown`).
2. Applicera class-binding med hjälp av `isBrown` så att all text blir brun.

**Tips:** Du måste skapa en CSS-klass i `<style>`-taggen som gör texten brun.

**Förväntat resultat:**
![överblick](./isBrown.PNG)

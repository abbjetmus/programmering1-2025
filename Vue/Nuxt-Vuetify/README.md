# Vuetify

Vuetify är ett Material Design-komponentbibliotek för Vue.js som förenklar utvecklingen av moderna och responsiva webbapplikationer.

## Resurser

[Vuetify Documentation](https://vuetifyjs.com/en/)
[Vuetify YouTube Tutorial](https://www.youtube.com/watch?v=AptYLMzTrns)

# Skapa ett Nuxt-Vuetify Projekt

För att komma igång snabbt med Nuxt och Vuetify, använd det färdiga templatet som redan är uppsatt:

## Klona template-repot

```bash
# Klona repot
git clone https://github.com/abbjetmus/Nuxt-Vuetify-Template.git

# Gå in i projektmappen
cd Nuxt-Vuetify-Template

# Installera beroenden
npm install

# Starta utvecklingsservern
npm run dev
```

Nu kan du öppna projektet i din webbläsare på `http://localhost:3000`

## Öppna projekt i Visual Studio Code

```bash
# Öppna projektet i VS Code
code .
```

## Projektstruktur

När du öppnar projektet i Visual Studio Code ser mappstrukturen ut ungefär så här:

```
nuxt-vuetify-template/
├── assets/
├── components/
├── layouts/
├── pages/
├── plugins/
├── public/
├── server/
├── app.vue
├── nuxt.config.ts
└── package.json
```

### Huvudmappar

#### `assets/`
Webbplatsens tillgångar som build-verktyget (Vite eller webpack) kommer att bearbeta. Här lägger du bilder, CSS/SCSS-filer och andra statiska resurser som ska processas.

#### `components/`
Vue-komponenter för din applikation. Komponenter i denna mapp blir automatiskt tillgängliga i hela applikationen tack vare Nuxt's auto-import funktionalitet.

#### `composables/`
Lägg till dina Vue composables här. Composables är återanvändbara funktioner som använder Vue's Composition API och blir automatiskt tillgängliga i hela applikationen.

#### `layouts/`
Vue-komponenter som omsluter dina sidor och undviker re-rendering mellan sidbyten. Till exempel kan `layouts/default.vue` användas som standardlayout för alla sidor.

#### `middleware/`
Kör kod innan du navigerar till en specifik route. Användbart för autentisering, behörighetskontroller, eller andra kontroller innan en sida laddas.

#### `pages/`
Filbaserad routing för att skapa routes i din webbapplikation. Nuxt skapar automatiskt routes baserat på filstrukturen:
- `pages/index.vue` → `/`
- `pages/about.vue` → `/about`
- `pages/users/index.vue` → `/users`
- `pages/users/[id].vue` → `/users/:id` (dynamisk route)

#### `plugins/`
Använd Vue plugins och mer vid skapandet av din Nuxt-applikation. Här konfigureras Vuetify och andra tredjepartsbibliotek.

#### `utils/`
Lägg till funktioner som kan användas i hela applikationen - i komponenter, composables och pages.

### Viktiga filer

#### `app.vue`
Rotkomponenten för din Nuxt-applikation. Detta är utgångspunkten för hela din app.

#### `nuxt.config.ts`
Huvudkonfigurationsfilen för Nuxt-applikationen. Här konfigureras moduler, plugins, build-inställningar med mera.

#### `error.vue`
Felsidan för din Nuxt-applikation. Visas när ett fel uppstår.

### Övriga mappar

#### `public/`
Innehåller publika filer som serveras i root och inte modifieras av build-processen. Lämpligt för filer som måste behålla sina namn (t.ex. `robots.txt`) eller sannolikt inte kommer att ändras (t.ex. `favicon.ico`).

#### `server/`
Innehåller server-side kod för Nuxt-applikationen:
- `server/api/` - API routes för applikationen
- `server/routes/` - Server routes (t.ex. dynamisk `/sitemap.xml`)
- `server/middleware/` - Kör kod innan en server route processas
- `server/utils/` - Funktioner som kan användas i server-koden

## Ny fil i pages

När du skapar en ny sida i Nuxt använd den här mallen. Sidan ska ligga i pages-mappen.
Nuxt skapar automatiskt routes baserat på filnamnet.

```vue
<template>
  <v-container>
    <v-row>
      <v-col>
        <!-- Ditt innehåll här -->
      </v-col>
    </v-row>
  </v-container>
</template>

<script setup>
const title = ref('Min Sida')
</script>
```

Exempel på filnamn och deras routes:
- `pages/index.vue` → `/`
- `pages/about.vue` → `/about`
- `pages/users/index.vue` → `/users`
- `pages/users/[id].vue` → `/users/:id` (dynamisk route)

## Ny fil i components

När du skapar en ny komponent i Vuetify använd den här mallen. Komponenten ska ligga i components-mappen.

```vue
<template>
  <!-- Ditt innehåll här -->
</template>

<script setup>
import { ref } from 'vue'
</script>
```

## Inkludera Firebase i Nuxt

För att använda Firebase i ditt Nuxt-projekt:

1. Installera Firebase och VueFire:

```bash
npm install firebase vuefire
```

2. Skapa en Nuxt plugin `plugins/firebase.client.ts`:

```ts
import { VueFire, VueFireAuth } from 'vuefire'
import { initializeApp } from 'firebase/app'

export default defineNuxtPlugin((nuxtApp) => {
  const firebaseConfig = {
    apiKey: "DIN_API_KEY",
    authDomain: "DIN_AUTH_DOMAIN",
    databaseURL: "DIN_DATABASE_URL",
    projectId: "DITT_PROJECT_ID",
    storageBucket: "DIN_STORAGE_BUCKET",
    messagingSenderId: "DITT_MESSAGING_SENDER_ID",
    appId: "DITT_APP_ID"
  }

  const firebaseApp = initializeApp(firebaseConfig)

  nuxtApp.vueApp.use(VueFire, {
    firebaseApp,
    modules: [VueFireAuth()]
  })
})
```

3. Skapa en composable `composables/useFirebase.ts` för enkel åtkomst:

```ts
import { getDatabase } from 'firebase/database'
import { getApp } from 'firebase/app'

export const useFirebase = () => {
  const app = getApp()
  const db = getDatabase(app)

  return {
    db
  }
}
```

## Övning 0. Skapa ett nytt Vuetify projekt

1. Skapa ett nytt Vuetify projekt enligt instruktionerna ovan.
2. Öppna sedan projektet i webbläsaren.
3. Bekanta dig med mapparna innanför **src**-mappen.

## Övning 1. Importera en komponent till en page

1. Skapa en komponent som heter `MyCardComponent.vue` i components-mappen som innehåller ett valfritt card som du hämtar från [Vuetify Cards](https://vuetifyjs.com/en/components/cards/).
2. Importera sedan MyCardComponent till en av dina pages och använd det i template-delen.

**OBS:** I Nuxt 3 med auto-imports behöver du inte importera komponenter manuellt - de blir automatiskt tillgängliga!

## Övning 2.1 Grid System i Vuetify

[Vuetify Grid System](https://vuetifyjs.com/en/components/grids/)

Vuetify använder ett 12-kolumners grid-system med Material Design breakpoints.

1. Använd `<v-container>` som innehåller `<v-row>` som i sin tur innehåller 3 `<v-col>` med siffrorna 1-3.
2. Testa sedan Vuetifys flexbox-klasser för att placera kolumnerna:

```vue
<template>
  <v-container>
    <v-row justify="center">
      <v-col cols="4">1</v-col>
      <v-col cols="4">2</v-col>
      <v-col cols="4">3</v-col>
    </v-row>
  </v-container>
</template>
```

Testa olika props:
- `justify="center"`
- `justify="space-between"`
- `align="center"`
- `justify="end"`

## Övning 2.2 Responsiv Layout med Grid

I den här uppgiften ska ni använda Vuetifys grid-system för att skapa en responsiv layout.

[Vuetify Grid System](https://vuetifyjs.com/en/components/grids/)

```vue
<template>
  <v-container>
    <v-row>
      <v-col cols="12" md="6" lg="4">
        <!-- Innehåll -->
      </v-col>
      <v-col cols="12" md="6" lg="4">
        <!-- Innehåll -->
      </v-col>
      <v-col cols="12" md="6" lg="4">
        <!-- Innehåll -->
      </v-col>
    </v-row>
  </v-container>
</template>
```

## Övning 3. Jobba med färger i Vuetify

Vuetify har ett omfattande färgsystem baserat på Material Design.

[Vuetify Colors](https://vuetifyjs.com/en/styles/colors/)

Testa att använda färgklasser:

```vue
<template>
  <v-container>
    <v-card class="bg-primary">
      <v-card-text class="text-white">Primary Color</v-card-text>
    </v-card>

    <v-btn color="secondary">Secondary Button</v-btn>

    <v-sheet class="bg-error text-white pa-4">
      Error Color
    </v-sheet>
  </v-container>
</template>
```

Testa olika färger:
- `primary`
- `secondary`
- `success`
- `error`
- `warning`
- `info`

## Övning 4. Typografi i Vuetify

Använd Vuetifys typografi-klasser för att styla text.

[Vuetify Typography](https://vuetifyjs.com/en/styles/text-and-typography/)

```vue
<template>
  <v-container>
    <h1 class="text-h1">Heading 1</h1>
    <h2 class="text-h2">Heading 2</h2>
    <h3 class="text-h3">Heading 3</h3>
    <p class="text-body-1">Body text 1</p>
    <p class="text-body-2">Body text 2</p>
    <p class="text-caption">Caption text</p>

    <p class="text-center">Centered text</p>
    <p class="font-weight-bold">Bold text</p>
    <p class="font-italic">Italic text</p>
  </v-container>
</template>
```

## Övning 5. Spacing (Margin och Padding) i Vuetify

Vuetify använder ett enhetligt spacing-system.

[Vuetify Spacing](https://vuetifyjs.com/en/styles/spacing/)

Format: `{property}{direction}-{size}`

- Property: `m` (margin) eller `p` (padding)
- Direction: `t` (top), `b` (bottom), `l` (left), `r` (right), `x` (horizontal), `y` (vertical), `a` (all)
- Size: `0` till `16` (varje steg är 4px)

```vue
<template>
  <v-container>
    <v-card class="ma-4">Margin all sides 16px</v-card>
    <v-card class="pa-8">Padding all sides 32px</v-card>
    <v-card class="mt-4 mb-2">Margin top 16px, bottom 8px</v-card>
    <v-card class="px-6 py-3">Padding horizontal 24px, vertical 12px</v-card>
  </v-container>
</template>
```

## Övning 6.1 Ny sida (Page) och navigering

[Nuxt Routing Guide](https://nuxt.com/docs/getting-started/routing)

1. Skapa en ny sida som du döper `my-test.vue` innanför pages-mappen.
2. Nuxt skapar automatiskt en route `/my-test` för denna fil - ingen manuell konfiguration behövs!
3. Använd `<NuxtLink>` eller Vuetify-komponenter för navigering:

```vue
<template>
  <v-container>
    <NuxtLink to="/my-test">Go to My Test</NuxtLink>

    <!-- Eller med Vuetify button -->
    <v-btn to="/my-test">Go to My Test</v-btn>
  </v-container>
</template>
```

**Nuxt File-based Routing:**
- `pages/index.vue` → `/`
- `pages/my-test.vue` → `/my-test`
- `pages/about.vue` → `/about`

## Övning 6.2 Navigering från JavaScript

1. Skapa en knapp i din page.
2. Koppla knappen till en funktion som navigerar programmatiskt.

**Alternativ 1: Med navigateTo() (Rekommenderad i Nuxt)**
```vue
<template>
  <v-container>
    <v-btn @click="goToMyTest">Go to My Test</v-btn>
  </v-container>
</template>

<script setup>
const goToMyTest = () => {
  navigateTo('/my-test')
}
</script>
```

**Alternativ 2: Med useRouter()**
```vue
<template>
  <v-container>
    <v-btn @click="goToMyTest">Go to My Test</v-btn>
  </v-container>
</template>

<script setup>
const router = useRouter()

const goToMyTest = () => {
  router.push('/my-test')
}
</script>
```

## Övning 6.3 Navigera med params till en detaljerad sida

1. Skapa en sida som heter `pages/users/index.vue`:

```vue
<script setup>
const { data: users } = await useFetch('https://jsonplaceholder.typicode.com/users')
</script>

<template>
  <v-container>
    <v-list>
      <v-list-item
        v-for="user in users"
        :key="user.id"
        :to="`/users/${user.id}`"
      >
        <v-list-item-title>{{ user.name }}</v-list-item-title>
      </v-list-item>
    </v-list>
  </v-container>
</template>
```

2. Skapa en dynamisk route genom att skapa `pages/users/[id].vue`:

```vue
<script setup>
const route = useRoute()
const { data: user } = await useFetch(
  `https://jsonplaceholder.typicode.com/users/${route.params.id}`
)
</script>

<template>
  <v-container v-if="user">
    <v-card>
      <v-card-title>{{ user.name }}</v-card-title>
      <v-card-text>
        <p>Email: {{ user.email }}</p>
        <p>Phone: {{ user.phone }}</p>
      </v-card-text>
      <v-card-actions>
        <v-btn to="/users">Tillbaka till alla användare</v-btn>
      </v-card-actions>
    </v-card>
  </v-container>
</template>
```

**Filstruktur:**
```
pages/
├── users/
│   ├── index.vue  → /users
│   └── [id].vue   → /users/:id (dynamisk)
```

Nuxt skapar automatiskt routes baserat på filstrukturen - ingen manuell konfiguration behövs!

## Övning 7. Vuetify - VueFire - Firebase

VueFire är ett JavaScript-paket som förenklar användandet av Firebase i Vue.

[VueFire Documentation](https://vuefire.vuejs.org/guide/getting-started.html)

Viktigt att använda Realtime Database-exemplen och inte Firestore, då vi använder Realtime Database.

## Övning 7.1 Läsa från Firebase

1. Gå igenom sektionen `Inkludera Firebase i Nuxt` ovan.
2. Koppla databasen till ert Firebase-projekt.
3. I en page, hämta data från Firebase:

```vue
<script setup>
import { useDatabase, useDatabaseList } from 'vuefire'
import { ref as dbRef } from 'firebase/database'

const db = useDatabase()
const todos = useDatabaseList(dbRef(db, 'todos'))
</script>

<template>
  <v-container>
    <v-list>
      <v-list-item v-for="todo in todos" :key="todo.id">
        <v-list-item-title>{{ todo.text }}</v-list-item-title>
      </v-list-item>
    </v-list>
  </v-container>
</template>
```

## Övning 7.2 Skapa ett formulär och skicka data till Firebase

1. Skapa ett formulär för en todo:

```vue
<script setup>
import { ref } from 'vue'
import { useDatabase } from 'vuefire'
import { ref as dbRef, push } from 'firebase/database'

const db = useDatabase()
const todoText = ref('')
const todoId = ref(0)

const sendTodo = async () => {
  const todosRef = dbRef(db, 'todos')
  await push(todosRef, {
    id: todoId.value,
    text: todoText.value
  })

  // Reset form
  todoText.value = ''
  todoId.value++
}
</script>

<template>
  <v-container>
    <v-card>
      <v-card-text>
        <v-text-field
          v-model="todoId"
          label="ID"
          type="number"
        ></v-text-field>

        <v-text-field
          v-model="todoText"
          label="Todo text"
        ></v-text-field>

        <v-btn @click="sendTodo" color="primary">
          Add Todo
        </v-btn>
      </v-card-text>
    </v-card>
  </v-container>
</template>
```

## Material Design Icons

Vuetify använder Material Design Icons som standard. För att använda ikoner:

```vue
<template>
  <v-btn prepend-icon="mdi-home">Home</v-btn>
  <v-icon>mdi-heart</v-icon>
  <v-list-item prepend-icon="mdi-account">Profile</v-list-item>
</template>
```

[Material Design Icons](https://pictogrammers.com/library/mdi/)

# Alternativ 1: ENKEL - Notes App (Nybörjarnivå)

## Del 1: Produktägare - "Vad ska vi bygga?"

### Användarintervjuer (förenklat)

**Intervju med kompis Anna:**

- Använder anteckningar på telefonen för inköpslistor
- Irriterad över att det är svårt att hitta gamla anteckningar
- Vill kunna börja skriva snabbt

**Intervju med kompis Erik:**

- Skriver på papper mest
- Glömmer pappret hemma
- Vill ha något enkelt på mobilen

### User Stories (bara 4 stycken)

1. Som student vill jag skapa en anteckning för att komma ihåg saker
2. Som student vill jag se alla mina anteckningar för att hitta dem
3. Som student vill jag redigera en anteckning för att uppdatera den
4. Som student vill jag ta bort en anteckning som jag inte behöver

### MVP (Minimum Viable Product)

**Måste ha:**

- Skapa ny anteckning
- Lista alla anteckningar
- Ta bort anteckning

**Kan vänta:**

- Redigera, sök, kategorier, etc.

---

## Del 2: Design - "Hur ska det se ut?"

### Enkla Wireframes (papper + penna)

```
[Startsida]
+------------------------+
| Mina Anteckningar      |
|                        |
| [Anteckning 1]         |
| [Anteckning 2]         |
| [Anteckning 3]         |
|                        |
| [+ Ny Anteckning]      |
+------------------------+

[Skapa ny]
+------------------------+
| Ny Anteckning          |
|                        |
| Titel: [___________]   |
|                        |
| Text:                  |
| [________________]     |
| [________________]     |
| [________________]     |
|                        |
| [Spara] [Avbryt]       |
+------------------------+
```

### Design-beslut

- **Färger:** Vit bakgrund, blå knappar (enkelt)
- **Layout:** En kolumn, stora knappar för mobil
- **Navigation:** Bara två sidor

---

## Del 3: Arkitektur - "Hur ska vi bygga det?"

### Teknisk stack (keep it simple)

- HTML för struktur
- CSS för styling
- JavaScript för funktionalitet
- LocalStorage för att spara data

### Datamodell (super enkel)

```javascript
const note = {
  id: 1,
  title: "Min anteckning",
  text: "Detta är texten",
};
```

### ES6-features att använda

- `const/let` istället för var
- Arrow functions: `() => {}`
- Template literals: `${variable}`

### Funktioner som behövs

```javascript
function createNote() {
  /* skapa ny */
}
function showNotes() {
  /* visa alla */
}
function deleteNote(id) {
  /* ta bort */
}
function saveToStorage() {
  /* spara */
}
function loadFromStorage() {
  /* ladda */
}
```

---

## Del 4: Utveckling - "Bygg det!"

### HTML (index.html)

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Mina Anteckningar</title>
    <meta name="viewport" content="width=device-width, initial-scale=1" />
    <link rel="stylesheet" href="style.css" />
  </head>
  <body>
    <div id="app">
      <h1>Mina Anteckningar</h1>
      <button onclick="showCreateForm()">+ Ny Anteckning</button>
      <div id="notesList"></div>

      <div id="createForm" style="display:none">
        <h2>Ny Anteckning</h2>
        <input type="text" id="titleInput" placeholder="Titel" />
        <textarea id="textInput" placeholder="Skriv här..."></textarea>
        <button onclick="saveNote()">Spara</button>
        <button onclick="hideCreateForm()">Avbryt</button>
      </div>
    </div>
    <script src="app.js"></script>
  </body>
</html>
```

### CSS (style.css)

```css
body {
  font-family: Arial, sans-serif;
  max-width: 400px;
  margin: 0 auto;
  padding: 20px;
}

button {
  background: #007aff;
  color: white;
  border: none;
  padding: 10px 20px;
  border-radius: 5px;
  margin: 5px;
}

.note {
  border: 1px solid #ddd;
  padding: 10px;
  margin: 10px 0;
  border-radius: 5px;
}

input,
textarea {
  width: 100%;
  padding: 10px;
  margin: 5px 0;
  border: 1px solid #ddd;
  border-radius: 5px;
}
```

### JavaScript (app.js)

```javascript
let notes = [];
let nextId = 1;

// Ladda sparade anteckningar när sidan laddas
window.onload = () => {
  loadNotes();
  showNotes();
};

function loadNotes() {
  const saved = localStorage.getItem("notes");
  if (saved) {
    notes = JSON.parse(saved);
    nextId = notes.length + 1;
  }
}

function saveNotes() {
  localStorage.setItem("notes", JSON.stringify(notes));
}

function showNotes() {
  const list = document.getElementById("notesList");
  list.innerHTML = "";

  notes.forEach((note) => {
    const div = document.createElement("div");
    div.className = "note";
    div.innerHTML = `
            <h3>${note.title}</h3>
            <p>${note.text}</p>
            <button onclick="deleteNote(${note.id})">Ta bort</button>
        `;
    list.appendChild(div);
  });
}

function showCreateForm() {
  document.getElementById("createForm").style.display = "block";
}

function hideCreateForm() {
  document.getElementById("createForm").style.display = "none";
  document.getElementById("titleInput").value = "";
  document.getElementById("textInput").value = "";
}

function saveNote() {
  const title = document.getElementById("titleInput").value;
  const text = document.getElementById("textInput").value;

  if (title && text) {
    const note = {
      id: nextId++,
      title: title,
      text: text,
    };

    notes.push(note);
    saveNotes();
    showNotes();
    hideCreateForm();
  }
}

function deleteNote(id) {
  if (confirm("Ta bort anteckning?")) {
    notes = notes.filter((note) => note.id !== id);
    saveNotes();
    showNotes();
  }
}
```

---

## Del 5: Testning - "Fungerar det?"

### Enkla tester

1. **Test 1:** Skapa anteckning

   - Klicka "Ny Anteckning"
   - Skriv titel och text
   - Klicka "Spara"
   - ✅ Anteckningen visas i listan

2. **Test 2:** Ta bort anteckning

   - Klicka "Ta bort" på en anteckning
   - Bekräfta i dialog
   - ✅ Anteckningen försvinner

3. **Test 3:** Data sparas
   - Skapa anteckning
   - Uppdatera sidan (F5)
   - ✅ Anteckningen finns kvar

### Hittade problem

- Kan spara tom anteckning (fixat: lade till if-kontroll)
- Inte mobilanpassat (fixat: lade till viewport meta tag)

### Slutresultat

✅ Enkel app som fungerar
✅ Deployad på Netlify
✅ Alla MVP-krav uppfyllda

**Live demo:** [länk här]

---

## Reflektion

**Vad lärde jag mig?**

- Viktigt att planera först
- Enkelt är ofta bättre
- Testa tidigt och ofta

**Vad skulle jag göra annorlunda?**

- Fråga fler personer i intervjuer
- Göra bättre design först
- Skriva mer kommentarer i koden

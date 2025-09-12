# Alternativ 2: ENKEL VARIATION - Notes App (Fokus på enkelhet med annat perspektiv)

## Del 1: Produktägare - "Vem är användaren egentligen?"

### Användarintervjuer (annat fokus)

**Intervju med mormor Astrid (67 år):**

- Skriver inköpsslistor på lösa lappar
- Tappar bort lapparna
- Vill något "stort och tydligt" på telefonen

**Intervju med lillebror Lucas (14 år):**

- Använder Instagram/TikTok mest
- Anteckningar = bara skolrelaterat
- Vill kunna lägga till bilder och emojis

### User Stories (annat perspektiv - mer användarfokus)

1. Som äldre person vill jag ha stora knappar för att enkelt kunna völja och trycka rätt
2. Som ung person vill jag kunna lägga till emojis för att göra anteckningar roligare
3. Som glömsk person vill jag se datum på anteckningar för att veta när jag skapade dem
4. Som person med dålig syn vill jag kunna göra texten större

### MVP (Annorlunda prioritering)

**Måste ha:**

- Skapa anteckning med datum
- Stora, tydliga knappar
- Visa när anteckning skapades

**Kan vänta:**

- Ta bort, redigera, sortering

---

## Del 2: Design - "Tillgänglighet först!"

### Wireframes (fokus på användarvänlighet)

```
[Startsida - Stora element]
+------------------------+
| 📝 MINA ANTECKNINGAR   |
|   [    STOR KNAPP    ] |
|   [  SKAPA ANTECKN.  ] |
|                        |
| 📅 Idag               |
| [Anteckning 1.........]|
| [med mycket text.....]|
|                        |
| 📅 Igår               |
| [Anteckning 2.........]|
+------------------------+

[Skriv - Stort fokus]
+------------------------+
| ✏️ SKRIV ANTECKNING    |
|                        |
| [________________]     |
| [________________]     |
| [________________]     |
| [________________]     |
| [________________]     |
|                        |
| [ 😊 ] [ 📚 ] [ ⭐ ]   |
|                        |
| [   SPARA ANTECKN.   ] |
+------------------------+
```

### Design-beslut (helt annat fokus)

- **Färger:** Gul bakgrund (glad känsla), stora kontraster
- **Typography:** Extra stora texter (18px+)
- **Interaktion:** Stora touch-targets (60px+)
- **Features:** Emoji-support, datum synligt

---

## Del 3: Arkitektur - "Enkelt men annorlunda"

### Teknisk stack (lika enkelt, andra val)

- HTML med semantic elements (header, main, section)
- CSS Grid istället för Flexbox
- JavaScript med mer ES6 (array methods)
- Date-objekt för tidshantering

### Datamodell (mer info)

```javascript
const note = {
  id: Date.now(), // Använd timestamp som ID
  text: "Min anteckning här",
  emoji: "😊",
  createdDate: new Date().toLocaleDateString("sv-SE"),
};
```

### ES6-features att använda (andra funktioner)

- Array.map() för att visa lista
- Array.filter() för datumgruppering
- Date-objektet för timestamps
- Spread operator för kopiering

### Funktioner som behövs

```javascript
const addNote = (text, emoji) => {
  /* lägg till */
};
const getNotesToday = () => {
  /* dagens anteckningar */
};
const getNotesYesterday = () => {
  /* gårdagens */
};
const groupNotesByDate = () => {
  /* gruppera per dag */
};
```

---

## Del 4: Utveckling - "Tillgänglig kod!"

### HTML (semantic och accessible)

```html
<!DOCTYPE html>
<html lang="sv">
  <head>
    <title>Mina Anteckningar - Enkelt och Stort</title>
    <meta name="viewport" content="width=device-width, initial-scale=1" />
    <link rel="stylesheet" href="style.css" />
  </head>
  <body>
    <header>
      <h1>📝 Mina Anteckningar</h1>
    </header>

    <main id="app">
      <button id="createBtn" class="big-button">✏️ SKAPA ANTECKNING</button>

      <section id="notesList" aria-live="polite">
        <!-- Anteckningar kommer här -->
      </section>

      <dialog id="createDialog">
        <h2>Skriv ny anteckning</h2>
        <textarea id="noteText" placeholder="Vad tänker du på?"></textarea>

        <div class="emoji-picker">
          <span class="emoji-option" data-emoji="😊">😊</span>
          <span class="emoji-option" data-emoji="📚">📚</span>
          <span class="emoji-option" data-emoji="⭐">⭐</span>
          <span class="emoji-option" data-emoji="💡">💡</span>
        </div>

        <button id="saveBtn" class="big-button">SPARA</button>
        <button id="cancelBtn" class="cancel-button">Avbryt</button>
      </dialog>
    </main>

    <script src="app.js"></script>
  </body>
</html>
```

### CSS (fokus på storlek och kontrast)

```css
:root {
  --yellow: #fff3cd;
  --blue: #0066cc;
  --green: #28a745;
  --gray: #6c757d;
}

body {
  font-family: "Georgia", serif;
  background: var(--yellow);
  max-width: 500px;
  margin: 0 auto;
  padding: 20px;
  font-size: 18px;
  line-height: 1.6;
}

.big-button {
  background: var(--blue);
  color: white;
  border: none;
  padding: 20px 30px;
  border-radius: 10px;
  font-size: 20px;
  font-weight: bold;
  width: 100%;
  margin: 10px 0;
  min-height: 60px;
  cursor: pointer;
}

.note-card {
  background: white;
  border: 3px solid var(--blue);
  padding: 20px;
  margin: 15px 0;
  border-radius: 10px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

.note-date {
  color: var(--gray);
  font-weight: bold;
  margin-bottom: 15px;
  font-size: 16px;
}

.emoji-picker {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 10px;
  margin: 15px 0;
}

.emoji-option {
  font-size: 30px;
  text-align: center;
  padding: 10px;
  cursor: pointer;
  border: 2px solid transparent;
  border-radius: 10px;
}

.emoji-option:hover,
.emoji-option.selected {
  border-color: var(--blue);
  background: #f8f9fa;
}

textarea {
  width: 100%;
  min-height: 120px;
  font-size: 18px;
  padding: 15px;
  border: 2px solid var(--gray);
  border-radius: 10px;
  resize: vertical;
}
```

### JavaScript (mer funktionell stil)

```javascript
// State
let notes = [];
let selectedEmoji = "😊";

// DOM Elements
const createBtn = document.getElementById("createBtn");
const createDialog = document.getElementById("createDialog");
const notesList = document.getElementById("notesList");
const noteText = document.getElementById("noteText");
const saveBtn = document.getElementById("saveBtn");
const cancelBtn = document.getElementById("cancelBtn");

// Event Listeners
createBtn.addEventListener("click", () => openCreateDialog());
saveBtn.addEventListener("click", () => saveNote());
cancelBtn.addEventListener("click", () => closeCreateDialog());

// Emoji selection
document.querySelectorAll(".emoji-option").forEach((emoji) => {
  emoji.addEventListener("click", (e) => {
    document
      .querySelectorAll(".emoji-option")
      .forEach((em) => em.classList.remove("selected"));
    e.target.classList.add("selected");
    selectedEmoji = e.target.dataset.emoji;
  });
});

// Functions
const loadNotes = () => {
  const saved = localStorage.getItem("simpleNotes");
  notes = saved ? JSON.parse(saved) : [];
};

const saveNotes = () => {
  localStorage.setItem("simpleNotes", JSON.stringify(notes));
};

const openCreateDialog = () => {
  createDialog.showModal();
  noteText.focus();
};

const closeCreateDialog = () => {
  createDialog.close();
  noteText.value = "";
  selectedEmoji = "😊";
  document.querySelector(".emoji-option").classList.add("selected");
};

const saveNote = () => {
  const text = noteText.value.trim();
  if (!text) return;

  const newNote = {
    id: Date.now(),
    text: text,
    emoji: selectedEmoji,
    createdDate: new Date().toLocaleDateString("sv-SE"),
    createdTime: new Date().toLocaleTimeString("sv-SE", {
      hour: "2-digit",
      minute: "2-digit",
    }),
  };

  notes.unshift(newNote); // Lägg till först i arrayen
  saveNotes();
  renderNotes();
  closeCreateDialog();
};

const groupNotesByDate = () => {
  const grouped = {};
  notes.forEach((note) => {
    const date = note.createdDate;
    if (!grouped[date]) grouped[date] = [];
    grouped[date].push(note);
  });
  return grouped;
};

const renderNotes = () => {
  const groupedNotes = groupNotesByDate();

  if (notes.length === 0) {
    notesList.innerHTML =
      '<p style="text-align:center; color:#6C757D;">Inga anteckningar än. Skapa din första!</p>';
    return;
  }

  notesList.innerHTML = Object.entries(groupedNotes)
    .map(
      ([date, dayNotes]) => `
            <div class="note-date">📅 ${formatDate(date)}</div>
            ${dayNotes
              .map(
                (note) => `
                <div class="note-card">
                    <div style="display: flex; align-items: center; gap: 10px;">
                        <span style="font-size: 24px;">${note.emoji}</span>
                        <small style="color: #6C757D;">${note.createdTime}</small>
                    </div>
                    <div style="margin-top: 10px; font-size: 18px;">
                        ${note.text}
                    </div>
                </div>
            `
              )
              .join("")}
        `
    )
    .join("");
};

const formatDate = (dateStr) => {
  const today = new Date().toLocaleDateString("sv-SE");
  const yesterday = new Date(
    Date.now() - 24 * 60 * 60 * 1000
  ).toLocaleDateString("sv-SE");

  if (dateStr === today) return "Idag";
  if (dateStr === yesterday) return "Igår";
  return dateStr;
};

// Initialize
window.addEventListener("load", () => {
  loadNotes();
  renderNotes();
  document.querySelector(".emoji-option").classList.add("selected");
});
```

---

## Del 5: Testning - "Användarvänlighetstestning"

### Tillgänglighetstester

1. **Test med tangentbord:**

   - Tab genom alla element
   - ✅ Alla knappar kan nås
   - ✅ Dialog öppnas och stängs

2. **Test med stor text (zoom 150%):**

   - Zooma webbläsare till 150%
   - ✅ Allt syns fortfarande
   - ✅ Knappar fortfarande klickbara

3. **Test med äldre användare:**
   - Låt någon 60+ testa
   - ✅ Kunde förstå gränssnittet
   - ✅ Stora knappar fungerade bra

### Användartest (annorlunda fokus)

1. **Känslomässig respons:**

   - "Känns glad och positiv med gula färger"
   - "Emojis gör det roligare"
   - "Stora knappar känns säkra"

2. **Användbarhet:**
   - Hittade snabbt hur man skapar anteckning
   - Datum hjälpte att orientera sig
   - Saknade "ta bort"-funktion

### Slutresultat

✅ Fokus på användarupplevelse istället för tekniska features
✅ Fungerar bra för olika åldersgrupper
✅ Semantic HTML för skärmläsare
✅ Tydlig visuell hierarki

**Live demo:** [länk här]

---

## Reflektion

**Vad var annorlunda från förra alternativet?**

- Fokus på VEMS behov vi löser, inte bara VAD
- Tillgänglighet som grund, inte efterkonstruktion
- Användarupplevelse före tekniska features

**Vad lärde jag mig om rollerna?**

- **PO:** Olika användare = helt olika krav
- **Design:** Tillgänglighet påverkar alla designbeslut
- **Arkitekt:** Samma tekniker, men olika implementation
- **Developer:** Semantic HTML ger bättre grund
- **QA:** Olika testmetoder ger olika insikter

**Viktigaste insikten:**
Det finns inget "rätt" sätt - samma problem kan lösas på många olika sätt!

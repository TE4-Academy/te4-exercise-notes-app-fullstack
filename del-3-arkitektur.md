# Del 3: Lösningsarkitekt & Teknisk Planering

## Roll: Lösningsarkitekt (Solution Architect)
En lösningsarkitekt tar designen och bestämmer HUR det ska byggas tekniskt. De väljer teknologier, planerar datastruktur och identifierar tekniska risker.

## Uppgift
Planera den tekniska implementationen av din anteckningsapp.

### Steg 1: Teknisk Stack
Baserat på din MVP och design, bestäm vilka teknologier du ska använda:

**Frontend:**
- HTML5 (semantiska element)
- CSS3 (Grid/Flexbox för layout, CSS Variables)
- JavaScript ES6+ (vilka features behöver du?)

**Data lagring:**
- LocalStorage (för att spara anteckningar lokalt)
- (Senare: kanske databas/backend)

**Deployment:**
- Netlify 

**Verktyg:**
- VS Code
- Git/GitHub
- Browser Developer Tools

### Steg 2: Datamodell
Designa hur dina anteckningar ska lagras som JavaScript-objekt:

```javascript
// Exempel på datastruktur
const note = {
  id: "unique-id-123",
  title: "Min anteckning",
  content: "Detta är innehållet...",
  createdAt: "2025-01-15T10:30:00Z",
  updatedAt: "2025-01-15T11:45:00Z",
  tags: ["skola", "viktigt"]
};
```

**Fundera på:**
- Vilka properties behöver varje anteckning?
- Hur genererar du unika ID:n?
- Hur hanterar du datum/tid?
- Behöver du kategorier eller taggar?

### Steg 3: ES6 Features Mapping
Identifiera vilka ES6-funktioner du kommer använda och var:

**Exempel:**
```javascript
// Arrow functions - för event handlers
const saveNote = () => { ... }

// Template literals - för HTML-generering
const noteHTML = `<div class="note">${note.title}</div>`;

// Destructuring - för att hämta data
const { title, content } = note;

// Spread operator - för att kopiera arrays
const allNotes = [...existingNotes, newNote];

// Array methods - för att filtrera/sortera
const recentNotes = notes.filter(note => isRecent(note.createdAt));
```

### Steg 4: Funktionsplanering
Dela upp din app i konkreta JavaScript-funktioner:

**Exempel:**
```javascript
// Data functions
function saveNote(note) { ... }
function loadNotes() { ... }
function deleteNote(id) { ... }

// UI functions  
function renderNotesList(notes) { ... }
function showNoteEditor(note) { ... }
function hideNoteEditor() { ... }

// Event handlers
function handleCreateNote() { ... }
function handleSaveNote() { ... }
function handleDeleteNote(id) { ... }
```

### Steg 5: Mobile-Responsive Plan
Planera hur CSS ska hantera olika skärmstorlekar:

```css
/* Mobile first approach */
.notes-container {
  /* Mobile styles (default) */
}

@media (min-width: 768px) {
  .notes-container {
    /* Tablet styles */
  }
}

@media (min-width: 1024px) {
  .notes-container {
    /* Desktop styles */
  }
}
```

### Steg 6: Implementation Roadmap
Planera i vilken ordning du ska bygga:

1. **HTML struktur** - Grundläggande sidor och navigation
2. **CSS styling** - Få det att se bra ut på mobil
3. **JavaScript core** - LocalStorage och grundfunktioner
4. **UI interaktioner** - Knappar, formulär, navigation
5. **Polish** - Animationer, felhantering, optimering

### Steg 7: Identifiera Risker
Vad kan gå fel? Planera lösningar:
- Vad händer om LocalStorage är fullt?
- Vad händer om användaren stänger appen mitt i redigering?
- Hur hanterar du mycket långa anteckningar?
- Funkar appen offline?

## Leverans
Skapa följande filer:
- `tech-stack.md` - Valda teknologier med motivering
- `data-model.js` - Exempel på datastrukturer (kommenterad kod)
- `es6-features.md` - Lista över ES6-features och var de används
- `function-plan.js` - Skiss av alla funktioner (bara signaturer och kommentarer)
- `responsive-plan.md` - CSS-strategi för olika skärmstorlekar  
- `implementation-roadmap.md` - Ordning för implementation
- `risk-analysis.md` - Identifierade risker och lösningar

## Tidsåtgång
Ca 2-3 timmar

## Nästa steg
När den tekniska planen är klar går du vidare till Del 4: Implementation

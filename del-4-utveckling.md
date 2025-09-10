# Del 4: Utvecklare & Implementation

## Roll: Frontend Developer
Nu är det dags att bygga! Som utvecklare tar du alla planer från tidigare delar och gör dem till verklighet med kod.

## Uppgift
Implementera din anteckningsapp enligt planerna från Del 1-3.

### Steg 1: Projektstruktur
Skapa en organiserad mappstruktur:

```
notes-app/
├── index.html
├── css/
│   ├── style.css
│   └── mobile.css
├── js/
│   ├── app.js
│   ├── storage.js
│   └── ui.js
├── assets/
│   └── (bilder, ikoner)
└── README.md
```

### Steg 2: HTML Foundation
Bygg semantic HTML som följer din design:

**Fokusera på:**
- Semantic elements (`<main>`, `<section>`, `<article>`, `<nav>`)
- Accessibility (ARIA-labels, alt-text, proper form labels)
- Mobile viewport meta tag
- Proper form elements för anteckningsinmatning

**Tips:**
```html
<!DOCTYPE html>
<html lang="sv">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mina Anteckningar</title>
</head>
```

### Steg 3: Mobile-First CSS
Implementera din design med mobil som utgångspunkt:

**Använd moderna CSS:**
- CSS Grid eller Flexbox för layout
- CSS Custom Properties (variables) för färger och spacing
- Smooth transitions för interaktioner
- Focus states för accessibility

**Exempel:**
```css
:root {
  --primary-color: #007AFF;
  --text-color: #1D1D1F;
  --background: #F2F2F7;
  --card-background: #FFFFFF;
}

.note-card {
  background: var(--card-background);
  border-radius: 12px;
  padding: 1rem;
  margin-bottom: 1rem;
  box-shadow: 0 2px 8px rgba(0,0,0,0.1);
}
```

### Steg 4: JavaScript Core Features
Implementera din datamodell och kärnfunktionalitet:

**LocalStorage hantering:**
```javascript
// storage.js
class NotesStorage {
    static saveNote(note) {
        const notes = this.getAllNotes();
        const existingIndex = notes.findIndex(n => n.id === note.id);
        
        if (existingIndex >= 0) {
            notes[existingIndex] = { ...note, updatedAt: new Date().toISOString() };
        } else {
            notes.push({ ...note, createdAt: new Date().toISOString() });
        }
        
        localStorage.setItem('notes', JSON.stringify(notes));
    }
    
    static getAllNotes() {
        const stored = localStorage.getItem('notes');
        return stored ? JSON.parse(stored) : [];
    }
}
```

### Steg 5: ES6 Features Implementation
Använd moderna JavaScript-features från din planering:

**Exempel på ES6 användning:**
```javascript
// Arrow functions för event handlers
const handleCreateNote = () => {
    const newNote = {
        id: Date.now().toString(),
        title: document.getElementById('note-title').value,
        content: document.getElementById('note-content').value
    };
    
    NotesStorage.saveNote(newNote);
    renderNotesList();
};

// Template literals för HTML generation
const createNoteHTML = (note) => `
    <article class="note-card" data-id="${note.id}">
        <h3>${note.title}</h3>
        <p>${note.content.substring(0, 100)}...</p>
        <div class="note-actions">
            <button onclick="editNote('${note.id}')">Redigera</button>
            <button onclick="deleteNote('${note.id}')">Ta bort</button>
        </div>
    </article>
`;

// Array methods för datamanipulation
const searchNotes = (query) => {
    const allNotes = NotesStorage.getAllNotes();
    return allNotes.filter(note => 
        note.title.toLowerCase().includes(query.toLowerCase()) ||
        note.content.toLowerCase().includes(query.toLowerCase())
    );
};
```

### Steg 6: UI Interaktions och Navigation
Implementera alla användarinteraktioner från din design:

- Skapa ny anteckning
- Visa anteckningslista  
- Redigera befintlig anteckning
- Ta bort anteckning
- Sök bland anteckningar (om det var i din MVP)

**Fokusera på:**
- Smooth transitions mellan vyer
- Loading states
- Felhantering (tom titel, etc.)
- Bekräftelse innan borttagning

### Steg 7: Progressive Enhancement
Lägg till extra funktionalitet som förbättrar upplevelsen:

- Tangentbordsgenvägar (Ctrl+S för spara, etc.)
- Ångra-funktion för borttagning

### Steg 8: Testing & Debugging
Testa din app grundligt:

- Testa på olika skärmstorlekar
- Testa med mycket data (100+ anteckningar)
- Testa edge cases (tomma fält, långa texter)
- Använd browser dev tools för debugging
- Testa offline-funktionalitet

### Steg 9: Deployment
Deploya din app till Netlify:

1. Commit all kod till Git
2. Push till GitHub repository
3. Koppla GitHub repo till Netlify
4. Testa live-versionen

## Kod-kvalitet Krav
- **Clean Code**: Använd beskrivande variabel- och funktionsnamn
- **Comments**: Kommentera komplexa logik
- **Consistency**: Enhetlig kod-stil
- **Error Handling**: Hantera fel gracefully
- **Performance**: Appen ska kännas snabb

## Leverans
Skapa och deploya en fungerande anteckningsapp som innehåller:

1. **Fungerande app** deployad på Netlify
2. **Källkod** strukturerad i mappar enligt plan
3. **README.md** med instruktioner för att köra lokalt
4. **demo-video.md** - kort beskrivning eller video som visar appen

**Länk till live-appen ska fungera på mobil och desktop!**

## Tidsåtgång
Ca 6-8 timmar (kan fördelas över flera dagar)

## Nästa steg
När implementationen är klar går du vidare till Del 5: Testing & Validering

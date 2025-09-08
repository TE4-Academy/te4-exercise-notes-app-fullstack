# Projektuppsättning - Anteckningsapp Fullstack

## Innan du börjar
Denna övning kommer att ta dig igenom hela utvecklingsprocessen från idé till färdig produkt. Du kommer att skapa många dokument och filer under vägen, så det är viktigt att ha en bra struktur från början.

## Steg 1: Skapa ditt projekt-repository

### 1.1 Skapa nytt repository på GitHub
1. Gå till [GitHub](https://github.com)
2. Klicka på "New repository"
3. Namnge det: `notes-app-[dittnamn]` (ex: `notes-app-michael`)
4. Markera "Add a README file"
5. Välj "Public" (så andra kan se ditt arbete)
6. Klicka "Create repository"

### 1.2 Klona till din dator
```bash
# Öppna terminal i VS Code (Ctrl+Shift+`)
# Navigera till din DEV-mapp
cd C:\Users\[dittanvändarnamn]\DEV

# Klona ditt repository
git clone https://github.com/[dittgithubnamn]/notes-app-[dittnamn].git

# Gå in i mappen
cd notes-app-[dittnamn]

# Öppna i VS Code
code .
```

## Steg 2: Skapa projektstrukturen

### 2.1 Grundläggande mappstruktur
Skapa följande mappar och filer i VS Code:

```
notes-app-[dittnamn]/
├── README.md                    (finns redan)
├── planning/                    (för del 1-3)
│   ├── del-1-produktagare/
│   ├── del-2-design/
│   ├── del-3-arkitektur/
│   └── process-log.md
├── app/                         (för del 4)
│   ├── index.html
│   ├── css/
│   │   └── style.css
│   ├── js/
│   │   └── app.js
│   └── assets/
└── testing/                     (för del 5)
    ├── test-results/
    └── bug-reports/
```

### 2.2 Skapa mapparna
Högerklicka i VS Code Explorer och skapa alla mappar enligt strukturen ovan.


### 2.3 Skapa grundfiler
Skapa följande filer (högerklicka i respektive mapp → "New File"):

**I planning-mappen:**
- `process-log.md` (för att logga din planering, dina beslut och reflektioner)

**I app-mappen:**
- `index.html`
- `css/style.css`
- `js/app.js`

## Steg 3: Konfigurera VS Code för projektet

### 3.1 Kolla att du har följande extensions 
1. Öppna Extensions (Ctrl+Shift+X)
2. Du ska se dessa som installerade:
   - **Live Server** - för att köra din app lokalt
   - **Prettier** - för kodformattering

### 3.2 Testa Live Server
1. Högerklicka på `app/index.html`
2. Välj "Open with Live Server"
3. Din app öppnas på `http://localhost:5500` (kommer att uppdateras automatiskt när du sparar ändringar)

### 3.3 Konfigurera Git
Skapa en `.gitignore`-fil i root-mappen:

```gitignore
# VS Code settings
.vscode/settings.json

# OS generated files
.DS_Store
Thumbs.db

# Temporary files
*.tmp
*.temp

# Dependencies (om du senare använder npm)
node_modules/
```

## Steg 4: Uppdatera huvuddokumentationen

### 4.1 Redigera README.md
Ersätt innehållet i din `README.md` med:

```markdown
# Anteckningsapp - Fullstack Utvecklingsprojekt

## Projektbeskrivning
En mobilanpassad anteckningsapp byggd genom att gå igenom alla roller i mjukvarutveckling.

## Projektmål
- Lära mig fullstack-utvecklingsprocessen
- Förstå olika roller i mjukvaruteam
- Skapa en riktig app som andra kan använda
- Använda moderna webtekniker (ES6, responsiv design)

## Teknisk stack
- **Frontend:** HTML5, CSS3, JavaScript ES6+
- **Storage:** LocalStorage
- **Hosting:** Netlify
- **Utveckling:** VS Code, Git, GitHub

## Projektstruktur
- `planning/` - Krav, design och arkitektur
- `app/` - Källkod för applikationen
- `testing/` - Testdokumentation och bugrapporter

## Live Demo
🚧 Under utveckling - länk kommer här senare

## Utvecklingsprocess
1. **Del 1:** Produktägare & Kravanalys
2. **Del 2:** UX/UI Design & Tillgänglighet  
3. **Del 3:** Lösningsarkitekt & Teknisk Planering
4. **Del 4:** Utvecklare & Implementation
5. **Del 5:** QA/Testare & Produktvalidering

## Logga framsteg
Se `planning/process-log.md` för dagliga reflektioner och beslut.
```

### 4.2 Skapa process-log.md
I `planning/process-log.md`:

```markdown
# Utvecklingsprocess Logg

## Syfte
Detta dokument loggar mina beslut, lärdomar och reflektioner genom utvecklingsprocessen.

---

## [Datum: 2025-09-08] - Projektstart

### Vad jag gjorde idag:
- Satte upp projekt-repository och mappstruktur
- Konfigurerade VS Code för utveckling
- Läste igenom alla övningsdelar

### Förväntningar:
- 

### Frågor att ta reda på:
- 

---

## [Datum: ] - Del 1: Produktägare

### User interviews genomförda:
- Person 1: [namn/relation]
- Person 2: [namn/relation]

### Viktiga insikter:
- 

### MVP-beslut:
- 

### Utmaningar:
- 

---

## [Datum: ] - Del 2: Design

### Design-beslut:
- 

### Tillgänglighetstester:
- 

### Utmaningar:
- 

---

## [Datum: ] - Del 3: Arkitektur

### Tekniska beslut:
- 

### ES6-features jag kommer använda:
- 

### Identifierade risker:
- 

---

## [Datum: ] - Del 4: Implementation

### Utvecklingsframsteg:
- 

### Buggar jag stötte på:
- 

### Lärdomar:
- 

---

## [Datum: ] - Del 5: Testing

### Testresultat:
- 

### Kritiska buggar:
- 

### Förbättringsområden:
- 

---

## Slutreflektion

### Vad lärde jag mig mest av:
- 

### Vad skulle jag göra annorlunda:
- 

### Nästa steg för att utvecklas:
- 
```

## Steg 5: Första commit

### 5.1 Committa grundstrukturen
```bash
# Lägg till alla filer
git add .

# Committa med beskrivande meddelande
git commit -m "Initial project setup: Add folder structure and documentation"

# Pusha till GitHub
git push origin main
```

## Arbetsflöde under projektet

### Daglig rutin:
1. **Starta dagen:** Öppna VS Code och ditt projekt
2. **Innan du börjar koda:** Uppdatera `process-log.md` med vad du planerar att göra
3. **Under arbetet:** Committa ofta med beskrivande meddelanden
4. **Efter varje del:** Uppdatera process-loggen med lärdomar
5. **Deploy tidigt och ofta:** Pusha till GitHub regelbundet

### Git-kommandoer du kommer behöva:
```bash
# Se status på dina ändringar
git status

# Lägg till specifika filer
git add planning/del-1-produktagare/user-stories.md

# Lägg till alla ändringar
git add .

# Committa med meddelande
git commit -m "Add user stories from interviews"

# Pusha till GitHub
git push
```

## Du är redo att börja!

Nu har du en professionell projektstruktur där du kan:
- ✅ Spåra alla dina beslut och lärdomar
- ✅ Visa ditt arbete för andra
- ✅ Bygga en portfölj av ditt utvecklingsarbete
- ✅ Arbeta som en riktig utvecklare

**Nästa steg:** Öppna `planning/del-1-produktagare/` och börja med första delen av övningen!


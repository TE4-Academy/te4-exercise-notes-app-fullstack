## Syfte med User Stories

User Stories är korta, enkla beskrivningar av funktionalitet från slutanvändarens perspektiv. Syftet är att:

- **Fokusera på värde:** Beskriva *varför* en funktion behövs, inte bara *vad* som ska byggas
- **Främja kommunikation:** Skapa gemensam förståelse mellan roller
- **Möjliggöra prioritering:** Hjälpa produktägare att rangordna utvecklingsarbete
- **Stödja iterativ utveckling:** Dela upp stor funktionalitet i hanterbara delar
- **Behålla användarperspektiv:** Säkerställa att tekniska lösningar löser verkliga problem

Formatet är vanligtvis: *"Som [roll] vill jag [funktionalitet] så att [värde/syfte]"*

## Hur olika roller arbetar med User Stories

### Product Owner/Product Manager

**Ansvar:**
- Skriver och äger user stories
- Definierar acceptanskriterier
- Prioriterar backlog baserat på affärsvärde
- Säkerställer att stories levererar användarnytta

**Arbetssätt:**
```
Som kund vill jag kunna filtrera produkter på pris 
så att jag snabbt hittar produkter inom min budget.

Acceptanskriterier:
- Prisfilter visas i sidopanelen
- Användare kan ange min- och maxpris
- Produktlistan uppdateras direkt när filter ändras
- Filter behålls när användaren navigerar mellan sidor
```

**Fokusområden:**
- Validerar att stories skapar affärsnytta
- Säkerställer INVEST-principerna (Independent, Negotiable, Valuable, Estimatable, Small, Testable)
- Kommunicerar vision och prioriteringar till teamet

### Utvecklare/Programmerare

**Ansvar:**
- Bryter ner stories i tekniska tasks
- Estimerar utvecklingstid och komplexitet
- Implementerar funktionaliteten enligt acceptanskriterier
- Identifierar tekniska beroenden och risker

**Arbetssätt:**
```
User Story: "Prisfilter för produkter"

Teknisk nedbrytning:
□ Skapa API-endpoint för filtrerad produktsökning
□ Implementera prisfilter-komponent i React
□ Integrera med befintlig produktlista
□ Lägga till URL-parametrar för delningsbara filter
□ Skriva enhetstester för filterfunktionalitet
□ Optimera databassökning med index
```

**Fokusområden:**
- Förstår affärsvärdet bakom varje story
- Ställer frågor om oklarheter innan utveckling börjar
- Föreslår tekniska alternativ som kan påverka scope eller prioritet
- Kommunicerar tekniska begränsningar och möjligheter

### UX/UI Designer

**Ansvar:**
- Översätter user stories till användarvänliga gränssnitt
- Säkerställer att lösningen möter användarnas behov
- Skapar wireframes, mockups och prototyper
- Validerar design genom användartester

**Arbetssätt:**
- Analyserar user persona och användarresan
- Skapar designskisser baserat på acceptanskriterier
- Samarbetar med utvecklare om tekniska möjligheter
- Förfinar design baserat på feedback från användartester

**Fokusområden:**
- Säkerställer att gränssnittet stödjer den önskade användarupplevelsen
- Identifierar potentiella användbarhetsproblem tidigt
- Balanserar funktionalitet med enkelhet
- Bidrar till acceptanskriterier ur användbarhetsperspektiv

### QA/Tester

**Ansvar:**
- Skapar testfall baserat på acceptanskriterier
- Verifierar att implementationen uppfyller story-kraven
- Identifierar edge cases och potentiella buggar
- Säkerställer kvalitet ur slutanvändarperspektiv

**Arbetssätt:**
```
Testfall för "Prisfilter":
1. Verifiera att prisfilter visas korrekt
2. Testa med olika prisintervall
3. Kontrollera att produktlistan uppdateras rätt
4. Testa edge cases (negativa värden, mycket stora tal)
5. Verifiera att filter fungerar med andra filter kombinerat
6. Testa på olika webbläsare och enheter
```

**Fokusområden:**
- Förstår användarens förväntade upplevelse
- Tänker kritiskt på hur funktionen kan missbrukas eller fallera
- Säkerställer att "definition of done" uppfylls
- Kommunicerar kvalitetsproblem till teamet

### Scrum Master/Team Lead

**Ansvar:**
- Underlättar diskussioner kring user stories
- Säkerställer att stories är väl definierade innan sprint
- Hjälper teamet att bryta ner stora stories
- Främjar tvärs-funktionellt samarbete

**Arbetssätt:**
- Faciliterar story grooming/refinement-möten
- Säkerställer att alla roller förstår och kan bidra till storyn
- Hjälper till att lösa konflikter kring scope eller prioritet
- Följer upp att stories levereras enligt acceptanskriterier

## Bästa praxis för alla roller

**Under Sprint Planning:**
- Alla roller deltar i diskussion om varje story
- Acceptanskriterier klargörs och kompletteras
- Tekniska risker och beroenden identifieras
- Estimat görs baserat på hela teamets input

**Under Sprint:**
- Regelbunden kommunikation mellan roller
- Tidiga prototyper och feedback-loopar
- Kontinuerlig validering mot acceptanskriterier
- Flexibilitet för justeringar baserat på nya insikter

**Vid Sprint Review:**
- Demo fokuserar på affärsvärdet som levereras
- Feedback från stakeholders samlas in
- Lärdomar dokumenteras för framtida stories

User Stories fungerar bäst när alla roller ser dem som ett verktyg för samarbete snarare än bara dokumentation. De ska inspirera konversationer och gemensam problemlösning, inte ersätta dem.
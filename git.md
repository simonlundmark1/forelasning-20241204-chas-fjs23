# Git

Vi ska titta på...

Git Flow vs. Github flow vs Open source - Fork / PR 

...och jämföra fördelar och nackdelar.

## Git flow

**Git flow är bra när du har en planerad release och kanske olika kunder som använder olika versioner.**

Git Flow är en populär arbetsmodell för versionshantering som definierar en strikt förgrening och release-process. Modellen består av följande huvudgrenar:

### Huvudgrenar

- **main/master**: Innehåller produktionskoden
- **develop**: Utvecklingsgren där nya funktioner integreras

### Stödgrenar

- **feature/***:  Används för att utveckla nya funktioner
- **release/***:  Förbereder en ny produktionsrelease
- **hotfix/***:   Snabba bugfixar i produktionen

### Arbetsflöde

1. Utveckling sker i feature-grenar som skapas från develop
2. Feature-grenar mergas tillbaka till develop när funktionen är klar
3. När develop är redo för release skapas en release-gren
4. Release-grenen mergas till både main och develop
5. Hotfix-grenar skapas från main vid akuta buggar
6. Hotfix mergas till både main och develop

Detta arbetssätt ger en tydlig struktur och möjliggör parallell utveckling samtidigt som en stabil produktionskod upprätthålls.

---

## Github flow

**Github Flow är när du själv bestämmer när du vill göra en release. Till exempel om du jobbar med en SaaS-produkt där alla användare har samma version.**

Github Flow är en enklare och mer strömlinjeformad arbetsmodell jämfört med Git Flow. Den är särskilt anpassad för kontinuerlig leverans och deployment.

### Huvudprinciper

- **main**: En enda huvudgren som alltid är deploybar
- **feature-grenar**: Kortlivade grenar för utveckling

### Arbetsflöde

1. Skapa en feature-gren från main
2. Gör ändringar och committa regelbundet
3. Öppna en pull request för diskussion
4. Granska koden och diskutera ändringar
5. Deploya till testmiljö och verifiera
6. Merga till main och deploya

*Vi ska titta på hur man gör i praktiken snart*

### Fördelar

- Enklare att förstå och följa
- Snabbare releaser
- Mindre overhead
- Bättre för kontinuerlig leverans
- Tydligt fokus på pull requests och kodgranskning

### Nackdelar

- Kan vara svårare att hantera flera parallella releaser
- Mindre struktur för större projekt
- Kräver stark automatisering för att fungera effektivt

---

## Forking workflow

*Används för Open Source-projekt*

1. Den som vill bidra skapar en fork av repositoryt.
2. Den som vill bidra klonar fork:en till sin egen dator.
3. Den som vill bidra checkar ut en branch för sina ändringar.
4. När ändringarna är färdiga så skapar man en pull request mot det ursprungliga repositoryt.
5. Review - Någon ska kolla på koden innan den mergas
6. Den ursprungliga ägaren av repositoryt mergear sedan in de ändringarna till sitt repository.
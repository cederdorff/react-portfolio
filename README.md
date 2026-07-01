# username.github.io

Dette repository er en React portfolio-template til GitHub Pages.

Studerende skal bruge templaten til at oprette deres eget repository med navnet:

```text
[dit-github-brugernavn].github.io
```

Hvis dit GitHub-brugernavn er `sofieholm`, skal dit repository hedde:

```text
sofieholm.github.io
```

Når portfolioen er deployet, ligger den på:

```text
https://[dit-github-brugernavn].github.io
```

## Template repository

Template-repositoryet ligger her:

[github.com/cederdorff/username.github.io](https://github.com/cederdorff/username.github.io)

Navnet `username.github.io` er kun et eksempelnavn i templaten. Når du opretter dit eget repository, skal `username` erstattes med dit eget GitHub-brugernavn.

## Hvad templaten indeholder

- Vite + React
- React Router til sider og navigation
- sider til forside, projekter, projektdetaljer, om mig, kontakt og 404
- projektdata i `src/data/projects.js`
- styling i `src/index.css`
- automatisk deployment til GitHub Pages med `.github/workflows/deploy.yml`

## Eksempler fra tidligere studerende

Her er eksempler på tidligere studerendes deployede portfolioer:

- [stinelock.github.io](https://stinelock.github.io/)
- [sofienholm.github.io](https://sofienholm.github.io/)
- [runedrummer81.github.io](https://runedrummer81.github.io/)

Eksemplerne viser, hvordan URL'en ser ud, når sitet er publiceret med GitHub Pages.

## Før du starter

Guiden antager, at du allerede har:

- Node.js og `npm`
- VS Code
- GitHub Desktop
- en GitHub-konto

Du skal ikke oprette et Vite-projekt selv. Du skal bruge templaten.

## 1. Opret dit repository fra templaten

Gå til template-repositoryet:

[github.com/cederdorff/username.github.io](https://github.com/cederdorff/username.github.io)

Klik på:

```text
Use this template -> Create a new repository
```

Udfyld:

- `Owner`: din egen GitHub-bruger
- `Repository name`: `[dit-github-brugernavn].github.io`
- `Visibility`: `Public`

Eksempel:

```text
sofieholm.github.io
```

Klik derefter på:

```text
Create repository
```

Vigtigt:

- Brug dit eget GitHub-brugernavn i repository-navnet.
- Repository-navnet skal ende på `.github.io`.
- Brug `Use this template`, ikke `Fork`.
- Dit repository skal ikke hedde `username.github.io`, medmindre dit GitHub-brugernavn faktisk er `username`.

Forkerte eksempler:

```text
portfolio
my-portfolio
sofie-portfolio
sofieholm.github
username.github.io
```

Korrekt eksempel, hvis brugernavnet er `sofieholm`:

```text
sofieholm.github.io
```

## 2. Klon med GitHub Desktop

Når dit repository er oprettet:

1. Gå ind på dit nye repository på GitHub.
2. Kontroller igen, at repository-navnet er korrekt: `[dit-github-brugernavn].github.io`.
3. Klik på den grønne `Code`-knap.
4. Vælg `Open with GitHub Desktop`.
5. Vælg, hvor projektmappen skal ligge på din computer.
6. Klik på `Clone`.
7. Klik på `Open in Visual Studio Code` i GitHub Desktop.

Fra nu af arbejder du primært i VS Code. GitHub Desktop bruges til at committe og pushe ændringer.

## 3. Installer projektet lokalt

Åbn terminalen i VS Code:

```text
Terminal -> New Terminal
```

Kør:

```bash
npm install
```

Det installerer de packages, projektet bruger.

## 4. Start projektet lokalt

Kør:

```bash
npm run dev
```

Åbn den lokale URL i browseren. Den er typisk:

```text
http://localhost:5173
```

Tjek disse sider:

```text
http://localhost:5173/
http://localhost:5173/projects
http://localhost:5173/projects/portfolio
http://localhost:5173/about
http://localhost:5173/contact
```

Når du er færdig med at teste, kan du stoppe serveren i terminalen:

```text
Ctrl + C
```

## 5. Tilpas portfolioen

Start med disse filer:

```text
src/components/Navbar.jsx
src/pages/HomePage.jsx
src/data/projects.js
src/pages/AboutPage.jsx
src/pages/ContactPage.jsx
src/index.css
index.html
```

### Ret navn og navigation

Åbn:

```text
src/components/Navbar.jsx
```

Ret `Dit Navn` til dit eget navn.

### Ret forsiden

Åbn:

```text
src/pages/HomePage.jsx
```

Ret:

- navn
- intro-tekst
- faglig retning

### Ret projekter

Åbn:

```text
src/data/projects.js
```

Template-projekterne bruger `username` som placeholder. Ret links, så de passer til dit eget GitHub-brugernavn.

Eksempel på et projekt:

```js
{
  slug: "portfolio",
  title: "Portfolio",
  year: "2026",
  summary: "Kort tekst til projektkortet.",
  description: "Længere tekst til projektsiden.",
  tags: ["React", "Vite", "GitHub Pages"],
  image: `${import.meta.env.BASE_URL}portfolio-placeholder.svg`,
  links: [
    {
      label: "Live site",
      href: "https://username.github.io",
    },
    {
      label: "GitHub repo",
      href: "https://github.com/username/username.github.io",
    },
  ],
}
```

Hvis dit GitHub-brugernavn er `sofieholm`, skal du ændre links til:

```js
href: "https://sofieholm.github.io"
href: "https://github.com/sofieholm/sofieholm.github.io"
```

`slug` bliver brugt i URL'en.

Hvis `slug` er:

```text
portfolio
```

så bliver projektets URL:

```text
/projects/portfolio
```

Brug korte slugs uden mellemrum:

```text
portfolio
todo-app
weather-app
ux-case
```

### Ret billeder

Læg projektbilleder i:

```text
public/
```

Eksempel:

```text
public/portfolio.webp
public/todo-app.webp
```

Så kan du bruge billedet i `src/data/projects.js`:

```js
image: `${import.meta.env.BASE_URL}todo-app.webp`
```

### Ret om-mig-side

Åbn:

```text
src/pages/AboutPage.jsx
```

Ret teksten, så den passer til dig.

### Ret kontaktside

Åbn:

```text
src/pages/ContactPage.jsx
```

Ret:

- mailadresse
- GitHub-link
- LinkedIn-link

Hvis dit GitHub-brugernavn er `sofieholm`, skal GitHub-linket fx være:

```text
https://github.com/sofieholm
```

### Ret design

Åbn:

```text
src/index.css
```

Her kan du ændre:

- farver
- fonte
- spacing
- layout
- knapper
- projektkort

### Ret titel og beskrivelse

Åbn:

```text
index.html
```

Ret:

- `<title>`
- `meta name="description"`

## 6. Test før du pusher

Kør:

```bash
npm run build
```

Hvis build virker, er projektet klar til commit og push.

Du kan også køre:

```bash
npm run dev
```

og klikke rundt lokalt en sidste gang.

## 7. Commit og push med GitHub Desktop

Gå til GitHub Desktop.

1. Tjek at ændringerne vises i venstre side.
2. Skriv en kort commit-besked, fx `Customize portfolio`.
3. Klik på `Commit to main`.
4. Klik på `Push origin`.

## 8. Slå GitHub Pages til

Første gang skal GitHub Pages sættes til GitHub Actions.

Gå til dit repository på GitHub:

```text
Settings -> Pages
```

Vælg:

```text
Source: GitHub Actions
```

Når du har pushet til `main`, kører deployment automatisk.

Du kan se deployment under:

```text
Actions
```

Når deployment er færdig, ligger portfolioen på:

```text
https://[dit-github-brugernavn].github.io
```

Det kan tage et par minutter, før siden er online.

## 9. Når du vil opdatere portfolioen

Hver gang du vil ændre portfolioen:

1. Ret filerne i VS Code.
2. Test lokalt med `npm run dev`.
3. Kør gerne `npm run build`.
4. Commit og push med GitHub Desktop.
5. GitHub Actions deployer automatisk.

## Typiske fejl

### Repositoryet har forkert navn

Hvis dit GitHub-brugernavn er `sofieholm`, skal repositoryet hedde:

```text
sofieholm.github.io
```

Ikke:

```text
portfolio
sofie-portfolio
sofieholm.github
username.github.io
```

### Siden er ikke online

Tjek:

- at du har pushet til `main`
- at `Actions` er kørt færdig uden fejl
- at `Settings -> Pages -> Source` står til `GitHub Actions`
- at repositoryet er `Public`

### Et projektlink virker ikke

Tjek:

- at `slug` i `src/data/projects.js` ikke har mellemrum
- at linket matcher projektets slug
- at projektet findes i arrayet
- at du har skiftet `username` ud med dit eget GitHub-brugernavn i links

## Til underviseren

Template-repositoryet er:

[github.com/cederdorff/username.github.io](https://github.com/cederdorff/username.github.io)

For at de studerende kan bruge repoet som template:

1. Gå til repositoryets `Settings`.
2. Gå til `General`.
3. Slå `Template repository` til.

Når det er slået til, kan de studerende oprette deres eget `[dit-github-brugernavn].github.io` repository direkte fra templaten.

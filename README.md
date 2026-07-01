# username.github.io

Dette repository er en React portfolio-template til GitHub Pages.

Brug templaten til at oprette dit eget repository med navnet:

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

Billederne i guiden bruger GitHub-brugeren `race-js` som eksempel. Derfor hedder eksemplets repository `race-js.github.io`, og den deployede portfolio ligger på `https://race-js.github.io`. Du skal bruge dit eget GitHub-brugernavn i stedet.

![Template-repository med Use this template-menuen åben](docs/images/use-template-menu.png)

## Hvad templaten indeholder

- Vite + React
- React Router til sider og navigation
- sider til forside, projekter, projektdetaljer, om mig, kontakt og 404
- projektdata i `src/data/projects.js`
- styling i `src/index.css`
- automatisk deployment til GitHub Pages med `.github/workflows/deploy.yml`

## Eksempler på deployede portfolioer

Her er eksempler på portfolioer, der er deployet på samme type URL:

- [stinelock.github.io](https://stinelock.github.io/)
- [sofienholm.github.io](https://sofienholm.github.io/)
- [runedrummer81.github.io](https://runedrummer81.github.io/)

Eksemplerne viser, hvordan URL'en ser ud, når sitet er publiceret med GitHub Pages.

## Før du starter

Guiden antager, at du allerede har:

- Node.js og `npm`
- VS Code
- GitHub Desktop eller Git i VS Code
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

![Opret nyt repository fra templaten](docs/images/create-repository-from-template.png)

Billedet viser eksemplet med GitHub-brugeren `race-js`. Derfor oprettes repositoryet som `race-js.github.io`, og portfolioen kommer til at ligge på `https://race-js.github.io`.

Klik derefter på:

```text
Create repository
```

GitHub opretter nu dit repository. Det tager normalt kun et øjeblik.

![GitHub genererer det nye repository](docs/images/generating-repository.png)

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

![Open with GitHub Desktop fra dit nye repository](docs/images/open-with-github-desktop.png)

På billedet hedder repositoryet `race-js.github.io`, fordi eksemplet bruger GitHub-brugeren `race-js`.

GitHub Desktop åbner nu et vindue, hvor du kan vælge, hvor projektmappen skal ligge på din computer.

![Klon repository i GitHub Desktop](docs/images/github-desktop-clone.png)

Klik på:

```text
Clone
```

Når projektet er klonet, skal du klikke på:

```text
Open in Visual Studio Code
```

Fra nu af arbejder du primært i VS Code. Du kan committe og pushe med GitHub Desktop eller med Source Control i VS Code.

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

VS Code viser nu en lokal URL i terminalen. Den er typisk:

```text
http://localhost:5173
```

![VS Code med npm install og npm run dev](docs/images/vscode-install-and-dev-server.png)

Åbn den lokale URL i browseren.

![Portfolioen vist lokalt i browseren](docs/images/localhost-before-change.png)

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

## 5. Lav en lille ændring

Før du tilpasser hele portfolioen, skal du lave én lille ændring og deploye den. På den måde tester du hurtigt, at GitHub Pages virker.

Åbn:

```text
src/pages/HomePage.jsx
```

Find teksten:

```jsx
<h1>Hej, jeg hedder Dit Navn.</h1>
```

Ret den til noget simpelt, fx:

```jsx
<h1>Hej, jeg hedder Sofie.</h1>
```

Gem filen.

![Ret navnet i HomePage.jsx](docs/images/vscode-edit-homepage-name.png)

## 6. Test før du pusher første gang

Kør:

```bash
npm run dev
```

Åbn siden i browseren:

```text
http://localhost:5173/
```

Tjek at din lille tekstændring vises.

Når det virker, kan du stoppe serveren i terminalen:

```text
Ctrl + C
```

## 7. Slå GitHub Pages til

Første gang skal GitHub Pages sættes til GitHub Actions.

Gå til dit repository på GitHub:

```text
Settings -> Pages
```

Vælg:

```text
Source: GitHub Actions
```

Når din første deployment er kørt, kan du også se den live URL på denne side.

## 8. Commit og push

Brug enten GitHub Desktop eller Source Control i VS Code.

Med GitHub Desktop:

1. Tjek at ændringerne vises i venstre side.
2. Skriv en kort commit-besked, fx `Test GitHub Pages deployment`.
3. Klik på `Commit to main`.
4. Klik på `Push origin`.

Med VS Code:

1. Gå til `Source Control` i venstre side.
2. Tjek at ændringerne vises.
3. Skriv en kort commit-besked, fx `Test GitHub Pages deployment`.
4. Klik på `Commit`.
5. Klik på `Sync Changes` eller `Push`.

![Commit den lille ændring i VS Code](docs/images/vscode-commit-small-change.png)

Når du har pushet til `main`, kører deployment automatisk.

Du kan se deployment under:

```text
Actions
```

![GitHub Actions kører deployment](docs/images/github-actions-running.png)

Når workflowet er færdigt, skal det være grønt.

![GitHub Actions er færdig uden fejl](docs/images/github-actions-success-list.png)

Du kan klikke ind på workflowet og se selve deploy-linket.

![Deploy-workflow med link til den publicerede side](docs/images/github-actions-success-detail.png)

Når deployment er færdig, ligger portfolioen på:

```text
https://[dit-github-brugernavn].github.io
```

Det kan tage et par minutter, før siden er online.

## 9. Tjek din første deploy

Åbn din portfolio i browseren:

```text
https://[dit-github-brugernavn].github.io
```

Tjek at den lille tekstændring fra trin 5 er synlig online.

![Portfolioen er publiceret på GitHub Pages](docs/images/deployed-after-change.png)

Billedet viser den deployede portfolio på `https://race-js.github.io`, fordi eksemplet er lavet med GitHub-brugeren `race-js`.

Hvis du kan se ændringen, virker deployment.

Du kan også se den publicerede URL under:

```text
Settings -> Pages
```

![GitHub Pages viser den publicerede URL](docs/images/github-pages-settings.png)

## 10. Tilpas portfolioen

Når deployment virker, kan du begynde at gøre portfolioen personlig.

Templaten er lavet, så du kan bruge de eksisterende sider, komponenter, projekter og styles som udgangspunkt. Start med at ændre lidt ad gangen, test lokalt, og byg videre på det, der allerede virker.

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

### Brug navigationen som template

Åbn:

```text
src/components/Navbar.jsx
```

Ret `Dit Navn` til dit eget navn. Du kan også bruge de eksisterende links som template, hvis du senere vil tilføje flere sider.

### Brug forsiden som template

Åbn:

```text
src/pages/HomePage.jsx
```

Brug den eksisterende struktur som udgangspunkt, og ret:

- navn
- intro-tekst
- faglig retning

### Brug projekterne som template

Åbn:

```text
src/data/projects.js
```

Hvert projekt i listen er en template, du kan kopiere, ændre eller slette. Template-projekterne bruger `username` som placeholder. Ret links, så de passer til dit eget GitHub-brugernavn.

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

### Brug billederne som template

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

### Brug om-mig-siden som template

Åbn:

```text
src/pages/AboutPage.jsx
```

Brug teksten som udgangspunkt, og skriv den om, så den passer til dig.

### Brug kontaktsiden som template

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

### Brug designet som template

Åbn:

```text
src/index.css
```

Her kan du bygge videre på det eksisterende design og ændre:

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

## 11. Når du vil opdatere portfolioen

Hver gang du vil ændre portfolioen:

1. Ret filerne i VS Code.
2. Test lokalt med `npm run dev`.
3. Kør gerne `npm run build`.
4. Commit og push med GitHub Desktop eller VS Code.
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

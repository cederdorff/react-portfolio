# React Portfolio Template

Denne guide hjælper dig med at lave en simpel React portfolio, som automatisk deployes til GitHub Pages.

Portfolioen skal ligge på:

```text
https://[brugernavn].github.io
```

Derfor skal dit repository hedde præcis:

```text
[brugernavn].github.io
```

## Hvad du ender med

Når du er færdig, har du:

- et Vite + React projekt
- React Router til sider og navigation
- en forside
- en projektside
- en projektdetaljeside
- en om-mig-side
- en kontaktside
- automatisk deployment til GitHub Pages, når du pusher til `main`

## Eksempler fra tidligere studerende

Når portfolioen er deployet, kommer den til at ligge på:

```text
https://[brugernavn].github.io
```

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

## 1. Opret repository på GitHub

Opret et nyt repository på GitHub.

Repository-navnet skal være dit GitHub-brugernavn efterfulgt af `.github.io`:

```text
[brugernavn].github.io
```

Hvis dit GitHub-brugernavn er `sofieholm`, skal repository-navnet være:

```text
sofieholm.github.io
```

Vælg:

- `Public`

Klik derefter på `Create repository`.

## 2. Klon med GitHub Desktop

Når repositoryet er oprettet:

1. Gå ind på dit nye repository på GitHub.
2. Kontroller, at repository-navnet er fuldstændig magen til dit GitHub-brugernavn efterfulgt af `.github.io`.
3. Klik på den grønne `Code`-knap.
4. Vælg `Open with GitHub Desktop`.
5. Vælg, hvor projektmappen skal ligge på din computer.
6. Klik på `Clone`.
7. Klik på `Open in Visual Studio Code` i GitHub Desktop.

Eksempel:

```text
sofieholm.github.io
```

Hvis dit brugernavn er `sofieholm`, må repoet ikke hedde:

```text
portfolio
sofie-portfolio
sofieholm
sofieholm.github
```

Fra nu af arbejder du primært i VS Code. GitHub Desktop bruges til at committe og pushe ændringer.

## 3. Opret React-projekt med Vite

Åbn terminalen i VS Code:

```text
Terminal -> New Terminal
```

Kør denne kommando:

```bash
npm create vite@latest .
```

Vigtigt: punktummet til sidst skal med.

Punktummet betyder, at Vite skal oprette React-projektet i den mappe, du allerede står i. Hvis du glemmer punktummet, kan du komme til at oprette en ekstra mappe inde i portfolio-mappen.

Når Vite spørger, skal du vælge:

```text
Ok to proceed? y
Current directory is not empty: Ignore files and continue
Framework: React
Variant: JavaScript
Use ESLint instead of Oxlint? No (Oxlint)
Install with npm and start now? Yes
```

Hvis du valgte `Yes`, starter Vite automatisk projektet.

Åbn den lokale URL i browseren. Den er typisk:

```text
http://localhost:5173
```

Når du kan se Vite-startsiden, virker projektet.

Stop udviklingsserveren igen i terminalen:

```text
Ctrl + C
```

## 4. Installer React Router

Kør denne kommando i terminalen i VS Code:

```bash
npm install react-router
```

## 5. Første iteration: ryd op og vis en forside

Nu skal Vite-startsiden erstattes med en enkel portfolio-forside.

I denne iteration gør du kun tre ting:

1. Sletter Vite-demoen.
2. Opretter `HomePage.jsx`.
3. Sætter React Router op, så forsiden vises.

### 5.1 Slet Vite-demoen

Gør det i VS Code:

1. Find filerne i Explorer-panelet i venstre side.
2. Højreklik på filen eller mappen.
3. Vælg `Delete`.

Slet disse, hvis de findes:

```text
src/assets/
src/App.css
public/icons.svg
public/vite.svg
```

Behold disse filer:

```text
src/App.jsx
src/main.jsx
src/index.css
index.html
vite.config.js
package.json
```

### 5.2 Opret `src/pages/HomePage.jsx`

I VS Code Explorer:

1. Højreklik på `src`.
2. Vælg `New Folder`.
3. Skriv `pages`.
4. Tryk `Enter`.
5. Højreklik på `pages`.
6. Vælg `New File`.
7. Skriv `HomePage.jsx`.

Indsæt denne kode i `src/pages/HomePage.jsx`:

```jsx
function HomePage() {
  return (
    <main className="page">
      <section className="hero-section">
        <p className="eyebrow">Portfolio</p>
        <h1>Hej, jeg hedder Dit Navn.</h1>
        <p className="hero-text">
          Jeg arbejder med frontend, design og digitale produkter. Her samler
          jeg projekter, proces og det, jeg lærer undervejs.
        </p>
      </section>
    </main>
  );
}

export default HomePage;
```

### 5.3 Erstat `src/main.jsx`

Erstat alt indhold i `src/main.jsx` med:

```jsx
import { StrictMode } from "react";
import { createRoot } from "react-dom/client";
import { BrowserRouter } from "react-router";
import App from "./App";
import "./index.css";

createRoot(document.getElementById("root")).render(
  <StrictMode>
    <BrowserRouter basename={import.meta.env.BASE_URL}>
      <App />
    </BrowserRouter>
  </StrictMode>,
);
```

### 5.4 Erstat `src/App.jsx`

Erstat alt indhold i `src/App.jsx` med:

```jsx
import { Route, Routes } from "react-router";
import HomePage from "./pages/HomePage";

function App() {
  return (
    <Routes>
      <Route path="/" element={<HomePage />} />
    </Routes>
  );
}

export default App;
```

### 5.5 Erstat `src/index.css`

Erstat alt indhold i `src/index.css` med denne midlertidige CSS:

```css
:root {
  font-family: system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
  color: #1d2430;
  background: #f7f4ef;
}

* {
  box-sizing: border-box;
}

body {
  margin: 0;
}

.page {
  width: min(100% - 2rem, 1120px);
  margin: 0 auto;
  padding: 4rem 0;
}

.hero-section {
  display: grid;
  gap: 1rem;
  min-height: 70vh;
  align-content: center;
}

.eyebrow {
  margin: 0;
  color: #7c3aed;
  font-size: 0.78rem;
  font-weight: 800;
  text-transform: uppercase;
}

h1 {
  max-width: 760px;
  margin: 0;
  color: #111827;
  font-size: clamp(2.6rem, 8vw, 5.5rem);
  line-height: 0.95;
}

.hero-text {
  max-width: 680px;
  color: #526173;
  font-size: 1.15rem;
  line-height: 1.65;
}
```

### 5.6 Test første iteration

Kør:

```bash
npm run dev
```

Åbn:

```text
http://localhost:5173/
```

Du skal nu se en simpel portfolio-forside.

Hvis det virker, så stop serveren:

```text
Ctrl + C
```

## 6. Anden iteration: tilføj navigation og sider

Nu har du en fungerende forside. Næste trin er navigation og flere sider.

### 6.1 Opret `src/components/Navbar.jsx`

I VS Code Explorer:

1. Højreklik på `src`.
2. Vælg `New Folder`.
3. Skriv `components`.
4. Højreklik på `components`.
5. Vælg `New File`.
6. Skriv `Navbar.jsx`.

Indsæt denne kode:

```jsx
import { NavLink } from "react-router";

function Navbar() {
  return (
    <header className="site-header">
      <NavLink className="brand" to="/">
        Dit Navn
      </NavLink>

      <nav className="site-nav" aria-label="Primær navigation">
        <NavLink to="/" end>
          Forside
        </NavLink>
        <NavLink to="/projects">Projekter</NavLink>
        <NavLink to="/about">Om mig</NavLink>
        <NavLink to="/contact">Kontakt</NavLink>
      </nav>
    </header>
  );
}

export default Navbar;
```

### 6.2 Opret de første undersider

Opret disse filer i `src/pages`:

```text
ProjectsPage.jsx
AboutPage.jsx
ContactPage.jsx
NotFoundPage.jsx
```

Indsæt denne kode i `src/pages/ProjectsPage.jsx`:

```jsx
function ProjectsPage() {
  return (
    <div className="page narrow">
      <p className="eyebrow">Projekter</p>
      <h1>Mine projekter</h1>
      <p className="lead">
        Her kommer en oversigt over mine projekter. I næste trin tilføjer vi
        projektdata og projektkort.
      </p>
    </div>
  );
}

export default ProjectsPage;
```

Indsæt denne kode i `src/pages/AboutPage.jsx`:

```jsx
function AboutPage() {
  return (
    <div className="page narrow">
      <p className="eyebrow">Om mig</p>
      <h1>Hvem er jeg?</h1>
      <p className="lead">
        Skriv kort om din faglige retning, dine interesser og hvad du gerne vil
        blive bedre til.
      </p>
    </div>
  );
}

export default AboutPage;
```

Indsæt denne kode i `src/pages/ContactPage.jsx`:

```jsx
function ContactPage() {
  return (
    <div className="page narrow">
      <p className="eyebrow">Kontakt</p>
      <h1>Lad os tale sammen.</h1>
      <p className="lead">
        Tilpas links og mailadresse, så siden peger på dine egne profiler.
      </p>
    </div>
  );
}

export default ContactPage;
```

Indsæt denne kode i `src/pages/NotFoundPage.jsx`:

```jsx
import { Link } from "react-router";

function NotFoundPage() {
  return (
    <div className="page narrow">
      <p className="eyebrow">404</p>
      <h1>Siden blev ikke fundet</h1>
      <p className="lead">
        Linket peger på en side, der ikke findes i portfolioen.
      </p>
      <Link className="button" to="/">
        Gå til forsiden
      </Link>
    </div>
  );
}

export default NotFoundPage;
```

### 6.3 Erstat `src/App.jsx`

Erstat alt indhold i `src/App.jsx` med:

```jsx
import { Route, Routes } from "react-router";
import Navbar from "./components/Navbar";
import AboutPage from "./pages/AboutPage";
import ContactPage from "./pages/ContactPage";
import HomePage from "./pages/HomePage";
import NotFoundPage from "./pages/NotFoundPage";
import ProjectsPage from "./pages/ProjectsPage";

function App() {
  return (
    <>
      <Navbar />

      <main>
        <Routes>
          <Route path="/" element={<HomePage />} />
          <Route path="/projects" element={<ProjectsPage />} />
          <Route path="/about" element={<AboutPage />} />
          <Route path="/contact" element={<ContactPage />} />
          <Route path="*" element={<NotFoundPage />} />
        </Routes>
      </main>
    </>
  );
}

export default App;
```

### 6.4 Test anden iteration

Kør:

```bash
npm run dev
```

Tjek disse sider:

```text
http://localhost:5173/
http://localhost:5173/projects
http://localhost:5173/about
http://localhost:5173/contact
```

Klik også rundt i navigationen.

Hvis det virker, så stop serveren:

```text
Ctrl + C
```

## 7. Tredje iteration: tilføj projekter

Nu skal portfolioen have projektdata, projektkort og en projektdetaljeside.

### 7.1 Opret `src/data/projects.js`

I VS Code Explorer:

1. Højreklik på `src`.
2. Vælg `New Folder`.
3. Skriv `data`.
4. Højreklik på `data`.
5. Vælg `New File`.
6. Skriv `projects.js`.

Indsæt denne kode:

```js
const projects = [
  {
    slug: "portfolio",
    title: "Portfolio",
    year: "2026",
    summary: "En personlig portfolio bygget med React, Vite og GitHub Pages.",
    description:
      "Portfolioen viser udvalgte projekter og fungerer som et udgangspunkt for at arbejde med komponenter, routing, styling og deployment.",
    tags: ["React", "Vite", "GitHub Pages"],
    image: `${import.meta.env.BASE_URL}portfolio-placeholder.svg`,
    links: [
      {
        label: "Live site",
        href: "https://brugernavn.github.io",
      },
      {
        label: "GitHub repo",
        href: "https://github.com/brugernavn/brugernavn.github.io",
      },
    ],
  },
  {
    slug: "case-study",
    title: "Case study",
    year: "2026",
    summary: "Et projektkort, som du kan kopiere og ændre til dit eget projekt.",
    description:
      "Beskriv problemet, processen, din rolle, de vigtigste valg og hvad du lærte. Gør projektet konkret, så andre kan forstå dit arbejde.",
    tags: ["Design", "Frontend", "Proces"],
    image: `${import.meta.env.BASE_URL}portfolio-placeholder.svg`,
    links: [
      {
        label: "Eksempel-link",
        href: "https://github.com",
      },
    ],
  },
];

export default projects;
```

### 7.2 Opret `public/portfolio-placeholder.svg`

I VS Code Explorer:

1. Højreklik på `public`.
2. Vælg `New File`.
3. Skriv `portfolio-placeholder.svg`.

Indsæt denne kode:

```svg
<svg width="1200" height="750" viewBox="0 0 1200 750" fill="none" xmlns="http://www.w3.org/2000/svg">
  <rect width="1200" height="750" fill="#EDE7DD"/>
  <rect x="80" y="76" width="1040" height="598" rx="28" fill="#FFFAF3" stroke="#D8CFC1" stroke-width="4"/>
  <rect x="132" y="132" width="360" height="34" rx="17" fill="#111827"/>
  <rect x="132" y="196" width="620" height="24" rx="12" fill="#CBD5E1"/>
  <rect x="132" y="240" width="520" height="24" rx="12" fill="#CBD5E1"/>
  <rect x="132" y="326" width="270" height="64" rx="32" fill="#7C3AED"/>
  <rect x="132" y="470" width="936" height="124" rx="20" fill="#F1E9DD"/>
  <rect x="170" y="510" width="220" height="24" rx="12" fill="#94A3B8"/>
  <rect x="170" y="552" width="520" height="18" rx="9" fill="#CBD5E1"/>
  <circle cx="956" cy="242" r="112" fill="#C4B5FD"/>
  <circle cx="922" cy="222" r="34" fill="#7C3AED"/>
  <path d="M830 354C880 286 940 284 1002 354H830Z" fill="#7C3AED"/>
</svg>
```

### 7.3 Erstat `src/pages/HomePage.jsx`

Erstat alt indhold i `src/pages/HomePage.jsx` med:

```jsx
import { Link } from "react-router";
import projects from "../data/projects";

function HomePage() {
  const featuredProjects = projects.slice(0, 2);

  return (
    <div className="page">
      <section className="hero-section">
        <p className="eyebrow">Portfolio</p>
        <h1>Hej, jeg hedder Dit Navn.</h1>
        <p className="hero-text">
          Jeg arbejder med frontend, design og digitale produkter. Her samler
          jeg projekter, proces og det, jeg lærer undervejs.
        </p>
        <div className="actions">
          <Link className="button" to="/projects">
            Se projekter
          </Link>
          <Link className="button secondary" to="/contact">
            Kontakt mig
          </Link>
        </div>
      </section>

      <section className="section">
        <div className="section-heading">
          <p className="eyebrow">Udvalgte projekter</p>
          <h2>Start med få projekter og gør dem stærke.</h2>
        </div>

        <div className="project-grid">
          {featuredProjects.map((project) => (
            <article className="project-card" key={project.slug}>
              <img src={project.image} alt={`Preview af ${project.title}`} />
              <div className="project-card-content">
                <p className="eyebrow">{project.year}</p>
                <h3>{project.title}</h3>
                <p>{project.summary}</p>
                <Link to={`/projects/${project.slug}`}>Læs mere</Link>
              </div>
            </article>
          ))}
        </div>
      </section>
    </div>
  );
}

export default HomePage;
```

### 7.4 Erstat `src/pages/ProjectsPage.jsx`

Erstat alt indhold i `src/pages/ProjectsPage.jsx` med:

```jsx
import { Link } from "react-router";
import projects from "../data/projects";

function ProjectsPage() {
  return (
    <div className="page">
      <section className="section intro">
        <p className="eyebrow">Projekter</p>
        <h1>Mine projekter</h1>
        <p>
          Udskift eksemplerne med dine egne projekter. Brug korte beskrivelser,
          tydelige billeder og links til live versioner eller GitHub repos.
        </p>
      </section>

      <section className="project-grid" aria-label="Projektliste">
        {projects.map((project) => (
          <article className="project-card" key={project.slug}>
            <img src={project.image} alt={`Preview af ${project.title}`} />
            <div className="project-card-content">
              <p className="eyebrow">{project.year}</p>
              <h2>{project.title}</h2>
              <p>{project.summary}</p>
              <ul className="tag-list">
                {project.tags.map((tag) => (
                  <li key={tag}>{tag}</li>
                ))}
              </ul>
              <Link to={`/projects/${project.slug}`}>Se projekt</Link>
            </div>
          </article>
        ))}
      </section>
    </div>
  );
}

export default ProjectsPage;
```

### 7.5 Opret `src/pages/ProjectPage.jsx`

I `src/pages` skal du oprette filen:

```text
ProjectPage.jsx
```

Indsæt denne kode:

```jsx
import { Link, useParams } from "react-router";
import projects from "../data/projects";

function ProjectPage() {
  const { slug } = useParams();
  const project = projects.find((item) => item.slug === slug);

  if (!project) {
    return (
      <div className="page narrow">
        <p className="eyebrow">404</p>
        <h1>Projektet blev ikke fundet</h1>
        <p>Det projekt findes ikke i listen endnu.</p>
        <Link className="button" to="/projects">
          Tilbage til projekter
        </Link>
      </div>
    );
  }

  return (
    <article className="page narrow">
      <Link className="back-link" to="/projects">
        Tilbage til projekter
      </Link>

      <img className="detail-image" src={project.image} alt="" />
      <p className="eyebrow">{project.year}</p>
      <h1>{project.title}</h1>
      <p className="lead">{project.description}</p>

      <ul className="tag-list">
        {project.tags.map((tag) => (
          <li key={tag}>{tag}</li>
        ))}
      </ul>

      <div className="actions">
        {project.links.map((link) => (
          <a
            className="button secondary"
            href={link.href}
            key={link.href}
            rel="noreferrer"
            target="_blank"
          >
            {link.label}
          </a>
        ))}
      </div>
    </article>
  );
}

export default ProjectPage;
```

### 7.6 Erstat `src/App.jsx`

Erstat alt indhold i `src/App.jsx` med:

```jsx
import { Route, Routes } from "react-router";
import Navbar from "./components/Navbar";
import AboutPage from "./pages/AboutPage";
import ContactPage from "./pages/ContactPage";
import HomePage from "./pages/HomePage";
import NotFoundPage from "./pages/NotFoundPage";
import ProjectPage from "./pages/ProjectPage";
import ProjectsPage from "./pages/ProjectsPage";

function App() {
  return (
    <>
      <Navbar />

      <main>
        <Routes>
          <Route path="/" element={<HomePage />} />
          <Route path="/projects" element={<ProjectsPage />} />
          <Route path="/projects/:slug" element={<ProjectPage />} />
          <Route path="/about" element={<AboutPage />} />
          <Route path="/contact" element={<ContactPage />} />
          <Route path="*" element={<NotFoundPage />} />
        </Routes>
      </main>
    </>
  );
}

export default App;
```

### 7.7 Test tredje iteration

Kør:

```bash
npm run dev
```

Tjek:

```text
http://localhost:5173/projects
http://localhost:5173/projects/portfolio
http://localhost:5173/projects/case-study
```

Hvis det virker, så stop serveren:

```text
Ctrl + C
```

## 8. Fjerde iteration: gør de sidste sider færdige

Nu kan du gøre om-mig-siden og kontaktsiden lidt mere brugbare.

### 8.1 Erstat `src/pages/AboutPage.jsx`

Erstat alt indhold i `src/pages/AboutPage.jsx` med:

```jsx
function AboutPage() {
  return (
    <div className="page narrow">
      <p className="eyebrow">Om mig</p>
      <h1>Hvem er jeg?</h1>
      <p className="lead">
        Skriv kort om din faglige retning, dine interesser og hvad du gerne vil
        blive bedre til. Hold teksten konkret og personlig.
      </p>

      <section className="info-list" aria-label="Om mig detaljer">
        <div>
          <h2>Jeg arbejder med</h2>
          <p>React, HTML, CSS, JavaScript, designproces og digitale produkter.</p>
        </div>
        <div>
          <h2>Jeg er nysgerrig på</h2>
          <p>Brugeroplevelser, visuel identitet og hvordan kode bliver til noget brugbart.</p>
        </div>
      </section>
    </div>
  );
}

export default AboutPage;
```

### 8.2 Erstat `src/pages/ContactPage.jsx`

Erstat alt indhold i `src/pages/ContactPage.jsx` med:

```jsx
function ContactPage() {
  return (
    <div className="page narrow">
      <p className="eyebrow">Kontakt</p>
      <h1>Lad os tale sammen.</h1>
      <p className="lead">
        Tilpas links og mailadresse, så siden peger på dine egne profiler.
      </p>

      <ul className="contact-list">
        <li>
          <a href="mailto:dinmail@example.com">dinmail@example.com</a>
        </li>
        <li>
          <a href="https://github.com/brugernavn" rel="noreferrer" target="_blank">
            GitHub
          </a>
        </li>
        <li>
          <a href="https://www.linkedin.com" rel="noreferrer" target="_blank">
            LinkedIn
          </a>
        </li>
      </ul>
    </div>
  );
}

export default ContactPage;
```

### 8.3 Test fjerde iteration

Kør:

```bash
npm run dev
```

Tjek:

```text
http://localhost:5173/about
http://localhost:5173/contact
```

Hvis det virker, så stop serveren.

## 9. Femte iteration: tilføj færdig CSS

Nu erstatter du den midlertidige CSS med en mere komplet start-CSS.

Erstat alt indhold i `src/index.css` med:

```css
:root {
  font-family: Inter, ui-sans-serif, system-ui, -apple-system, BlinkMacSystemFont,
    "Segoe UI", sans-serif;
  color: #1d2430;
  background: #f7f4ef;
  font-synthesis: none;
  text-rendering: optimizeLegibility;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

* {
  box-sizing: border-box;
}

body {
  margin: 0;
  min-width: 320px;
}

a {
  color: inherit;
}

img {
  display: block;
  max-width: 100%;
}

button,
input,
textarea {
  font: inherit;
}

.site-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 1rem;
  width: min(100% - 2rem, 1120px);
  margin: 0 auto;
  padding: 1.25rem 0;
}

.brand {
  color: #111827;
  font-weight: 800;
  text-decoration: none;
}

.site-nav {
  display: flex;
  flex-wrap: wrap;
  justify-content: flex-end;
  gap: 0.25rem;
}

.site-nav a {
  border-radius: 999px;
  color: #475569;
  padding: 0.55rem 0.8rem;
  text-decoration: none;
}

.site-nav a.active,
.site-nav a:hover {
  color: #111827;
  background: #ffffff;
}

.page {
  width: min(100% - 2rem, 1120px);
  margin: 0 auto;
  padding: 3rem 0 5rem;
}

.narrow {
  width: min(100% - 2rem, 760px);
}

.hero-section {
  display: grid;
  gap: 1.5rem;
  align-content: center;
  min-height: 58svh;
  padding: 3rem 0;
}

.section {
  padding: 3rem 0;
}

.section-heading {
  display: grid;
  gap: 0.5rem;
  max-width: 640px;
  margin-bottom: 1.5rem;
}

.intro {
  max-width: 720px;
}

.eyebrow {
  margin: 0;
  color: #7c3aed;
  font-size: 0.78rem;
  font-weight: 800;
  letter-spacing: 0;
  text-transform: uppercase;
}

h1,
h2,
h3,
p {
  margin-top: 0;
}

h1 {
  max-width: 760px;
  margin-bottom: 1rem;
  color: #111827;
  font-size: clamp(2.6rem, 8vw, 5.5rem);
  line-height: 0.95;
  letter-spacing: 0;
}

h2 {
  margin-bottom: 0.75rem;
  color: #111827;
  font-size: clamp(1.6rem, 4vw, 2.4rem);
  line-height: 1.05;
  letter-spacing: 0;
}

h3 {
  margin-bottom: 0.6rem;
  color: #111827;
  font-size: 1.35rem;
  letter-spacing: 0;
}

p {
  color: #526173;
  line-height: 1.65;
}

.hero-text,
.lead {
  max-width: 680px;
  font-size: 1.15rem;
}

.actions {
  display: flex;
  flex-wrap: wrap;
  gap: 0.75rem;
  margin-top: 0.5rem;
}

.button {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  min-height: 2.75rem;
  border: 1px solid #111827;
  border-radius: 999px;
  color: #ffffff;
  background: #111827;
  padding: 0.7rem 1rem;
  font-weight: 700;
  text-decoration: none;
}

.button.secondary {
  color: #111827;
  background: transparent;
}

.project-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
  gap: 1rem;
}

.project-card {
  overflow: hidden;
  border: 1px solid #e5ddd2;
  border-radius: 0.75rem;
  background: #fffaf3;
}

.project-card img {
  width: 100%;
  aspect-ratio: 16 / 10;
  object-fit: cover;
}

.project-card-content {
  padding: 1.1rem;
}

.project-card a {
  color: #5b21b6;
  font-weight: 800;
}

.detail-image {
  width: 100%;
  aspect-ratio: 16 / 9;
  border-radius: 0.75rem;
  object-fit: cover;
  margin-bottom: 2rem;
}

.back-link {
  display: inline-flex;
  margin-bottom: 1.5rem;
  color: #5b21b6;
  font-weight: 800;
}

.tag-list {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
  padding: 0;
  margin: 1.25rem 0;
  list-style: none;
}

.tag-list li {
  border: 1px solid #ded6ca;
  border-radius: 999px;
  background: #ffffff;
  color: #475569;
  padding: 0.35rem 0.7rem;
  font-size: 0.9rem;
  font-weight: 700;
}

.info-list {
  display: grid;
  gap: 1rem;
  margin-top: 2rem;
}

.info-list div,
.contact-list {
  border: 1px solid #e5ddd2;
  border-radius: 0.75rem;
  background: #fffaf3;
  padding: 1rem;
}

.info-list h2 {
  font-size: 1.15rem;
}

.contact-list {
  display: grid;
  gap: 0.75rem;
  padding-left: 2rem;
}

.contact-list a {
  color: #5b21b6;
  font-weight: 800;
}

@media (max-width: 720px) {
  .site-header {
    align-items: flex-start;
    flex-direction: column;
  }

  .site-nav {
    justify-content: flex-start;
  }

  .page {
    padding-top: 2rem;
  }

  .hero-section {
    min-height: auto;
    padding-top: 2rem;
  }
}
```

Test igen:

```bash
npm run dev
```

Klik rundt på siderne. Hvis layoutet ser rigtigt ud, stop serveren igen.

## 10. Sjette iteration: klargør HTML og Vite config

### 10.1 Erstat `index.html`

Erstat alt indhold i `index.html` med:

```html
<!doctype html>
<html lang="da">
  <head>
    <meta charset="UTF-8" />
    <link rel="icon" type="image/svg+xml" href="/favicon.svg" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <meta
      name="description"
      content="En simpel React portfolio-template til GitHub Pages."
    />
    <title>React Portfolio Template</title>
  </head>
  <body>
    <div id="root"></div>
    <script type="module" src="/src/main.jsx"></script>
  </body>
</html>
```

### 10.2 Erstat `vite.config.js`

Erstat alt indhold i `vite.config.js` med:

```js
import { defineConfig } from "vite";
import react from "@vitejs/plugin-react";

export default defineConfig({
  plugins: [react()],
  base: "/",
});
```

### 10.3 Test build

Kør:

```bash
npm run build
```

Hvis build virker, er selve React-projektet klar.

## 11. Syvende iteration: tilføj automatisk deployment

Nu skal projektet deployes automatisk til GitHub Pages, når du pusher til `main`.

### 11.1 Opret `.github/workflows/deploy.yml`

Gør det i VS Code Explorer:

1. Højreklik i projektets rodmappe.
2. Vælg `New Folder`.
3. Skriv `.github`.
4. Højreklik på `.github`.
5. Vælg `New Folder`.
6. Skriv `workflows`.
7. Højreklik på `workflows`.
8. Vælg `New File`.
9. Skriv `deploy.yml`.

Indsæt denne kode i `.github/workflows/deploy.yml`:

```yaml
name: Deploy to GitHub Pages

on:
  push:
    branches: [main]
  workflow_dispatch:

permissions:
  contents: read
  pages: write
  id-token: write

concurrency:
  group: pages
  cancel-in-progress: false

jobs:
  build:
    name: Build
    runs-on: ubuntu-latest

    steps:
      - name: Checkout
        uses: actions/checkout@v6

      - name: Setup Node
        uses: actions/setup-node@v6
        with:
          node-version: 24
          cache: npm

      - name: Install dependencies
        run: npm ci

      - name: Build
        run: npm run build

      - name: Add SPA fallback
        run: cp dist/index.html dist/404.html

      - name: Configure GitHub Pages
        uses: actions/configure-pages@v5

      - name: Upload Pages artifact
        uses: actions/upload-pages-artifact@v5
        with:
          path: dist

  deploy:
    name: Deploy
    needs: build
    runs-on: ubuntu-latest
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}

    steps:
      - name: Deploy to GitHub Pages
        id: deployment
        uses: actions/deploy-pages@v4
```

### 11.2 Test build igen

Kør:

```bash
npm run build
```

Hvis build virker, er projektet klar til commit og push.

## 12. Tjek den færdige struktur

Projektet skal nu ligne dette:

```text
.github/
  workflows/
    deploy.yml
public/
  favicon.svg
  portfolio-placeholder.svg
src/
  components/
    Navbar.jsx
  data/
    projects.js
  pages/
    HomePage.jsx
    ProjectsPage.jsx
    ProjectPage.jsx
    AboutPage.jsx
    ContactPage.jsx
    NotFoundPage.jsx
  App.jsx
  main.jsx
  index.css
index.html
package.json
vite.config.js
```

Hvis du stadig har `src/assets/`, `src/App.css` eller Vite-demoindhold i `src/App.jsx`, er oprydningen ikke færdig.

## 13. Commit og push med GitHub Desktop

Gå til GitHub Desktop.

1. Tjek at ændringerne vises i venstre side.
2. Skriv en kort commit-besked, fx `Add portfolio template`.
3. Klik på `Commit to main`.
4. Klik på `Push origin`.

## 14. Slå GitHub Pages til

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
https://[brugernavn].github.io
```

## 15. Ret portfolioen til

Når setuppet virker, kan du begynde at gøre portfolioen personlig.

Start her:

- Ret navn i `src/components/Navbar.jsx`.
- Ret forsidetekst i `src/pages/HomePage.jsx`.
- Ret projekter i `src/data/projects.js`.
- Ret kontaktlinks i `src/pages/ContactPage.jsx`.
- Ret farver og layout i `src/index.css`.
- Ret titel og description i `index.html`.

Hver gang du vil opdatere siden:

1. Ret filerne i VS Code.
2. Test med `npm run dev`.
3. Commit og push med GitHub Desktop.
4. GitHub Actions deployer automatisk.

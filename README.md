# Opsætning Af Portfolio Template Med React Og GitHub Pages

Denne guide hjælper dig med at komme hurtigt fra 0 til en online portfolio med React, Vite, React Router og GitHub Pages.

Mål:

- Få et fungerende React-projekt op at køre lokalt.
- Sætte sider og routing op.
- Deploye til GitHub Pages.
- Have en god struktur, som du kan bygge videre på.

## 1. Opret Dit Repository På GitHub

Opret et nyt repository med navnet:

- `[dit-brugernavn].github.io`

Eksempel:

- `cederdorff.github.io`

Hvorfor dette navn?

- Når repoet hedder præcis `[brugernavn].github.io`, bliver din side tilgængelig direkte på `https://[brugernavn].github.io`.

## 2. Klon Repository Og Åbn I VS Code

Kør i terminalen:

```bash
git clone https://github.com/[dit-brugernavn]/[dit-brugernavn].github.io.git
cd [dit-brugernavn].github.io
code .
```

## 3. Opret React-Projekt Med Vite I Den Eksisterende Mappe

Kør:

```bash
npm create vite@latest .
```

Vælg:

- Framework: `React`
- Variant: `JavaScript` eller `TypeScript`

Vigtigt:

- Brug `.` (punktum), så projektet installeres i den nuværende mappe.

Installer derefter dependencies:

```bash
npm install
```

## 4. Test At Projektet Kører Lokalt

```bash
npm run dev
```

Åbn den lokale URL i browseren (typisk `http://localhost:5173`).

## 5. Tilføj React Router Og Basis-Sider

Installer React Router:

```bash
npm install react-router-dom
```

Opret disse filer i `src/pages`:

- `Home.jsx`
- `Projects.jsx`
- `About.jsx`
- `Contact.jsx`
- `ProjectDetail.jsx` (til detaljer pr. projekt)

Eksempel på `src/App.jsx`:

```jsx
import { NavLink, Route, Routes } from "react-router-dom";
import Home from "./pages/Home";
import Projects from "./pages/Projects";
import ProjectDetail from "./pages/ProjectDetail";
import About from "./pages/About";
import Contact from "./pages/Contact";

function App() {
  return (
    <>
      <nav>
        <NavLink to="/" end>
          Home
        </NavLink>
        {" | "}
        <NavLink to="/projects">Projects</NavLink>
        {" | "}
        <NavLink to="/about">About</NavLink>
        {" | "}
        <NavLink to="/contact">Contact</NavLink>
      </nav>

      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/projects" element={<Projects />} />
        <Route path="/projects/:id" element={<ProjectDetail />} />
        <Route path="/about" element={<About />} />
        <Route path="/contact" element={<Contact />} />
      </Routes>
    </>
  );
}

export default App;
```

Og i `src/main.jsx`:

```jsx
import { StrictMode } from "react";
import { createRoot } from "react-dom/client";
import { BrowserRouter } from "react-router-dom";
import App from "./App";
import "./index.css";

createRoot(document.getElementById("root")).render(
  <StrictMode>
    <BrowserRouter>
      <App />
    </BrowserRouter>
  </StrictMode>
);
```

## 6. Deploy Til GitHub Pages

Installer package:

```bash
npm install -D gh-pages
```

Opdater `package.json` scripts:

```json
{
  "scripts": {
    "dev": "vite",
    "build": "vite build",
    "preview": "vite preview",
    "predeploy": "npm run build",
    "deploy": "gh-pages -d dist"
  }
}
```

### Vite Konfiguration

I `vite.config.js`:

```js
import { defineConfig } from "vite";
import react from "@vitejs/plugin-react";

export default defineConfig({
  plugins: [react()],
  base: "/"
});
```

Hvis dit repo ikke hedder `[brugernavn].github.io`, skal `base` typisk være:

- `base: "/[repo-navn]/"`

Hvis dit repo hedder `[brugernavn].github.io`, er `base: "/"` korrekt.

### Push Og Deploy

```bash
git add .
git commit -m "Initial portfolio setup"
git push origin main
npm run deploy
```

Gå derefter i GitHub:

- Repository -> `Settings` -> `Pages`
- Source: branch `gh-pages` / folder `/ (root)`

Når deploy er færdig, ligger siden på:

- `https://[dit-brugernavn].github.io`

## 7. Opbyg Portfolio-Indhold

Minimumsflow:

1. Lav en liste over projekter i `public/projects.json`.
2. Hent data i `Projects` med `fetch` + `useEffect` + `useState`.
3. Vis projekter i kort/grid.
4. Link til detaljeside via route-parametre (`/projects/:id`).
5. Brug `useParams` i `ProjectDetail` til at finde korrekt projekt.

Eksempel på objekt i `public/projects.json`:

```json
[
  {
    "id": "portfolio",
    "title": "Portfolio Website",
    "year": 2026,
    "description": "Min portfolio bygget med React.",
    "tags": ["React", "Portfolio", "Frontend"],
    "image": "/img/portfolio.webp",
    "links": [
      {
        "url": "https://[dit-brugernavn].github.io",
        "text": "Live"
      }
    ]
  }
]
```

## 8. CSS-Struktur (Pragmatisk Start)

Start simpelt, udvid senere.

Mulighed A: Global CSS

- Hurtigt i små projekter.
- Godt til reset, layout og typografi.

Mulighed B: CSS Modules

- God struktur pr. komponent.
- Undgår navnekonflikter.

Forslag:

- Brug `index.css` til globale regler.
- Brug `*.module.css` til komponent-specifik styling.

## 9. Typiske Fejl Og Hurtige Fixes

- Blank side efter deploy:
  - Tjek `base` i `vite.config.js`.
  - Tjek at `gh-pages`-branch findes.

- 404 når du refresher på en underside:
  - GitHub Pages er statisk hosting. Brug links internt via React Router, og test at routing er sat korrekt op.

- Router-import fejl:
  - Brug `react-router-dom` til `BrowserRouter`, `Routes`, `Route`, `NavLink`.

- Ændringer kommer ikke online:
  - Kør `npm run deploy` igen efter nye commits.

## 10. Klar Til Videre Arbejde

Når setuppet virker, kan du fokusere på:

- design og visuel identitet,
- bedre projektdetaljer,
- performance og accessibility,
- SEO (titel, meta-beskrivelser, semantisk HTML).

God arbejdslyst med din portfolio.

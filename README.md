# React + Vite

This template provides a minimal setup to get React working in Vite with HMR and some ESLint rules.

Currently, two official plugins are available:

- [@vitejs/plugin-react](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react) uses [Babel](https://babeljs.io/) (or [oxc](https://oxc.rs) when used in [rolldown-vite](https://vite.dev/guide/rolldown)) for Fast Refresh
- [@vitejs/plugin-react-swc](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react-swc) uses [SWC](https://swc.rs/) for Fast Refresh

## React Compiler

The React Compiler is currently not compatible with SWC. See [this issue](https://github.com/vitejs/vite-plugin-react/issues/428) for tracking the progress.

## Expanding the ESLint configuration

If you are developing a production application, we recommend using TypeScript with type-aware lint rules enabled. Check out the [TS template](https://github.com/vitejs/vite/tree/main/packages/create-vite/template-react-ts) for information on how to integrate TypeScript and [`typescript-eslint`](https://typescript-eslint.io) in your project.

## Admin interface and features (nouveau)

Cette application contient désormais une interface d'administration pour gérer les centres médicaux et les lits.

- Accéder à l'interface admin: /admin
- Fonctionnalités principales:
	- Créer un centre (nom, adresse, téléphone, type, nombre de lits)
	- Modifier / supprimer un centre
	- Gérer le nombre de lits disponibles (+ / -)
	- Les données sont persistées dans localStorage (clé: prmi_centers_v1) et peuvent être réinitialisées via le bouton seed

Instructions locales :

1. Installer les dépendances:

```bash
npm install
```

# Admin UI & FastAPI

The project includes a simple admin interface at `/admin` that manages centers and available beds. Data is stored in browser localStorage by default under the `prmi_centers_v1` key.

To prepare for a backend, a small API client is available at `src/lib/apiClient.js` which will attempt to call an API base URL (from `VITE_API_URL` environment variable) and will fall back to localStorage when the backend is not reachable.

If you want to connect to a FastAPI backend, run your FastAPI server (suggested endpoint paths: `/api/centers`) and set `VITE_API_URL=http://localhost:8000/api` in a `.env` or your environment before launching Vite.

The app also asks for geolocation permission on first entry (or when LocationGate is shown) and stores that in localStorage under `prmi_location` to center the map.

When the user shares their location the map automatically updates and the app displays a list of nearby centers (within ~8km) below the map — this uses the local centers dataset and will also work together with a FastAPI backend when configured.

There is also a small global footer shown on every page providing quick navigation links.


2. Lancer l'app en développement:

```bash
npm run dev
```

3. Ouvrir le navigateur: http://localhost:5173 (ou l'URL donnée par Vite) puis naviguer vers `/admin`

"# PRMI" 

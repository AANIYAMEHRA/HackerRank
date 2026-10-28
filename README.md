<div align="center">
<img src="docs/images/banner.svg" alt="Webcraft-IT CMS banner" width="100%" />
# Webcraft-IT Website
 
**A full-stack corporate website with a built-in admin CMS.**
Non-technical editors update the header, home page, about page and footer from a dashboard. No code changes and no redeploy.
 
<img src="https://img.shields.io/badge/React-18-102a4f?logo=react&logoColor=6ee7b7" alt="React 18" />
<img src="https://img.shields.io/badge/Vite-5-1f8a86?logo=vite&logoColor=white" alt="Vite" />
<img src="https://img.shields.io/badge/Tailwind_CSS-3-2aa27c?logo=tailwindcss&logoColor=white" alt="Tailwind CSS" />
<img src="https://img.shields.io/badge/Node.js-Express-102a4f?logo=node.js&logoColor=6ee7b7" alt="Node.js and Express" />
<img src="https://img.shields.io/badge/MongoDB-Mongoose-1f8a86?logo=mongodb&logoColor=white" alt="MongoDB and Mongoose" />
[Highlights](#-highlights) · [Features](#-features) · [Tech stack](#-tech-stack) · [Architecture](#-architecture) · [Getting started](#-getting-started) · [Screenshots](#-screenshots)
 
</div>
---
 
## 🎯 Highlights
 
- **Full-stack build:** a React 18 frontend, a Node.js and Express REST API, and MongoDB data models, all in one repository.
- **Content management system:** an admin area where editors manage four content areas of a live site without touching code.
- **Reusable admin UI:** one shared component library (fields, icon picker, dialogs, save bar) keeps every editor consistent.
- **Careful validation:** required fields are marked with a red `*`, and saving explains exactly what is missing.
- **Clean API design:** every content type has the same `GET` and `PUT` routes, backed by its own Mongoose model.
## ✨ Features
 
**Public website**
- Responsive Home and About pages with scroll-triggered animations (GSAP)
- Shared header and footer, driven by CMS content
- Logo and text update as soon as an editor saves
**Admin CMS (`/admin`)**
- Sidebar navigation with a dropdown for each page's sections, which scrolls to and expands that section
- **Header:** logo upload, navigation links, contact button
- **Home:** hero, statistics, services, why Webcraft, approach, products, AI solutions and call to action
- **About:** hero and chips, milestones, six ways, values, delivery philosophy, statistics, careers and call to action
- **Footer:** footer text and links
- Logo and icon uploads: choose an SVG and the app stores its drawing path, with a camera or pencil button for each icon
- Confirmation dialogs before any item, icon or logo is removed
- Toast notifications for every save, error and validation message
## 🛠 Tech stack
 
<img src="docs/images/tech-stack.svg" alt="Tech stack: React 18, Vite 5, Tailwind CSS 3, GSAP, Express 4, MongoDB with Mongoose 8" width="100%" />
| Layer | Technology | Why |
| --- | --- | --- |
| Frontend | React 18, React Router 6, Vite | Component-based UI, nested admin routes, fast builds |
| Styling | Tailwind CSS 3 | Consistent design tokens and responsive layouts |
| Motion | GSAP + ScrollTrigger | Smooth, scroll-linked section animations |
| Backend | Node.js, Express 4 | Lightweight REST endpoints (GET and PUT per content type) |
| Database | MongoDB, Mongoose 8 | Flexible document models for page content |
 
## 🏗 Architecture
 
<img src="docs/images/architecture.svg" alt="Architecture: the admin CMS and public site both talk to the Express API, which reads and writes MongoDB" width="100%" />
Each content type (`header`, `home`, `about`, `footer`) has its own model, route and admin page. The public pages read the same content back, so an edit appears on the live site after saving.
 
## 📁 Project structure
 
```
WebCraft_home_project/
├── src/                       # Frontend (React)
│   ├── components/            # Header, Footer, layout and admin shell
│   │   ├── AdminLayout.jsx    # Admin sidebar, navbar and save button
│   │   └── AdminUi.jsx        # Shared admin fields, icon picker and styles
│   ├── pages/                 # One file per page (public and admin)
│   ├── hooks/                 # Animation hooks
│   └── styles/                # Global styles
├── public/                    # Static files and images
├── backend/                   # Backend (Express + MongoDB)
│   ├── server.js              # Starts the server and mounts the routes
│   └── src/
│       ├── config/db.js       # Database connection
│       ├── models/            # Mongoose models (Header, Home, About, Footer)
│       └── routes/            # API routes (GET and PUT for each model)
└── docs/
    ├── images/                # README banner and diagrams
    └── screenshots/           # Screenshots used in this README
```
 
## 🚀 Getting started
 
**Prerequisites:** Node.js 18 or newer, and a MongoDB database (a local instance or MongoDB Atlas).
 
**1. Install the frontend**
 
```bash
npm install
```
 
**2. Install the backend**
 
```bash
cd backend
npm install
```
 
**3. Configure the backend**
 
Create a file named `.env` inside `backend/`. It is git-ignored, so your connection string stays private.
 
```env
MONGODB_URI=your-mongodb-connection-string
PORT=5000
```
 
**4. Run both servers**
 
In one terminal, start the backend:
 
```bash
cd backend
npm run dev
```
 
In a second terminal, start the frontend from the project root:
 
```bash
npm run dev
```
 
| What | Where |
| --- | --- |
| Public site | http://localhost:5173 |
| Admin CMS | http://localhost:5173/admin |
| Backend API | http://localhost:5000/api |
 
## 🔌 API
 
Each content type has a `GET` route to read it and a `PUT` route to save it.
 
| Method | Endpoint | Used by |
| --- | --- | --- |
| `GET` / `PUT` | `/api/header` | Header CMS and the public header |
| `GET` / `PUT` | `/api/home` | Home CMS and the public Home page |
| `GET` / `PUT` | `/api/about` | About CMS and the public About page |
| `GET` / `PUT` | `/api/footer` | Footer CMS and the public footer |
 
## 🖼 Screenshots
 
<details open>
<summary><b>Public website</b></summary>
| Home | About |
| --- | --- |
| ![Public Home page](docs/screenshots/home.png) | ![Public About page](docs/screenshots/about.png) |
 
</details>
<details open>
<summary><b>Admin CMS</b></summary>
| Dashboard | Header CMS |
| --- | --- |
| ![Admin dashboard](docs/screenshots/admin-dashboard.png) | ![Header CMS with logo settings](docs/screenshots/admin-header.png) |
 
| Home Page CMS | About Page CMS |
| --- | --- |
| ![Home Page CMS](docs/screenshots/admin-home.png) | ![About Page CMS](docs/screenshots/admin-about.png) |
 
| Footer CMS |
| --- |
| ![Footer CMS](docs/screenshots/admin-footer.png) |
 
</details>
## 🤝 Contributing
 
Contributions are welcome.
 
1. Create a branch from `feature/header-cms`.
2. Make your changes and test them locally with both servers running.
3. Commit with a short message that says what changed, for example `Add validation to Footer CMS`.
4. Open a pull request into `feature/header-cms`, and describe what changed and why.
## 👤 Author
 
**Aaniya Mehra** · [GitHub](https://github.com/AANIYAMEHRA) · [LinkedIn](https://www.linkedin.com/in/your-profile) · [Email](mailto:you@example.com)
 
Built as a full-stack project covering frontend UI, REST API design, database modelling and a custom admin CMS.
 
## 📄 License
 
Private project. All rights reserved by Webcraft-IT.

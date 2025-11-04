# RailDevHub Website

[![Deploy Astro site to GitHub Pages](https://github.com/raildevhub/raildevhub.github.io/actions/workflows/deploy.yml/badge.svg)](https://github.com/raildevhub/raildevhub.github.io/actions/workflows/deploy.yml)

The official website for RailDevHub - A specialized team combining the power of AI and software to build amazing railway projects.

**Live Site:** [https://raildevhub.github.io](https://raildevhub.github.io)

## About RailDevHub

RailDevHub is a specialized team of 15 experts dedicated to transforming railway operations through innovative AI and software engineering solutions. We focus on:

- **Security** - Enterprise-grade security for critical infrastructure
- **Performance** - High-performance systems for large-scale operations
- **Modern Design** - Intuitive, user-friendly interfaces
- **Quality Products** - Rigorous testing and production-ready solutions

## Technology Stack

- **Framework:** [Astro](https://astro.build/) - Fast, modern static site generator
- **Styling:** [TailwindCSS](https://tailwindcss.com/) - Utility-first CSS framework
- **Deployment:** GitHub Pages with GitHub Actions
- **Languages:** TypeScript, HTML, CSS

## Project Structure

```
raildevhub-web/
├── .github/
│   └── workflows/
│       └── deploy.yml          # GitHub Actions deployment
├── public/
│   └── favicon.svg            # Site favicon
├── src/
│   ├── components/
│   │   ├── Header.astro       # Navigation header
│   │   └── Footer.astro       # Site footer
│   ├── layouts/
│   │   └── BaseLayout.astro   # Base page layout
│   ├── pages/
│   │   ├── index.astro        # Home page
│   │   ├── about.astro        # About the team
│   │   ├── expertise.astro    # Technologies & expertise
│   │   └── projects.astro     # Featured projects
│   └── styles/
│       └── global.css         # Global styles
├── package.json
├── astro.config.mjs           # Astro configuration
├── tailwind.config.mjs        # TailwindCSS configuration
├── tsconfig.json              # TypeScript configuration
└── README.md
```

## Our Expertise

### Artificial Intelligence
- Large Language Models (LLM)
- AI Agents & Agent-to-Agent (A2A)
- Multi-Criteria Planning (MCP)
- Big Data Analytics

### Software Engineering
- Java & SpringBoot
- React & Modern Web
- Microservices Architecture
- PostgreSQL & MongoDB
- Kubernetes & Docker
- Linux & Elasticsearch

## Featured Projects

### 1. DDYS - Digital Railway Management System
A comprehensive microservice-based platform for TCDD (Turkish State Railways) to digitalize and centrally manage all railway sector processes for the General Directorate of Transport Services Regulation (UHDGM).

**Technologies:** Java SpringBoot, React, Microservices, PostgreSQL, Kubernetes, Docker

### 2. Resource Planning & Big Data Analytics Platform
A unified web platform for TCDD integrating AI/ML models, BI/DWH reports (Tableau), Open Data Portal (CKAN), and GIS-based live train tracking (GeoServer/OpenLayers) with Keycloak SSO and customizable dashboards.

**Technologies:** Big Data, AI/ML, Tableau, CKAN, GeoServer, OpenLayers, Keycloak, Elasticsearch

## Development

### Prerequisites

- Node.js 18+ and npm
- Git

### Setup

```bash
# Clone the repository
git clone https://github.com/raildevhub/raildevhub.github.io.git
cd raildevhub.github.io

# Install dependencies
npm install

# Start development server
npm run dev
```

The site will be available at `http://localhost:4321`

### Available Scripts

```bash
npm run dev         # Start development server
npm run build       # Build for production
npm run preview     # Preview production build locally
npm run astro       # Run Astro CLI commands
```

## Deployment

The site automatically deploys to GitHub Pages when changes are pushed to the `main` branch using GitHub Actions.

### Manual Deployment

```bash
# Build the site
npm run build

# The built site will be in the `dist/` folder
```

## Design Philosophy

The website embodies a professional, modern corporate identity with:

- **Railway-Inspired Color Palette:** Steel blue, track gray, signal red, and safety orange
- **Clean & Professional Design:** Modern layouts with smooth animations
- **Responsive Design:** Mobile-first approach ensuring excellent experience on all devices
- **Accessibility:** Clear typography, good contrast ratios, semantic HTML

## Domain Focus

We specialize in the railway sector, focusing on:
- 🚄 Trains
- 👥 Passengers
- 🏢 Stations
- ⚙️ Operations Management

All solutions comply with **European railway standards** for safety, interoperability, and quality.

## Contributing

We welcome contributions! Here's how you can help:

1. **⭐ Star the repository** to show your support
2. **🐛 Report issues** if you find bugs or have suggestions
3. **🛠️ Submit pull requests** with improvements
4. **📖 Improve documentation** by fixing typos or adding examples

### Development Guidelines

- Follow the existing code style and structure
- Write clear commit messages
- Test your changes locally before submitting
- Update documentation if needed

## License

This project is open source and available under the [MIT License](LICENSE).

## Contact

- **Website:** [https://raildevhub.github.io](https://raildevhub.github.io)
- **GitHub Organization:** [https://github.com/raildevhub](https://github.com/raildevhub)

---

<p align="center">
  <strong>RailDevHub © 2024-2025 - Combining AI and Software for Railway Excellence</strong>
</p>

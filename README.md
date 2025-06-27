# MBA DevSecOps App

A modern React + TypeScript + Vite application with automated CI/CD pipeline for DevSecOps best practices.

[![Deploy to GitHub Pages](https://github.com/[username]/mba-devsecops-app/workflows/Deploy%20to%20GitHub%20Pages/badge.svg)](https://github.com/[username]/mba-devsecops-app/actions)

## 🎯 Project Overview

This project demonstrates the implementation of a complete CI/CD pipeline.

## 🚀 Live Demo

Visit the deployed application: `https://[username].github.io/mba-devsecops-app/`

## 🏗️ CI/CD Pipeline

### Pipeline Steps

The automated pipeline includes:

1. **📥Code Checkout** - Retrieves the latest source code
2. ** Environment Setup** - Configures Node.js 22.17.0
3. ** Dependency Installation** - Installs project dependencies
4. ** Security Audit** - Checks for vulnerabilities
5. ** Code Linting** - Ensures code quality standards
6. ** Test Execution** - Runs unit tests
7. ** Application Build** - Creates production build
8. ** Automated Deployment** - Deploys to GitHub Pages

### Pipeline Triggers

- **Push to main branch** - Full pipeline with deployment
- **Pull requests** - Build and test validation (no deployment)
- **Manual dispatch** - On-demand execution

## 🛠️ Technologies

| Category         | Technology               | Purpose                        |
| ---------------- | ------------------------ | ------------------------------ |
| **Frontend**     | React 19                 | UI framework                   |
| **Language**     | TypeScript               | Type-safe JavaScript           |
| **Build Tool**   | Vite 7                   | Fast build tool and dev server |
| **Testing**      | Vitest + Testing Library | Unit testing framework         |
| **Code Quality** | ESLint                   | Code linting and formatting    |
| **CI/CD**        | GitHub Actions           | Automated pipeline             |
| **Hosting**      | GitHub Pages             | Static site hosting            |

## 🔧 Local Development

### Prerequisites

- Node.js 22.17.0 or higher
- npm 10.9.2 or higher

### Setup Instructions

```bash
# Clone the repository
git clone https://github.com/[username]/mba-devsecops-app.git
cd mba-devsecops-app

# Install dependencies
npm install

# Start development server
npm run dev

# Run tests
npm run test

# Run linter
npm run lint

# Build for production
npm run build

# Preview production build
npm run preview
```

## � Available Scripts

| Script                  | Description              |
| ----------------------- | ------------------------ |
| `npm run dev`           | Start development server |
| `npm run build`         | Build for production     |
| `npm run lint`          | Run ESLint               |
| `npm run preview`       | Preview production build |
| `npm run test`          | Run tests in watch mode  |
| `npm run test:run`      | Run tests once           |
| `npm run test:coverage` | Run tests with coverage  |

## 🔒 Security Features

- **Dependency scanning** - Automated security audits
- **Code quality checks** - ESLint enforcement
- **Type safety** - TypeScript compilation
- **Automated testing** - Unit test validation

## 📊 Project Structure

```
mba-devsecops-app/
├── .github/
│   └── workflows/
│       └── deploy.yml          # CI/CD pipeline configuration
├── public/
│   └── vite.svg               # Static assets
├── src/
│   ├── components/            # React components
│   ├── tests/                 # Test files
│   ├── App.tsx               # Main application component
│   ├── main.tsx              # Application entry point
│   └── vite-env.d.ts         # Vite type definitions
├── package.json              # Dependencies and scripts
├── vite.config.ts           # Vite configuration
├── tsconfig.json            # TypeScript configuration
└── README.md                # Project documentation
```

## 🚦 GitHub Pages Setup

To enable automatic deployment:

1. Go to repository **Settings** → **Pages**
2. Set **Source** to "GitHub Actions"
3. Configure **Actions** → **General** → "Read and write permissions"
4. Push to main branch to trigger deployment

## 📈 Continuous Integration

The pipeline automatically:

- Validates code quality and security
- Runs comprehensive test suite
- Builds optimized production bundle
- Deploys to GitHub Pages on success
- Provides detailed feedback on failures

## 📄 License

This project is for educational purposes as part of the MBA in Solutions Architecture, DevSecOps discipline.

This template provides a minimal setup to get React working in Vite with HMR and some ESLint rules.

Currently, two official plugins are available:

- [@vitejs/plugin-react](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react) uses [Babel](https://babeljs.io/) for Fast Refresh
- [@vitejs/plugin-react-swc](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react-swc) uses [SWC](https://swc.rs/) for Fast Refresh

## Expanding the ESLint configuration

If you are developing a production application, we recommend updating the configuration to enable type-aware lint rules:

```js
export default tseslint.config([
  globalIgnores(['dist']),
  {
    files: ['**/*.{ts,tsx}'],
    extends: [
      // Other configs...

      // Remove tseslint.configs.recommended and replace with this
      ...tseslint.configs.recommendedTypeChecked,
      // Alternatively, use this for stricter rules
      ...tseslint.configs.strictTypeChecked,
      // Optionally, add this for stylistic rules
      ...tseslint.configs.stylisticTypeChecked,

      // Other configs...
    ],
    languageOptions: {
      parserOptions: {
        project: ['./tsconfig.node.json', './tsconfig.app.json'],
        tsconfigRootDir: import.meta.dirname,
      },
      // other options...
    },
  },
]);
```

You can also install [eslint-plugin-react-x](https://github.com/Rel1cx/eslint-react/tree/main/packages/plugins/eslint-plugin-react-x) and [eslint-plugin-react-dom](https://github.com/Rel1cx/eslint-react/tree/main/packages/plugins/eslint-plugin-react-dom) for React-specific lint rules:

```js
// eslint.config.js
import reactX from 'eslint-plugin-react-x';
import reactDom from 'eslint-plugin-react-dom';

export default tseslint.config([
  globalIgnores(['dist']),
  {
    files: ['**/*.{ts,tsx}'],
    extends: [
      // Other configs...
      // Enable lint rules for React
      reactX.configs['recommended-typescript'],
      // Enable lint rules for React DOM
      reactDom.configs.recommended,
    ],
    languageOptions: {
      parserOptions: {
        project: ['./tsconfig.node.json', './tsconfig.app.json'],
        tsconfigRootDir: import.meta.dirname,
      },
      // other options...
    },
  },
]);
```

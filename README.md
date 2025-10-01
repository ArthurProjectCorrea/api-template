<p align="center">
  <a href="http://nestjs.com/" target="blank"><img src="https://nestjs.com/img/logo-small.svg" width="120" alt="Nest Logo" /></a>
</p>

<h1 align="center">NestJS API Template</h1>

<p align="center">
  A production-ready NestJS template with pre-configured development tooling, code quality automation, and AI coding agent support.
</p>

## 📋 Description

This is a **comprehensive NestJS API template** designed to accelerate project initialization with a robust, pre-configured development environment. Built with TypeScript and following NestJS best practices, this template provides a solid foundation for building scalable server-side applications.

### ✨ Key Features

- **🏗️ NestJS Framework**: Latest version with decorator-based architecture and dependency injection
- **📦 Package Management**: Configured with pnpm for fast, efficient dependency management
- **✅ Code Quality**: ESLint + Prettier with automatic formatting and linting
- **🧪 Testing Setup**: Jest for unit tests and Supertest for E2E testing
- **🔄 Git Hooks**: Husky + lint-staged for pre-commit code quality checks
- **📝 Conventional Commits**: Commitlint + Commitizen for standardized commit messages
- **🚀 Semantic Release**: Automated versioning and changelog generation
- **🤖 AI Agent Support**: Comprehensive instructions for GitHub Copilot and other AI coding assistants
- **⚡ Fast Compilation**: SWC for rapid development builds
- **📚 Documentation Guidelines**: Pre-configured structure for public and private documentation

### 🎯 Use Cases

This template is ideal for:

- Starting new NestJS API projects with best practices already configured
- Maintaining consistency across multiple projects
- Reducing initial setup time and configuration overhead
- Learning NestJS with a well-structured example
- Building microservices with standardized tooling

## 🚀 Getting Started

### Prerequisites

Before you begin, ensure you have the following installed:

- **Node.js**: v18+ (LTS recommended)
- **pnpm**: v8+ (required package manager)

Install pnpm globally if you haven't already:

```bash
npm install -g pnpm
```

### Initial Setup

After cloning this repository, follow these steps:

1. **Install dependencies**

   ```bash
   pnpm install
   ```

2. **Initialize Git hooks** (if not already done)

   ```bash
   pnpm run prepare
   ```

3. **Verify the setup**

   ```bash
   # Run linting
   pnpm run lint

   # Run formatting
   pnpm run format

   # Run tests
   pnpm run test
   ```

4. **Start development server**
   ```bash
   pnpm run start:dev
   ```

The API will be available at `http://localhost:3000`

## 📜 Main Commands

### Development

```bash
# Start in watch mode (recommended for development)
pnpm run start:dev

# Start in debug mode
pnpm run start:debug

# Build for production
pnpm run build

# Start production server
pnpm run start:prod
```

### Code Quality

```bash
# Run ESLint with auto-fix
pnpm run lint

# Format code with Prettier
pnpm run format
```

### Testing

```bash
# Run unit tests
pnpm run test

# Run unit tests in watch mode
pnpm run test:watch

# Run E2E tests
pnpm run test:e2e

# Generate test coverage report
pnpm run test:cov

# Debug tests
pnpm run test:debug
```

### Git Workflow

```bash
# Create a commit using Commitizen (interactive)
pnpm run commit

# Test semantic release (dry run)
pnpm run release:dry

# Execute semantic release (CI/CD only)
pnpm run release
```

## 📂 Project Structure

```
api-template/
├── .github/
│   ├── copilot-instructions.md    # AI agent instructions
│   ├── instructions/               # Project guidelines
│   ├── prompts/                    # AI prompts
│   └── workflows/                  # GitHub Actions
├── .husky/                         # Git hooks
├── src/
│   ├── app.controller.ts           # Route handlers
│   ├── app.service.ts              # Business logic
│   ├── app.module.ts               # Root module
│   ├── main.ts                     # Application entry point
│   └── *.spec.ts                   # Unit tests
├── test/
│   └── *.e2e-spec.ts              # E2E tests
├── .releaserc.json                 # Semantic release config
├── commitlint.config.js            # Commit validation rules
├── eslint.config.mjs               # ESLint configuration
├── nest-cli.json                   # Nest CLI configuration
└── tsconfig.json                   # TypeScript configuration
```

## 🔧 Configuration

### Environment Variables

This template doesn't include environment configuration by default. To add environment support:

1. Install dependencies:

   ```bash
   pnpm add @nestjs/config
   ```

2. Create `.env` file in the root directory

3. Import `ConfigModule` in `app.module.ts`

### Port Configuration

Default port is `3000`. To change it, set the `PORT` environment variable:

```bash
PORT=4000 pnpm run start:dev
```

## 📝 Commit Guidelines

This project follows [Conventional Commits](https://www.conventionalcommits.org/) specification.

### Commit Types

- `feat`: New feature
- `fix`: Bug fix
- `docs`: Documentation changes
- `style`: Code style/formatting
- `refactor`: Code restructuring
- `test`: Adding or updating tests
- `chore`: Maintenance tasks
- `perf`: Performance improvements
- `ci`: CI/CD changes
- `build`: Build system changes

### Creating Commits

Use the interactive commit tool:

```bash
pnpm run commit
```

This will guide you through creating a properly formatted commit message.

## 🤖 AI Coding Agent Support

This template includes comprehensive instructions for AI coding agents in `.github/copilot-instructions.md`. These instructions help AI assistants understand the project structure, conventions, and workflows.

## 📚 Documentation

Documentation should be organized in the `docs/` folder:

- `docs/public/` - External API documentation
- `docs/private/` - Internal development documentation

See `.github/instructions/documentation.instructions.md` for detailed guidelines.

## 🧪 Testing

### Unit Tests

Located in `src/` alongside source files with `.spec.ts` extension. Uses Jest with NestJS testing utilities.

```bash
pnpm run test
```

### E2E Tests

Located in `test/` directory with `.e2e-spec.ts` extension. Uses Supertest for HTTP testing.

```bash
pnpm run test:e2e
```

## 🚀 Deployment

### Production Build

```bash
pnpm run build
```

Compiled output will be in the `dist/` directory.

### Running in Production

```bash
pnpm run start:prod
```

For deployment platforms, refer to [NestJS deployment documentation](https://docs.nestjs.com/deployment).

## 📦 Semantic Versioning

This project uses [Semantic Release](https://semantic-release.gitbook.io/) for automated versioning and changelog generation.

### Release Process

Releases are triggered manually via GitHub Actions:

1. Go to **Actions** → **Release** workflow
2. Click **Run workflow**
3. Select branch (`main` for stable, `develop` for beta)
4. Semantic Release will:
   - Analyze commits since last release
   - Determine next version
   - Generate CHANGELOG.md
   - Create Git tag
   - Create GitHub Release

## 📖 Resources

- [NestJS Documentation](https://docs.nestjs.com)
- [NestJS Discord](https://discord.gg/G7Qnnhy)
- [Conventional Commits](https://www.conventionalcommits.org/)
- [Semantic Versioning](https://semver.org/)

## 📄 License

This template is [UNLICENSED](LICENSE) - modify as needed for your project.

## 🤝 Contributing

Contributions, issues, and feature requests are welcome! Feel free to check the issues page.

---

<p align="center">Made with ❤️ using NestJS</p>

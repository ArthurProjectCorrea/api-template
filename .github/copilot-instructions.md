# AI Coding Agent Instructions

## Project Overview

This is a **NestJS API template** - a clean starter repository built with TypeScript. It follows NestJS best practices for building scalable Node.js server-side applications using decorator-based architecture with dependency injection.

## Architecture & Key Patterns

### Module Structure

- **Centralized module system**: All features organized in `src/app.module.ts` with imports/controllers/providers
- **Decorator-driven**: Use `@Controller()`, `@Injectable()`, `@Get()`, `@Post()` etc. from `@nestjs/common`
- **Dependency injection**: Constructor-based DI pattern - see `AppController` constructor injecting `AppService`

### Project Template Structure

```
src/
├── main.ts           # Application bootstrap (NestFactory.create)
├── app.module.ts     # Root module with controllers/providers
├── app.controller.ts # Route handlers with @Get/@Post decorators
├── app.service.ts    # Business logic with @Injectable()
└── *.spec.ts        # Unit tests co-located with source
test/
└── *.e2e-spec.ts    # End-to-end integration tests
```

## Development Workflow

### Package Manager

- **Uses pnpm exclusively** - never use npm/yarn commands
- Install: `pnpm install`
- Add dependencies: `pnpm add <package>` or `pnpm add -D <package>`

### Key Scripts

```bash
pnpm run start:dev     # Watch mode for development (most used)
pnpm run start:debug   # Debug mode with --inspect-brk
pnpm run build         # Production build to dist/
pnpm run lint          # ESLint with auto-fix
pnpm run format        # Prettier formatting
pnpm run test          # Unit tests with Jest
pnpm run test:e2e      # E2E tests with supertest
pnpm run test:cov      # Coverage reports
```

### Testing Conventions

- **Unit tests**: Use `Test.createTestingModule()` for module mocking - see `app.controller.spec.ts`
- **E2E tests**: Use `supertest` with `app.getHttpServer()` - see `test/app.e2e-spec.ts`
- **Test files**: `.spec.ts` for unit, `.e2e-spec.ts` for integration
- **Co-location**: Unit tests live next to source files in `src/`

## Code Conventions

### NestJS Patterns

- **Controllers**: Handle HTTP requests, delegate to services
- **Services**: Contain business logic, marked with `@Injectable()`
- **Modules**: Group related controllers/services with `@Module()` decorator
- **Bootstrap**: Always use `NestFactory.create()` in `main.ts`

### TypeScript Configuration

- **Target**: ES2023 with decorators enabled
- **Strict mode**: Partially enabled (strictNullChecks: true, noImplicitAny: false)
- **Build output**: Compiled to `dist/` directory
- **Path mapping**: Base URL set to `./` for clean imports

### Code Quality

- **ESLint**: Flat config (eslint.config.mjs) with TypeScript + Prettier integration
- **Prettier**: Automatic formatting on `pnpm run format`
- **SWC**: Fast compilation with @swc/core for development builds

## Adding New Features

### New Endpoint Pattern

1. Add method to controller with appropriate decorator (`@Get()`, `@Post()`, etc.)
2. Implement business logic in service
3. Add unit tests for both controller and service
4. Add E2E test for the endpoint

### New Module Pattern

1. Create module folder with: `module.ts`, `controller.ts`, `service.ts`
2. Import new module in `app.module.ts`
3. Follow same testing patterns as root module

## Common Development Tasks

### Port Configuration

- Default port: 3000 (configurable via `process.env.PORT`)
- Server starts with `await app.listen(process.env.PORT ?? 3000)`

### Environment Setup

- No environment configuration in template (add as needed)
- Production build runs with `node dist/main`

When extending this template, maintain the clean separation of concerns and decorator-based patterns that make NestJS applications maintainable and testable.

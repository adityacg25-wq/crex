# Repository Guidelines

## Project Structure & Module Organization

CREX Consulting Group is a multipage Next.js App Router website using TypeScript, React and Tailwind CSS v4.

- `src/app/`: App Router pages, layouts, and route handlers.
- `src/components/`: Reusable interface components.
- `src/lib/`: Shared utilities and server integrations.
- `src/content/`: Service descriptions and company information.
- `public/`: Logos, images, and other static assets.
- `tests/`: Node.js validation and Playwright browser regression tests.

The existing `work/` and `outputs/` directories hold planning material and deliverables.

## Build, Test, and Development Commands

Use Node.js 24 and pnpm 11, as specified in the package manifest and lockfile.
- `pnpm install`: Install dependencies.
- `pnpm dev`: Start local development at `http://127.0.0.1:3000`.
- `pnpm build`: Validate the production build.
- `pnpm start`: Serve the production build.
- `pnpm lint` and `pnpm typecheck`: Check code quality and types.
- `pnpm test`: Run validation tests.
- `pnpm test:e2e`: Run browser tests against a running local server.

Use the package manager selected by the committed lockfile.

## Coding Style & Naming Conventions

Use TypeScript, two-space indentation, and descriptive names. Name components in PascalCase, utilities in camelCase, and route directories in lowercase kebab-case.

Prefer Server Components; introduce Client Components where interaction requires them. Keep content separate from presentation. Follow ESLint and the semantic theme tokens in `globals.css`. Preserve current service URLs and the consistent radius scale.

## Testing Guidelines

Use Node.js tests for validation and Playwright for browser regressions. Cover enquiry validation, submission failures, navigation and important business logic. Name validation tests `*.test.ts` and browser tests `*.spec.ts`. No numerical coverage threshold is configured.

Verify mobile and desktop layouts in the light design, including dark system preferences and keyboard navigation. Do not reintroduce a theme switch. Run configured checks and a production build before submitting changes. Never send real client enquiries during testing.

## Commit & Pull Request Guidelines

There is no Git history establishing conventions. Use concise, imperative messages, such as `feat: add leasing service page`.

Pull requests should explain the change, include validation results, reference relevant issues, and attach screenshots for visual changes.

## Security & Content

Keep credentials in environment variables; never commit secrets. Expose only intentionally public values through `NEXT_PUBLIC_*`.

The public enquiry form validates fields and opens a WhatsApp draft; email is optional. Never claim the message was sent. The retained email API validates on the server and reports success only after delivery is accepted. Preserve CREX's advisory positioning and regional expertise. Avoid invented testimonials, credentials, completed projects or guaranteed returns. Architectural imagery is representative.

Use `.env.example` for mail configuration. Credentials stay server-side.

<!-- BEGIN:nextjs-agent-rules -->

# This is NOT the Next.js you know

This version has breaking changes — APIs, conventions, and file structure may all differ from your training data. Read the relevant guide in `node_modules/next/dist/docs/` (resolved from this file's directory; in monorepos the `next` package may not be visible from the repo root) before writing any code. Heed deprecation notices.

This block is written and re-added by `next dev` — verify at `node_modules/next/dist/server/lib/generate-agent-files.js`. Removing it from a diff only re-creates the uncommitted change; committing it with your work keeps the tree clean.

<!-- END:nextjs-agent-rules -->

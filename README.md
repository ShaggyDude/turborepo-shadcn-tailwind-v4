# Turborepo + Shadcn/ui + Tailwind CSS v4 + Next.js

## Introduction

- I created this setup to share after completing the migration process from Tailwind CSS v3 to v4 in a monorepo structure, as I found it difficult to find documentation on this. It offers a ready-to-use configuration with Turborepo, Tailwind CSS v4, Shadcn/ui, and Next.js.

- Since I can’t always keep this up to date, please adjust versions like `react`, `next` and others as needed.

- Please use this with a basic understanding of Monorepo concepts using Turborepo.  
  [-> Turborepo Docs](https://turborepo.com/docs)

## Getting Started

```bash
# Clone the repository
git clone https://github.com/bytaesu/turborepo-shadcn-tailwind-v4.git

# Install dependencies
pnpm install

# Run the development server
turbo dev --filter nextjs

# Add new shadcn component
cd packages/ui
pnpm dlx shadcn@latest add [component]
```

## Structure

.
├── apps
│   └── nextjs
│       ├── eslint.config.mjs
│       ├── next-env.d.ts
│       ├── next.config.ts
│       ├── package.json
│       ├── postcss.config.mjs
│       ├── README.md
│       ├── src
│       └── tsconfig.json
├── bun.lock
├── bunfig.json
├── LICENSE
├── package.json
├── packages
│   ├── eslint-config
│   │   ├── base.js
│   │   ├── next.js
│   │   ├── package.json
│   │   ├── react-internal.js
│   │   └── README.md
│   ├── typescript-config
│   │   ├── base.json
│   │   ├── nextjs.json
│   │   ├── package.json
│   │   ├── react-library.json
│   │   └── README.md
│   └── ui
│       ├── components.json
│       ├── eslint.config.mjs
│       ├── package.json
│       ├── postcss.config.mjs
│       ├── README.md
│       ├── src
│       └── tsconfig.json
├── pnpm-workspace.yaml
├── README.md
└── turbo.json

## Critical Configuration

[-> Tailwind CSS Docs](https://tailwindcss.com/docs/detecting-classes-in-source-files)

The most important part of this setup is the `/src/app/globals.css` file in the Next.js application. Proper configuration of the `@source` directive is essential for the UI package to work correctly:

```css
@import 'tailwindcss';
@import '@repo/ui/styles/default.css';

@source '../../node_modules/@repo/ui';
```

## License

MIT


# 1. Epics Database

| Property Name    | Type         | Mandatory | Description                                | Example Usage                 |
|------------------|--------------|-----------|--------------------------------------------|-------------------------------|
| Title            | Title        | Yes       | Epic name or goal                          | "User Onboarding Flow"        |
| Description      | Text         | Optional  | Plain English summary                      | "Streamline new user signup"  |
| Status           | Select       | Yes       | Workflow status                            | Do, Doing, Done               |
| Owner            | Person       | Optional  | Person responsible                         | Team member assigned          |
| Due Date         | Date         | Optional  | Target completion date                     | 2025-12-31                    |
| Created Time     | Created time | Yes       | Auto timestamp                             | Auto-generated                |
| Last Edited Time | Last edited  | Yes       | Auto timestamp                             | Auto-generated                |

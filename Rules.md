## Rules

# 🚀 AI Agent Rules for Coding (Next.js + Tailwind + shadcn/ui + Bun)

This document defines the rules, principles, and best practices the AI agent must follow when helping with **Next.js, Tailwind CSS, shadcn/ui, and Bun projects**.

---

## 1. General Principles

1. **Clarity First**: Provide step-by-step explanations that are easy to follow.
2. **Simplicity Before Complexity**: Offer the simplest working solution before suggesting optimizations.
3. **Correctness > Creativity**: Ensure the code compiles and follows framework conventions before experimenting.
4. **Consistency**: Maintain consistent naming, file structure, and formatting.
5. **Error Awareness**: Anticipate common pitfalls (hydration errors, type issues, CSS conflicts).

---

## 2. Code Writing Rules

1. Always provide **complete, runnable code snippets** (pages, components, hooks).
2. Use **Next.js conventions**:
   - `app/` directory when possible.
   - Use **server components** by default; switch to **client components** only when needed.
   - Follow **file-based routing** conventions.
3. Use **Tailwind CSS best practices**:
   - Prefer utility-first classes over custom CSS.
   - Keep class names readable and avoid duplication.
   - Use `@apply` sparingly, only in reusable styles.
4. Use **shadcn/ui components** correctly:
   - Always import from `@/components/ui/...`.
   - Follow accessibility guidelines baked into shadcn/ui.
   - Extend components instead of rewriting from scratch.
5. Always use **Bun for package management and scripts**:
   - `bun add <package>` instead of `npm install`.
   - `bun run <script>` instead of `npm run`.
   - `bunx <tool>` instead of `npx <tool>`.
6. Prefer **modern practices**:
   - `async/await` for data fetching.
   - Server Actions when appropriate.
   - `next/navigation` hooks (`useRouter`, `redirect`) instead of deprecated ones.

---

## 3. Debugging & Problem-Solving Rules

1. When fixing errors, always:
   - Show **the cause of the problem**.
   - Provide a **fixed version of the code**.
   - Explain why the fix works.
2. After writing or fixing code, **check possible side effects**:
   - Could this change break or affect other components?
   - Does it modify shared state, props, or context?
   - Does it require updating related files (e.g., routes, layouts, API endpoints)?
3. Suggest **debugging tools**:
   - React DevTools.
   - Tailwind IntelliSense.
   - ESLint & TypeScript checks.

---

## 4. Verification Rules

1. After every change, **simulate a type check**:
   - Run:
     ```bash
     bunx tsc --noEmit
     ```
   - Ensure **no TypeScript errors** remain.
2. If errors exist, **report them with explanations and fixes**.
3. Always assume the project must remain in a **buildable, error-free state**.

---

## 5. Task Completion Summary Rules

After completing any task (writing code, fixing errors, refactoring):

1. Provide a **summary section** that includes:
   - ✅ **What was done** (new code, bug fix, refactor, etc.).
   - 🔄 **Possible side effects** (other components, routes, or states that may be impacted).
   - 🛠 **Verification result** from `bunx tsc --noEmit`.
   - 💡 **Next suggestions** (improvements, optimizations, or testing ideas).

---

## 6. Learning & Improvement Rules

1. Whenever introducing a new concept (e.g., server actions, middleware, data fetching), give a **short explanation + example**.
2. Encourage **best practices**:
   - Folder structure (`components/`, `lib/`, `hooks/`).
   - Shared UI components with shadcn/ui.
   - Clean separation of UI and logic.
3. Suggest **useful resources**: Next.js docs, Tailwind docs, shadcn/ui docs, Bun docs.
4. Show **refactor examples** when code can be cleaner or more reusable.

---

## 7. Communication Rules

1. Adapt explanations to the **user’s skill level**.
2. Ask clarifying questions before writing complex code.
3. Provide **examples relevant to Next.js apps** (pages, components, API routes, middleware).
4. Suggest **next steps** after solving a problem (e.g., add auth, improve UI, optimize queries).

---

## 8. Security & Safety Rules

1. Never expose **secrets** (API keys, tokens) in code.
2. Use **environment variables** via `.env.local` or `.env.production`.
3. Sanitize and validate **user inputs** in API routes.
4. Use **NextAuth.js or secure OAuth flows** for authentication.
5. Avoid inline styles for sensitive data rendering.

---

## 9. Continuous Improvement Rules

1. Suggest improvements after solving (e.g., accessibility, performance, SEO).
2. Encourage **reusability**:
   - Extract components.
   - Use Tailwind config for theme customization.
   - Extend shadcn/ui instead of duplicating.
3. Stay updated with **latest Next.js, Tailwind, shadcn/ui, and Bun releases**.
4. Encourage **testing** with Jest, React Testing Library, or Playwright.

---

## 10. Database Safety Rules

1. The agent **must never run** the following Prisma commands automatically:
   - `prisma generate`
   - `prisma db push`
   - `prisma migrate reset`
   - `prisma reset`
   - Any command that **deletes or resets** the database.
2. The agent **may only read** from existing Prisma schema or data models — no schema modifications or migrations.
3. If a migration or generation is needed, the agent should:
   - **Explain what needs to be done**,
   - **Show the command**,
   - But **not execute it** automatically.
4. Always confirm database safety and data persistence before suggesting any schema-related operations.

---

✅ Following these rules, the AI agent will provide **smart, Bun-powered, reliable, and production-ready help** for Next.js, Tailwind, and shadcn/ui projects — always with a final **task summary** for clarity.

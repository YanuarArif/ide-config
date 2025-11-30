# 🚀 AI Agent Rules for Coding (Next.js + Tailwind + shadcn/ui + npm)

This document defines the rules, principles, and best practices the AI agent must follow when helping with **Next.js, Tailwind CSS, shadcn/ui, and npm projects**.

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
5. Always use **npm for package management and scripts**:
   - `npm install <package>` for adding dependencies.
   - `npm run <script>` for running scripts.
   - `npx <tool>` for executing packages.
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
     npx tsc --noEmit
     ```
   - Ensure **no TypeScript errors** remain.
2. If errors exist, **report them with explanations and fixes**.
3. Always assume the project must remain in a **buildable, error-free state**.

---

## 5. Task Completion Summary Rules

After completing any task (writing code, fixing errors, refactoring):

1. Provide a **summary section** that includes:
   - ✅ **What was done** (new code, bug fix, refactor, etc.).
   - 📊 **Before/After comparison table** (showing key changes in functionality, behavior, or code structure).
   - 🔄 **Possible side effects** (other components, routes, or states that may be impacted).
   - 🛠 **Verification result** from `npx tsc --noEmit`.
   - 💡 **Next suggestions** (improvements, optimizations, or testing ideas).
   - 📝 **Commit message** (ready-to-use Git commit message following conventional commits format).

### Before/After Comparison Table:

Always include a **comparison table** that clearly shows what changed:

**Table Format:**

| Aspect             | Before ❌        | After ✅         |
| ------------------ | ---------------- | ---------------- |
| [Feature/Behavior] | [Old state/code] | [New state/code] |

**Example Tables:**

**Bug Fix Example:**
| Aspect | Before ❌ | After ✅ |
|--------|----------|---------|
| Event discount on edit | Lost when editing sales | Preserved using 3-tier fallback |
| Data source | Only from form | DB snapshot → form → existing data |
| Historical data | ❌ Not preserved | ✅ Fully preserved |

**What to Include in the Table:**

- **Functionality changes**: What behavior changed
- **Code structure**: How the code organization improved
- **Performance metrics**: Load times, bundle sizes, query counts
- **Data handling**: How data flows changed
- **Error handling**: What error cases are now covered
- **User experience**: How UX improved
- **Type safety**: TypeScript improvements

### Commit Message Format:

Follow the **Conventional Commits** specification:

```
<type>(<scope>): <subject>

<body>

<footer>
```

**Types:**

- `feat`: New feature
- `fix`: Bug fix
- `refactor`: Code refactoring
- `perf`: Performance improvement
- `style`: Code style changes (formatting, missing semicolons, etc.)
- `docs`: Documentation changes
- `test`: Adding or updating tests
- `chore`: Maintenance tasks (dependencies, build config, etc.)

**Example Commit Messages:**

```bash
# Simple fix
fix(penjualan): preserve event discount data on edit

# Feature with body
feat(event-discounts): add fallback mechanism for historical data

- Add existingItemsMap for backup data
- Implement 3-tier fallback: snapshot → form → existing
- Ensure historical discount data is preserved

# Refactor
refactor(api): optimize database queries in sales endpoint
```

**Rules:**

- Keep subject line under 72 characters
- Use imperative mood ("add" not "added" or "adds")
- Capitalize first letter of subject
- No period at the end of subject
- Provide context in body for complex changes

---

## 6. Flow Proses (Process Flow Diagrams)

After completing complex features or workflows, **always include a "Flow Proses" section** that visually documents the data flow and logic:

### Format Requirements:

1. Use **numbered steps** with clear descriptions
2. Use **arrow symbols** (↓) to show flow direction
3. Include **decision points** and **data transformations**
4. Mark **successful outcomes** with emojis (✅, 🎉)
5. Highlight **fallback mechanisms** and **error handling**

### Example Flow Proses:

```
1. User Edit Penjualan
   ↓
2. System ambil data existing items → Buat existingItemsMap
   ↓
3. Fetch event discount aktif dari database
   ↓
4. Saat save, untuk setiap item:
   - Coba gunakan data dari eventDiscountSnapshot (DB) ✅
   - Jika tidak ada, gunakan item.eventDiscountName (form) ✅
   - Jika tidak ada, gunakan existingEventData (backup) ✅
   - Jika semua tidak ada, null
   ↓
5. Data historis TERJAGA! 🎉
```

### When to Include Flow Proses:

- Complex CRUD operations with multiple data sources
- Multi-step form submissions with validation
- Data synchronization between database and UI
- Authentication/authorization flows
- Payment processing workflows
- Any feature involving 3+ sequential steps

### Benefits:

- Makes complex logic **easy to understand**
- Helps future developers **quickly grasp** the system
- Serves as **documentation** for code reviews
- Identifies **potential edge cases** early

---

## 7. Learning & Improvement Rules

1. Whenever introducing a new concept (e.g., server actions, middleware, data fetching), give a **short explanation + example**.
2. Encourage **best practices**:
   - Folder structure (`components/`, `lib/`, `hooks/`).
   - Shared UI components with shadcn/ui.
   - Clean separation of UI and logic.
3. Suggest **useful resources**: Next.js docs, Tailwind docs, shadcn/ui docs, npm docs.
4. Show **refactor examples** when code can be cleaner or more reusable.

---

## 8. Communication Rules

1. Adapt explanations to the **user's skill level**.
2. Ask clarifying questions before writing complex code.
3. Provide **examples relevant to Next.js apps** (pages, components, API routes, middleware).
4. Suggest **next steps** after solving a problem (e.g., add auth, improve UI, optimize queries).

---

## 9. Security & Safety Rules

1. Never expose **secrets** (API keys, tokens) in code.
2. Use **environment variables** via `.env.local` or `.env.production`.
3. Sanitize and validate **user inputs** in API routes.
4. Use **NextAuth.js or secure OAuth flows** for authentication.
5. Avoid inline styles for sensitive data rendering.

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

## 11. Continuous Improvement Rules

1. Suggest improvements after solving (e.g., accessibility, performance, SEO).
2. Encourage **reusability**:
   - Extract components.
   - Use Tailwind config for theme customization.
   - Extend shadcn/ui instead of duplicating.
3. Stay updated with **latest Next.js, Tailwind, shadcn/ui, and npm releases**.
4. Encourage **testing** with Jest, React Testing Library, or Playwright.

---

✅ Following these rules, the AI agent will provide **smart, npm-powered, reliable, and production-ready help** for Next.js, Tailwind, and shadcn/ui projects — always with a final **task summary** and **flow proses** for clarity.

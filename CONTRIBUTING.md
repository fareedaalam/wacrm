# Working on Afisofftech CRM

Afisofftech CRM is a complete WhatsApp CRM you run and brand as your
own. The expected flow is:

1. **Clone** this repository.
2. **Deploy** it — see the configuration notes in
   [`.env.local.example`](./.env.local.example).
3. **Customise** it. Rebrand, add the features you need, remove the
   ones you don't, swap hosting, change the schema.

## Clone and run

```bash
git clone https://github.com/fareedaalam/wacrm.git
cd wacrm

cp .env.local.example .env.local   # fill in Supabase + Meta creds
npm install
npm run dev
```

## Reporting bugs

File bugs using the
[bug report](https://github.com/fareedaalam/wacrm/issues/new?template=bug_report.yml)
template. Including the commit SHA, the runtime (managed Node.js /
Vercel / local / other), and logs will get to a fix fastest.

## Reporting security issues

**Do not file security issues publicly.** Follow the private flow in
[SECURITY.md](./.github/SECURITY.md).

## Pull requests

If you send a PR, the usual rules apply:

- Branch off the latest `main` (don't push to a merged branch — commits
  end up orphaned).
- Run `npm run typecheck` and `npm run format` locally first.
- Fill in the PR template, especially the **Test plan**.
- One logical change per PR.
- Commit-message first line is imperative + terse; the body explains
  the *why*, the diff shows the *what*.

## Rebranding for your customers

When you put a deployment in front of your own customers:

- Swap the "Afisofftech CRM" name, favicon, and any default URLs for
  your customer's brand where appropriate.
- Set `NEXT_PUBLIC_SITE_URL` to the customer's canonical domain so
  invite links resolve correctly.
- Keep the MIT [`LICENSE`](./LICENSE) file — that's how the software's
  permissions travel with the code.

## Dev-loop reference

| Command | What it does |
| --- | --- |
| `npm run dev` | Turbopack dev server on port 3000. |
| `npm run build` | Production build. Next also runs its own typecheck here. |
| `npm run typecheck` | `tsc --noEmit`. Fast TS-only pass. |
| `npm run lint` | ESLint. |
| `npm run format` | Prettier write. |
| `npm run format:check` | Prettier in check-only mode. Useful in CI. |
| `npm run test` | Vitest run. |

## Licensing

Afisofftech CRM is MIT ([`LICENSE`](./LICENSE)).

# Coding principles

## Facts
- Understanding correct code logic and generating logic from intent are not same. They are different skills and different muscles. It is okay to copy reusable logic if I understand how it works and what intent it solves. I should always know why I am using a snippet, even if I don’t write the logic from scratch.
- I am trying to jump from no reference → straight to final correct code. That’s too big a leap. Real developers don’t do that.
- Before writing code, I must write logic in words. Example for my filter: ❌ Bad approach “Let me remember filter syntax…”, ✅ Correct approach “Okay… I need all products, If category is ‘All’ don’t filter, Otherwise, match category, Then check if title contains keyword”. Only after that I write code.
- Here’s the rule I should follow from now on 1️⃣ First project: ✔ Copy, ✔ Modify, ✔ Understand. 2️⃣ Second project: ✔ Copy, ✔ Delete parts, ✔ Rebuild with changes. 3️⃣ Third project: ✔ Write from scratch, ✔ Refer back if stuck.
- If I force myself to “never copy”: I will freeze, progress will slow, confidence will drop. If I copy + consciously rebuild: patterns will internalize, my brain will start generating on its own, one day I will write this logic without thinking.
- I should Copy patterns. Generate intent. Translate intent into code.
- Iteration builds intuition. I can copy other people’s code, understand how it works, tweak it, and make it mine through repeated iteration. Intuition enables creation.

## Syntax
**Next.js folder structure**
```css 
src/
├─ app/                              # ROUTES (where)
│  ├─ layout.tsx                     # Root layout (html, body, providers)
│  ├─ page.tsx                       # /  → uses features/home
│  ├─ loading.tsx
│  ├─ error.tsx
│  │
│  ├─ dashboard/
│  │  ├─ layout.tsx                  # Dashboard shell (sidebar, header)
│  │  ├─ page.tsx                    # /dashboard
│  │  │
│  │  ├─ profile/
│  │  │  └─ page.tsx                 # /dashboard/profile
│  │  │
│  │  ├─ appearance/
│  │  │  └─ page.tsx                 # /dashboard/appearance
│  │
│  └─ auth/
│     ├─ login/page.tsx
│     └─ register/page.tsx
│
├─ features/                         # DOMAIN LOGIC (how)
│  ├─ home/                          # HOME FEATURE
│  │  ├─ components/
│  │  │  ├─ HomePage.tsx             # Main home UI
│  │  │  ├─ HeroSection.tsx
│  │  │  └─ FeatureList.tsx
│  │  ├─ hooks/
│  │  │  └─ useHome.ts
│  │  ├─ store/
│  │  │  └─ home.store.ts
│  │  └─ services/
│  │     └─ home.api.ts
│  │
│  ├─ dashboard/
│  │  ├─ components/
│  │  │  ├─ AppSidebar.tsx
│  │  │  └─ DashboardHeader.tsx
│  │  ├─ hooks/
│  │  │  └─ useSidebar.ts
│  │  ├─ store/
│  │  │  └─ sidebar.store.ts
│  │  └─ services/
│  │     └─ dashboard.api.ts
│  │
│  ├─ profile/
│  │  ├─ components/
│  │  │  ├─ ProfileForm.tsx
│  │  │  ├─ DeleteUser.tsx
│  │  │  └─ PageHeader.tsx
│  │  ├─ hooks/
│  │  │  └─ useProfile.ts
│  │  ├─ store/
│  │  │  └─ profile.store.ts
│  │  └─ services/
│  │     └─ profile.api.ts
│  │
│  ├─ appearance/
│  │  ├─ components/
│  │  │  └─ ThemeSelector.tsx
│  │  ├─ hooks/
│  │  │  └─ useTheme.ts
│  │  ├─ store/
│  │  │  └─ theme.store.ts
│  │  └─ services/
│  │     └─ appearance.api.ts
│  │
│  └─ auth/
│     ├─ components/
│     │  ├─ LoginForm.tsx
│     │  └─ RegisterForm.tsx
│     ├─ hooks/
│     │  └─ useAuth.ts
│     ├─ store/
│     │  └─ auth.store.ts
│     └─ services/
│        └─ auth.api.ts
│
├─ components/
│  └─ ui/                            # DESIGN SYSTEM (shadcn)
│     ├─ button.tsx
│     ├─ input.tsx
│     ├─ label.tsx
│     ├─ dropdown-menu.tsx
│     ├─ scroll-area.tsx
│     └─ sidebar.tsx
│
├─ styles/                           # GLOBAL STYLES
│  ├─ globals.css
│  └─ themes.css
│
├─ lib/                              # CORE UTILITIES
│  ├─ api.ts                         # fetch/axios wrapper
│  ├─ utils.ts                       # cn(), helpers
│  ├─ constants.ts
│  └─ env.ts
│
├─ stores/                           # GLOBAL STATE (cross-feature)
│  ├─ user.store.ts
│  └─ settings.store.ts
│
├─ services/                         # GLOBAL SERVICES
│  ├─ auth.service.ts
│  └─ upload.service.ts
│
├─ hooks/                            # SHARED HOOKS
│  └─ useDebounce.ts
│
└─ types/                            # GLOBAL TYPES
   └─ index.ts
```
- app/ → routing & layouts only (no business logic), features/ → domain-based UI + logic (self-contained), components/ui → shadcn primitives (design system), styles/ → global CSS & themes, stores/ → app-wide state, services/ → cross-feature APIs, lib/ → utilities & helpers.

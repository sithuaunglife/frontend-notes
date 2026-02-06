# Coding principles

## Facts
- Understanding correct code logic and generating logic from intent are not same. They are different skills and different muscles. It is okay to copy reusable logic if I understand how it works and what intent it solves. I should always know why I am using a snippet, even if I don’t write the logic from scratch.
- I am trying to jump from no reference → straight to final correct code. That’s too big a leap. Real developers don’t do that.
- Before writing code, I must write logic in words. Example for my filter: ❌ Bad approach “Let me remember filter syntax…”, ✅ Correct approach “Okay… I need all products, If category is ‘All’ don’t filter, Otherwise, match category, Then check if title contains keyword”. Only after that I write code.
- Here’s the rule I should follow from now on 1️⃣ First project: ✔ Copy, ✔ Modify, ✔ Understand. 2️⃣ Second project: ✔ Copy, ✔ Delete parts, ✔ Rebuild with changes. 3️⃣ Third project: ✔ Write from scratch, ✔ Refer back if stuck.
- If I force myself to “never copy”: I will freeze, progress will slow, confidence will drop. If I copy + consciously rebuild: patterns will internalize, my brain will start generating on its own, one day I will write this logic without thinking.
- I should Copy patterns. Generate intent. Translate intent into code.
- Iteration builds intuition. I can copy other people’s code, understand how it works, tweak it, and make it mine through repeated iteration. Intuition enables creation.
- The most important skill in programming is thinking, not syntax. Ideas, logic, and problem-solving come first. Code is just the language used to express those thoughts. AI is my syntax typist, not my brain. I decide what to build and how it should work. AI helps me write faster, cleaner syntax and navigate documentation efficiently. Documentation is unavoidable — and that’s okay. Modern developers don’t memorize everything. They know how to find answers. AI helps me search, summarize, and understand documentation faster in the AI age. Tutorial hell is dangerous. Tutorials reflect the teacher’s thinking, not mine. Following them blindly turns me into someone else’s code typist. If I rely on tutorials too much, I freeze at a blank page. That’s the real warning sign: when the guide is gone, my thinking disappears too. The right way to use tutorials: Watch once to understand the idea, Close it, Rebuild from memory, Make mistakes, Think independently. Practice > watching. Thinking > copying. Repetition with my own brain active builds real skill.
- “Out of the box” means something works immediately by default, without any extra setup, configuration, or libraries. Example 1: JavaScript — fetch() is promise-based out of the box; no installation required; no manual Promise wrapping needed. Example 2: React — useState works out of the box; no configuration needed; just import and use. Example 3: Next.js — Routing works out of the box; no router setup required; folder structure automatically maps to routes.
- Let errors crash loudly during development, but handle them gracefully in production to protect user trust.
- Anti-virus can block programming relative package, library and activity.
- Syntax is like muscle memory. You don’t need to feel guilty if you can’t remember it. Muscle memory is built through repeated coding and constant reference. It’s similar to driving a car or playing an RTS game: once you’ve done it enough times, you no longer think about every action. You simply act. Programming works the same way. You don’t need to memorize syntax; you let muscle memory handle it and focus on understanding what the syntax does. If you forget something, you can always reference your notes or use AI.
- Muscle memory emerges unconsciously through repeated, practice.

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
- If stores, services, types, or hooks are reused across features or modules, they live outside; if they belong to a single feature, they live inside that feature.

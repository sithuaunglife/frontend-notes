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
- Model (M). This is your data & business layer. Usually: services/, types/, stores/ (zustand), validation logic. This layer: Talks to backend, Knows business rules, Doesn’t care about UI.
- View (V). This is your UI like ```CustomerTable.tsx``` ```CustomerForm.tsx``` ```Modal.tsx```. It: Renders data, Calls functions, Doesn’t know how API works internally. It just says: ```const { customers } = useCustomerList()```.
- ViewModel (VM). This is the bridge. The brain between View and Model. In React world? It’s your custom hooks. Example: ```useCustomerList.ts``` ```useCustomerCreate.ts```. Inside that hook: Call service, Handle loading, Handle error, Transform data, Connect zustand, Then the View just consumes it. That hook = ViewModel.
- Separation of concerns is important.
- There is engineering guided vibe coding.
- Vibe coding maybe standard in future.
- Schema → Type, Hook → Logic, Component → UI
- Good file architecture is very important. Thanks to separation of concerns, each file has a clear responsibility, making it easier and faster to locate, understand, and maintain code.
- The ```services``` folder is responsible for API communication and external data handling, not UI logic.
- The ```types``` folder is responsible for storing shared TypeScript types and interfaces used across the application, including inferred schema types and payload definitions.
- The ```hooks``` folder is responsible for encapsulating reusable logic, including state management, side effects, and business logic. It may use schemas and types, but its main purpose is logic, not type storage.
- The ```components``` folder is responsible for rendering UI and receiving data through props. It focuses on presentation, not business logic.
- BFF (Backend for Frontend) is a backend layer designed specifically for one frontend, focus more on backend, understand UI needs deeply, understand backend services deeply, think across layers. Their mindset is very similar to full-stack thinking but they are still writing backend code.
- List hook (useCategoryList) fetches and manages multiple items. Detail hook (useCategoryDetail) fetches and manages one single item.
- When learning, isolate one concept (like useSearchParams) and focus only on understanding what it’s doing instead of thinking about everything at once. Zoom in and isolate that one thing like useSearchParams to understand what it is trying to do, and ignore other parts and syntax. After understanding what it is trying to do, zoom out and reconnect it back to the system. Don’t try to think about everything at once — it will overload your brain and cause confusion and frustration. Break problems into pieces, understand each piece, then reconnect the pieces.
- Backend defines the API contract, but frontend can rename fields after fetching the data.
- Data passing is like a pipeline. The real values come from the backend. TypeScript is just type checking. It doesn’t create real values and it disappears at runtime. The real data is created in the backend and carried through services and hooks until it reaches the component. Frontend only receives and renders the data. Now everything makes sense because I understand that TypeScript only checks structure, but backend is the one that provides the actual data.
- Engineering Mindset Rule is do not add abstraction / tools / structure unless the situation truly requires it. If something is unnecessary, if it adds confusion, if it doesn’t solve a real problem then remove it.
- From now on I view render and re-render from the user perspective and runtime perspective. Rendering does not happen because I coded the component. It happens at runtime when user interaction, state changes, routing, data fetching or browser refresh causes React to execute the component again.
- Whenever something confuses you, ask “From whose perspective am I seeing this?” Browser perspective, React perspective, User perspective, State perspective, Developer perspective. Frontend problems become solvable when you switch viewpoints.
- Sometimes the problem is not a frontend bug. If the backend server / API is down, slow, or not implemented yet, the frontend may show: No data rendering, Loading forever, Fetch / network errors, Filters or actions not working. Before debugging frontend logic deeply, always check API status, response, and backend readiness (Network tab / console / backend team confirmation).
 
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
│  │  ├─ appearance/                 # /dashboard/appearance
│  │  │  └─ page.tsx         
│  │  │
│  │  └─ customer/
│  │     └─ page.tsx                
│  │
│  └─ auth/
│     ├─ login/page.tsx
│     └─ register/page.tsx
│
├─ modules/ or features/             # DOMAIN LOGIC (how)
│  ├─ home/                          # HOME FEATURE
│  │  ├─ components/
│  │  │  ├─ HomePage.tsx             # Main home UI
│  │  │  ├─ HeroSection.tsx
│  │  │  └─ FeatureList.tsx
│  │  └─ hooks/
│  │     └─ useHome.ts
│  │
│  ├─ customer/ or customers/
│  │  ├─ components/                  
│  │  │     ├─ create/
│  │  │     │  └─ CustomerCreateForm.tsx
│  │  │     ├─ delete/
│  │  │     │  └─ CustomerDeleteBtn.tsx
│  │  │     ├─ detail/            
│  │  │     │  ├─ CustomerDetailCard.tsx
│  │  │     │  └─ CustomerDetailCardLoader.tsx     # Skeleton Loader 
│  │  │     ├─ edit/  
│  │  │     │  └─ CustomerEditForm.tsx
│  │  │     └─ list/  
│  │  │        └─ CustomerListSection.tsx
│  │  │        └─ CustomerTable.tsx
│  │  └─ hooks/
│  │     └─ useCustomer.ts
│  │
│  ├─ dashboard/
│  │  ├─ components/
│  │  │  ├─ AppSidebar.tsx
│  │  │  └─ DashboardHeader.tsx
│  │  └─ hooks/
│  │     └─ useSidebar.ts
│  │
│  ├─ profile/
│  │  ├─ components/
│  │  │  ├─ ProfileForm.tsx
│  │  │  ├─ DeleteUser.tsx
│  │  │  └─ PageHeader.tsx
│  │  └─ hooks/
│  │     └─ useProfile.ts
│  │
│  ├─ appearance/
│  │  ├─ components/
│  │  │  └─ ThemeSelector.tsx
│  │  └─ hooks/
│  │     └─ useTheme.ts
│  │
│  └─ auth/
│     ├─ components/
│     │  ├─ LoginForm.tsx
│     │  └─ RegisterForm.tsx
│     └─ hooks/
│        └─ useAuth.ts
│
├─ components/
│  ├─ ui/                            # DESIGN SYSTEM (shadcn)
│  │  ├─ button.tsx
│  │  ├─ input.tsx
│  │  ├─ label.tsx
│  │  ├─ dropdown-menu.tsx
│  │  ├─ scroll-area.tsx
│  │  └─ sidebar.tsx
│  │
│  └─ TablePagination.tsx            # Custom Centralized Component     
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
│  ├─ authService.ts
│  └─ uploadService.ts
│
├─ hooks/                            # SHARED HOOKS
│  └─ useDebounce.ts
│
└─ types/                            # GLOBAL TYPES
   └─ index.ts
```
- app/ → routing & layouts only (no business logic), features/ → domain-based UI + logic (self-contained), components/ui → shadcn primitives (design system), styles/ → global CSS & themes, stores/ → app-wide state, services/ → cross-feature APIs, lib/ → utilities & helpers.
- If stores, services, types, or hooks are reused across features or modules, they live outside; if they belong to a single feature, they live inside that feature.
- create/detail/edit/index are CRUD and are features.
- If components don’t talk to an API, no need to use create/detail/edit/index structure. Just put normal components under feature/components.
- Use Noun + Verb + UI type naming (e.g., CustomerCreateForm.tsx) for feature-specific components.
- services files (e.g, authService.ts) are written in camelCase.
- types files (e.g, UserTypes.ts) are written in PascalCase since they define interfaces or types.
- hooks files (e.g, useCustomerCreate.ts) need to use ```use``` since they define custom React hooks. stores files also use ```use``` too since they are implemented as hook-based stores (e.g., with Zustand).
- Use plural nouns for route paths (e.g., /customers) to represent resource collections and keep routing consistent.
- MV = Model + View (data layer and UI layer), while VM = ViewModel, which acts as the logic layer connecting data to the UI (often implemented as hooks in React).
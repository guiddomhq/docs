# Krovos — Complete Product Roadmap & Ideas Backlog
*Compiled from all founding sessions including ChatGPT founding thread (690 messages), CoWork sessions, and all Claude sessions.*
*This is the authoritative source of truth. Last updated: June 2026*

---

## The Kernel

> Krovos built the first system that truly understands a person's life.

Not the first system to track financial data. Not the first AI assistant. Not the first life planning tool. The first system that truly understands a person's life — across every domain, at every life phase, across years and decades — and uses that understanding to provide guidance that feels like it came from someone who knows you.

**Test for every decision:** Does this deepen our understanding of the person's life, or does it distract from it?

---

## The Three Human Problems Krovos Solves

| Gap | Definition |
|---|---|
| Knowledge Gap | People genuinely don't know — they were never taught. This is not a failure of intelligence. It is a failure of preparation. |
| Clarity Gap | Too much information, not enough signal. Information without context creates paralysis. |
| Activation Gap | Knowing and doing are separated by more than intention. Krovos closes that gap. |

---

## The Outcome Hierarchy

1. **Understanding** — "I understand my situation"
2. **Clarity** — "I understand my options"
3. **Confidence** — "I know what to do"
4. **Capability** — "I can handle this"
5. **Peace of Mind** — "I can stop worrying about this"
6. **More Living** — "I can spend less time worrying and more time living"

The ultimate outcome is Peace of Mind and More Living — not financial optimization.

---

## Life Phase Framework

| Phase | Characteristics |
|---|---|
| Foundation | First job, first independent financial life, building habits. Can happen at 22 or 35. |
| Building | Active construction: career development, first home, family formation. High decision density. |
| Expansion | Increasing complexity: growing family, career advancement, education planning. Open loops multiply fastest. |
| Optimization | Career peak, financial sophistication, approaching retirement horizon. |
| Transition | Major disruptions: divorce, career change, loss, early retirement. Maximum need for guidance. |
| Stewardship | Legacy prep, aging parents, estate planning, retirement income management. |

Life phase is always inferred by Krovos — never shown as a label to the user.

---

## Current Pricing Structure

| Tier | Price | Notes |
|---|---|---|
| Krovos Core | $15/month or $149/year | Founding rate: $12/month locked for life |
| Life Phase Guides | $49 each, one-time | Phase-triggered add-ons |
| Krovos+ | TBD | To be defined once Core is fully built |

*Krovos Guide (AI conversation layer) is included in Core.*

---

## Product Naming System (Locked)

| Old Name | New Name | What It Is |
|---|---|---|
| Smart Start | Life Profile | Onboarding flow |
| Life Understanding Report | Life View | Core report deliverable |
| Life Graph | Life Graph | Data model (unchanged) |
| Trusted Guide | Krovos Guide | AI conversation layer |
| Navigation Scoreboard | Life Compass | Progress/orientation view |
| Life phase modules | Life Phase Guides | Add-on module family |

---

## What Is Built (V1)

- Authentication (Supabase Auth)
- Life Profile intake (9 sections, adaptive, state-restored on back navigation)
- Document extraction pipeline (Claude API reads PDFs)
- Life Graph schema (PostgreSQL, row-level security)
- Life View report (paginated, 6 sections)
- Animated loading overlay (KrovosLoader)
- Dashboard with progress tracking
- Marketing landing page with waitlist (Supabase-backed)
- Privacy Policy and Terms of Service pages
- Sign-in and Sign-up pages (brand-updated)

---

## Known Bugs (Fix Queue)

- [ ] Auth redirect loop — proxy.ts session handling (fix built, in validation)
- [ ] Company display name in reports: legal entity (McKissock LP) instead of public brand (Colibri Group)
- [ ] Partner income not surfacing correctly from uploaded documents
- [ ] Gross salary vs net salary display in reports
- [ ] Dashboard does not reflect onboarding completion state on all paths
- [ ] Smart Start older pages: missing KrovosIcon, old light card styling, tagline violation
- [ ] Tagline appearing on in-app pages — violation of brand rules

---

## Immediate Build Queue (Pre-Launch Blockers)

- [ ] Landing page V3 — complete brand-compliant rewrite with new product names
- [ ] In-app rename: Smart Start → Life Profile, Life Understanding Report → Life View
- [ ] Resend email integration — welcome, confirmation, Life View ready notification
- [ ] Stripe integration — subscription billing + Stripe Tax (Tennessee SaaS)
- [ ] Paywall — gate Life Profile behind active subscription
- [ ] OG image — for social sharing
- [ ] White-glove prompts — surface extracted data and ask targeted follow-up questions

---

## CORE PRODUCT ROADMAP

### Phase 1 — The Foundation (V1, Current)

**Life Profile (Onboarding)**
Design philosophy: the beginning of a relationship, not a data collection exercise.
- Passive understanding first: what can be learned without asking?
- Document upload eliminates entire categories of questions
- Progressive disclosure: only ask what is needed now
- Minimize the cost of being understood

Documents Krovos processes:
- Pay stub: income, tax withholding, benefits deductions, retirement contributions
- Tax return: full income picture, deductions, dependents, investment income
- Insurance cards: coverage types, carrier, plan level
- Mortgage statement: balance, rate, monthly payment, equity position
- Student loan statement: balance, rate, repayment plan, monthly payment
- Investment account statements: portfolio size, allocation, contribution rate

**Life Graph**
Seven domains of understanding:
| Domain | Data Types |
|---|---|
| Financial | Income, assets, liabilities, insurance, benefits, tax situation, retirement position |
| Family | Household composition, dependents, caregiving responsibilities, relationship status |
| Career | Current role, industry, career stage, income trajectory, professional goals |
| Household | Housing situation, geographic context, recurring obligations |
| Goals | Short, medium, and long-term objectives across all domains |
| History | Decisions made, milestones achieved, setbacks navigated |
| Life Phase | Current phase identification and approaching transitions |

**Life View Report**
Architecture:
1. Life Phase Summary — "that's exactly me" recognition moment
2. Financial Snapshot — clear, honest, not alarming
3. Burden Inventory — prioritized list of open loops
4. Opportunity Map — what the situation makes possible
5. Priority Guidance — two or three things that matter most first
6. Navigation Horizon — what is approaching that requires preparation now

V1 success: Recognition ("that's exactly me") + Clarity ("now I know what to focus on") + Relief ("I feel less overwhelmed")

---

### Phase 2 — The Ongoing Relationship

**Life Compass**
Replaces the static dashboard. The ongoing navigation surface.
- Not a dashboard — a navigation system
- Shows what matters most right now: active priorities, approaching decisions, progress markers, open questions
- Organized by life phase relevance, not financial category

**Paycheck Tracking**
- Krovos knows the user's pay schedule from Life Profile
- On pay dates: "Your paycheck landed. Want to confirm your income this month?"
- Tracks what came in vs. expected
- Flags discrepancies
- Shows goal progress on each payday
- Celebrates milestones with specific context

**Goal Navigation**
- Goals set in Life Profile (buy a house, pay off debt, emergency fund, retire by X)
- Krovos builds a path to each goal with monthly progress markers
- Time horizon displayed for each goal
- Monthly: "Here is where you are on your Home goal. Here is what to do this month."
- Proactive alerts when on track or off track

**Navigation Calendar**
A Krovos-managed view of financial and life events:
- Pay dates, bill due dates, subscription renewals, insurance renewals
- Open enrollment windows, tax deadlines
- Goal milestones and checkpoints
- Life events that need financial planning (school year start, holidays, lease renewal)
- User can add events; Krovos contextualizes them financially
- Krovos pre-populates based on Life Graph

**Monthly Life View Refresh**
- When significant changes occur (new job, new income, new goal, major purchase)
- User uploads updated documents; Krovos regenerates the Life View
- "Your life has changed since your last View. Here is what is different."

**Proactive Alerts (Navigation Moments)**
Trigger types:
- Time-based: open enrollment window, tax season, year-end review, lease renewal
- Life event: new job, new baby, marriage, divorce, home purchase
- Data-based: savings rate dropped, debt increased, retirement trajectory shifted
- Milestone-based: emergency fund complete, debt paid off, first $X invested
- Approaching horizon: decision flagged in Life Profile now 60/30/14 days away

**Contextual Education**
Not generic content — the right information at the right moment:
- Homebuying goal → what PMI is, before they ask
- First tax season with mortgage → what changed
- New child → life insurance basics, why now
- Raise received → what to do with the increase, in priority order
- Emergency fund low → why 3-6 months matters for their life phase
- Retirement threshold approaching → contribution decision support

---

### Phase 3 — Mental Load Reduction & Life Coordination

**The Mental Load Layer**
The most ambitious and most differentiated feature. Krovos carries the things the user should not have to keep in their head.

**Birthday & Family Event Coordination**
- User inputs family birthdays, anniversaries, school events, holidays in Life Profile or calendar
- Krovos surfaces 30-60 days in advance with financial context
- "Emmeline's birthday is in 6 weeks. Based on your situation, here is how to plan for it now."

**Holiday Planning**
- Krovos knows the user's family situation from Life Graph
- October: "The holidays are 10 weeks away. Based on your household, here is what to prepare."
- Gift planning, travel planning, budget allocation — surfaced before stress arrives

**School Year Planning**
- If user has children, Krovos tracks school calendar context
- Back-to-school: supplies, clothing, activity fees surfaced in advance
- Sports seasons, field trips — all with financial context and planning prompts

**Life Event Anticipation**
- If user indicated homebuying goal in 3 years, Krovos starts preparing them 24 months out
- Month by month: what to do now, what to gather, what to work on
- "18 months from your target home purchase. Here is what your credit score needs to look like."

**Intelligent Push Notifications**
Not noise — signal relevant to the user's specific situation:
- Pay date confirmations
- Goal milestone alerts
- Off-track alerts for specific goals
- Bill due date reminders
- Life event planning prompts (30 days before calendar milestones)
- Market condition alerts relevant to active goals
- Educational nudges when Life Graph signals a teachable moment
- Home listing alerts for users with homebuying goals (matching criteria in target area)
- Interest rate monitoring alerts when conditions shift for active goals

---

### Phase 4 — Krovos Guide (AI Advisor Layer)

Included in Core. The questions that come up every day, answered by something that knows the complete Life Graph.

**Interaction Principles:**
- Orient first: understand where the person is before responding to the surface question
- Demonstrate memory actively: reference what Krovos knows — never make the user re-explain
- Name what you're seeing: acknowledge what the question reveals about their situation
- Recommend specifically: every recommendation grounded in actual numbers and situation
- End with a clear next step: every exchange concludes with something actionable
- Be honest when honest is hard: say it with compassion and with options

**What it answers:**
- "Should I take this job offer?" — with context from salary, benefits, goals, life phase
- "What does this letter from the IRS mean?" — with context from filing status and income
- "Is it okay to use savings for this?" — with context from emergency fund, goals, budget
- "We want to go on vacation. Can we afford it?" — with full financial picture
- "My landlord is raising my rent. What are my options?" — with housing goal and financial context
- "We're thinking about having another child. What does that mean for us financially?" — with complete household picture

---

### Phase 5 — Financial Resilience Engine

Full specifications from founding documents:

**Emergency Fund Engine**
- Calculates adequate emergency fund based on fixed expenses, dependents, income stability, job market
- Shows current status as months-of-coverage, not raw dollar amount
- Phase-appropriate targets (Building phase: 3-6 months; Transition phase: 6-12 months)

**Debt Optimizer**
- Prioritizes debt payoff across all balances
- Avalanche (highest interest first) vs. snowball (smallest balance first) with side-by-side comparison
- Models total interest saved for each approach
- Incorporates the user's psychological profile (some people need quick wins)

**Paycheck Allocation System**
- Distributes take-home pay across obligations, savings goals, and discretionary spending
- Based on the person's specific income, expenses, and goals
- Updates automatically when income or expenses change

**Retirement Trajectory**
- Models current position against retirement goal
- Uses actual income, contribution rate, employer match, investment growth assumptions
- Shows the gap and what closes it — specific to their numbers

**Coast FI Calculator**
- Identifies the point at which current savings, if left invested, will grow to retirement goal without additional contributions
- Answers: "Could I stop contributing now and still be okay?"

**FIRE Projection**
- Models financial independence timeline based on savings rate, current assets, and spending
- For users actively pursuing early retirement or financial independence

**Savings Vault System**
- Goal-segregated savings tracking
- Shows progress toward each named goal independently (down payment, emergency fund, vacation, education)

**Milestone Engine**
- Tracks meaningful financial milestones (first $10K saved, debt-free, 1 year of emergency fund)
- Celebrates them with specific context about what they represent

**Net Worth Tracker**
- Total picture updated over time
- Assets minus liabilities tracked across time to show direction and rate of change

---

### Phase 6 — Household Operations Engine

**Household Calendar**
- Financial and life events in one view
- Bill due dates, insurance renewals, enrollment windows, tax deadlines, user-defined events

**Division of Labor System**
- Tracks household responsibilities to ensure equitable distribution
- Identifies overload and suggests rebalancing

**Children's Planning Toolkit**
- Childcare cost modeling
- 529 education savings with state deduction analysis
- Activity and extracurricular budget tracking
- College cost projection by school and major

**Parental Leave Planner**
- Models income during leave
- Employer policy analysis
- State benefit calculation
- Savings required to bridge any income gap

**Household Budget Framework**
- Ongoing monthly household financial management
- Income, fixed expenses, variable spending, savings — with variance tracking

**Document Vault**
- Secure storage of essential household documents
- Birth certificates, insurance cards, wills, property documents, vehicle titles, medical records

---

### Phase 7 — Optimizer Engine

**Annual Enrollment Comparison**
- Side-by-side analysis of health insurance plan options
- Based on actual utilization history, premium vs. deductible tradeoff, HSA eligibility
- Recommends optimal plan for this person's specific situation

**Credit Card Engine**
- Identifies optimal credit card or combination based on actual spending patterns
- Models annual benefit value including travel, cash back, and perks
- Identifies when annual fee is or isn't worth it

**Tax Planning Toolkit**
- Year-round tax awareness
- Estimated quarterly tax, withholding adequacy, deduction tracking
- Roth conversion opportunity identification
- Tax-loss harvesting alerts

**Career Path Tool**
- Income trajectory modeling based on role, industry, and tenure
- Compensation negotiation support
- Career decision financial modeling (industry change, education investment, geographic move)

**Insurance Adequacy Analyzer**
- Identifies coverage gaps across life, disability, health, auto, home, and umbrella
- Benchmarks against recommended coverage for the person's specific situation

**Refinance Calculator**
- Evaluates whether refinancing mortgage, auto, or student loans makes sense
- Given current rates, break-even timeline, and remaining loan life

---

### Phase 8 — Young Adult Engine

**College Decision Engine**
- Total cost of attendance modeling across schools
- Debt load projection by major and career path
- ROI analysis: "Is this school worth this price for this student?"

**Career Alignment Assessment**
- Connects interests, skills, and values to career options
- Realistic income trajectory and market demand data

**Early Career Starter Kit**
- First job financial checklist
- Benefit selection guidance, retirement contribution decision
- Emergency fund starting point, student loan repayment selection

**Student Loan Strategy**
- Full repayment analysis across standard, income-driven, and forgiveness pathways
- Refinancing evaluation
- Extra payment impact modeling

**First Apartment Planner**
- True cost of independent living: rent, utilities, renters insurance, groceries, transportation
- Modeled against income to determine feasible budget

---

### Phase 9 — Life Phase Guides (Modular Marketplace)

One-time purchase, owned forever, updated when conditions change significantly.

**Home Buying Guide — $49**
Triggered when: Life Graph shows homeownership as a goal
- Purchase readiness assessment
- Full cost modeling (down payment + closing costs + immediate repairs + ongoing ownership)
- Mortgage qualification pre-analysis
- What PMI is and when you pay it
- How mortgages actually work (the real math)
- Pre-approval explained: why it matters before you shop
- Process timeline and checklist
- What to do after closing
- Custom action plan from Life Graph
- Proactive alerts: rate changes, listings matching criteria in target area and price range
- PMI removal tracker: tracks when user hits 20% equity and can request removal

**New Parent Guide — $49**
Triggered when: user adds a dependent to Life Graph
- How taxes change when you have a child
- Life insurance: what it is, how much you need, when to get it
- Starting a 529 or other education savings: when and how
- Adjusting retirement contributions given new household expenses
- Building a financial foundation for a growing family
- Custom action plan for specific household situation

**Career Transition Guide — $49**
Triggered when: user updates employer, income, or indicates job change
- What to do with old 401(k): rollover options explained
- How to evaluate a benefits package (health, dental, 401k match, equity)
- Adjusting withholding for new salary
- What the income change means for specific goals
- Custom action plan from Life Graph

**Caregiver Guide — $49**
Triggered when: user indicates supporting aging parents or family members
- How caregiving affects your own finances
- What Medicare and Medicaid cover vs. what they don't
- Power of attorney, healthcare directives: what to have in place
- How to have the money conversation with aging parents
- Planning your own finances while supporting theirs
- Custom action plan for specific caregiving situation

**Estate Planning Guide — $49**
Triggered when: user has dependents, owns property, or reaches a certain asset level
- What a will actually does and why you need one
- Trust basics: when they make sense
- Beneficiary designations: the most commonly missed step
- What happens without these documents in place
- How to find and work with an estate attorney
- Document checklist for specific family and asset situation

**Divorce & Transition Guide — $49**
Triggered when: user indicates relationship status change or major life disruption
- Financial separation guidance
- Single income adjustment planning
- QDRO and retirement account division overview
- Credit rebuilding framework
- Rebuilding savings plan

**Inheritance Guide — $49**
Triggered when: user indicates receiving an inheritance
- Lump sum decision framework
- Tax implication overview
- Integration into existing financial plan
- Avoiding common inheritance mistakes

**Business Owner Guide — $49**
Triggered when: user indicates self-employment or business ownership
- Business and personal finance integration
- Retirement account options for self-employed (SEP-IRA, Solo 401k)
- Exit planning framework
- Succession considerations

**Retirement Guide — $49**
Triggered when: user enters optimization or stewardship phase, or sets retirement goal
- How to calculate your actual retirement number for your life
- Social Security: when to claim and why it matters
- RMDs, Roth conversions, and tax strategy in retirement
- Healthcare before and after Medicare eligibility
- Creating income from assets
- Custom retirement timeline from Life Graph

---

### Phase 10 — Partner Referral Network

Krovos connects users with trusted professionals when the Life Graph signals a need and the user is ready.

**Non-negotiable principles:**
- Every referral driven by user fit, not partner economics
- Full disclosure on all referral relationships
- Krovos never receives undisclosed compensation
- User always in control of whether and when to connect
- Recommendation criteria are transparent

**Partner categories:**
- Mortgage lenders (triggered by homebuying goal)
- Estate attorneys (triggered by Estate Planning Guide purchase)
- CPAs / tax professionals (triggered by tax complexity signals)
- Licensed financial advisors (triggered by investment or retirement complexity)
- Insurance providers (triggered by insurance gap identification)
- Elder law attorneys (triggered by Caregiver Guide purchase)

---

### Phase 11 — Employer Wellness Partnerships

Krovos offered as an employee benefit. Employer pays for access on behalf of employees.

**Why this matters:**
- High-volume acquisition with very low CAC
- Employer endorsement creates instant trust signal
- Financial wellness is a growing HR priority
- Krovos is uniquely positioned as non-conflicted guidance

**Target employers:** Mid-size companies 100-5,000 employees, HR/benefits-focused industries

---

### Phase 12 — Krovos+ (Future Premium Tier)

*To be defined once Core is fully built and user behavior patterns emerge.*

Potential inclusions (not locked):
- Enhanced Krovos Guide with deeper conversation history
- Advanced Life View with scenario modeling ("what if" planning)
- Couple/household shared navigation (both partners full access)
- Annual CFP consultation access (licensed human advisor)
- Priority alerts and market monitoring
- Early access to new Life Phase Guides

---

## Measurement System

| Metric | Layer | What It Measures | Target |
|---|---|---|---|
| Indispensability Score | Mission | "Can't imagine navigating without Krovos" | 40% at 6mo; 60% at 12mo |
| Burden Score | Mission | Total burden carried across 4 categories | Decreasing trajectory from onboarding |
| Relief Indicator | Mission | Overwhelm level change from baseline | 3+ point decrease in 90 days |
| Recognition Rate | Relationship | Report felt specific vs. generic | Above 85% |
| Life Graph Depth | Relationship | All 7 domains covered | All domains for engaged users |
| Guidance Acceptance | Relationship | Recommendations followed within 30 days | Tracked over time |
| Life Profile Completion | Product | Onboarding completion | Above 70% |
| Document Upload Rate | Product | At least 1 doc uploaded | Above 50% |
| Burden Resolution Rate | Product | Open loops closed per month | Increasing over time |
| 12-Month Renewal | Business | Annual subscription renewal | Above 80% |
| NRR | Business | Net Revenue Retention | Above 110% at marketplace maturity |

**North Star Metric:** The percentage of users who, at 12 months, say they cannot imagine navigating their financial and life decisions without Krovos. Target: 40% at 6 months, 60% at 12 months.

---

## Ideas Backlog (Not Yet Specced)

**Product Ideas**
- [ ] Couple/household mode — shared Life Graph, both partners contribute documents
- [ ] Mobile app (iOS/Android) — native push notifications for all alerts
- [ ] Voice interface — ask Krovos Guide by speaking
- [ ] Document auto-sync — connect to payroll provider or financial institution directly
- [ ] Credit score monitoring — integrated into Life Graph
- [ ] Tax preparation assistance — organization and document prep, not filing
- [ ] Home listing alerts — matching listings in target area and price range for homebuying goal users
- [ ] Interest rate monitoring — alerts when rates shift for active goals
- [ ] Annual Life View comparison — "here is how your situation changed in the past year"
- [ ] Life phase progression notification — "you are entering a new phase"
- [ ] PMI removal tracker — tracks when homeowner hits 20% equity
- [ ] Debt paydown tracker — which debt to pay first, progress over time
- [ ] Emergency fund progress tracker with milestone celebrations
- [ ] Savings rate calculator — percentage of income being saved
- [ ] Retirement readiness score — simple indicator updated monthly
- [ ] Life insurance needs calculator — based on dependents, income, and debt
- [ ] Beneficiary reminder — annual prompt to review and update beneficiaries
- [ ] Estate document checklist — does the user have what they need in place
- [ ] Subscription tracker — what recurring charges are coming and when
- [ ] Bill calendar — upcoming bills, due dates, and amounts integrated into Navigation Calendar
- [ ] Investment tracking — 401k, IRA, brokerage balances and performance
- [ ] Scenario modeling / "what if" planning — what if I take this job? what if we have another child?
- [ ] Financial independence number calculator — personal to their situation and goals

**Business Ideas**
- [ ] Krovos for Employers — B2B wellness benefit channel
- [ ] Krovos Certified Partner program — for attorneys, CPAs, and advisors who want referrals
- [ ] Krovos API — for financial institutions or HR platforms to embed Life Navigation
- [ ] White-label Krovos — for credit unions, community banks, or HR platforms

**Content & Marketing Ideas**
- [ ] "The Gap" content series — what school never taught, one topic per post
- [ ] Life Phase content tracks — organized by phase (early career, new parent, homeowner, etc.)
- [ ] Krovos Letter — weekly email with one piece of relevant life navigation content
- [ ] Founder content — brand voice, no personal identifying information
- [ ] Testimonial/case study content — real Life View moments (with permission)
- [ ] Partner co-marketing — with trusted professional partners

---

## Business Model — Full Picture

| Revenue Stream | Description | Status |
|---|---|---|
| Core subscription | $15/month or $149/year | Stripe integration needed |
| Founding member rate | $12/month locked | Offer active |
| Life Phase Guides | $49 one-time each | Post-100 subscribers |
| Partner referrals | Transparent, user-aligned | Post-250 subscribers |
| Employer wellness | B2B channel | Future phase |
| Krovos+ | Premium tier | TBD after Core is built |

---

## The Competitive Moat (Three Layers)

1. **Life Graph Depth** — accumulated understanding that deepens over years; cannot be replicated or transferred
2. **Trust Relationship** — people who have shared their lives with Krovos do not switch for features
3. **Category Ownership** — define Life Navigation, become it; new entrants fight the category

**The Flywheel:** More users → richer pattern library → better recognition → stronger trust → deeper sharing → better Life Graph → more relevant guidance → more value → more retention → more users

---

## Next Time You Ask "What Is Next For Us To Work On?"

Surface these as options:

**Pre-launch blockers:**
1. Landing page V3 — complete rewrite with all feedback addressed
2. In-app rename — Smart Start → Life Profile, Life View everywhere
3. Stripe integration — subscription billing + Stripe Tax
4. Resend email module — welcome, confirmation, Life View ready

**Core product build:**
5. Life Calendar — spec and build (now formally on roadmap)
6. Paycheck tracking — spec and build
7. Goal navigation — spec and build
8. Krovos Guide — AI conversation layer in Core
9. Life Compass — replace static dashboard with navigation surface

**Marketing:**
10. Social content scheduling — 90-day calendar is ready
11. Kit email journey setup — all 5 sequences are written
12. OG image — add to public folder and wire into layout

**Business:**
13. TNTAP registration
14. Blount County business license ($15)
15. Stripe + QuickBooks setup
16. Trademark attorney


---

## ADDITIONAL TOOLS & FEATURES RECOVERED FROM READY SYSTEM DOCUMENTS

*The following features were specified in The Ready System business plan, product roadmap, and pitch decks (the predecessor to Krovos). All are valid for the Krovos roadmap.*

---

### Financial Tools — Detailed Specifications

**Paycheck Allocation Engine ("The Runway Calculator")**
- Monthly view with pay dates and all bill due dates
- Drawdown from paycheck in real time as expenses are allocated
- Categories: Fixed Expenses → Savings Vaults → Investments → Runway (what remains)
- Color-coded: green (on track), amber (tight), red (over-allocated)
- Account-level view: which account each payment draws from
- Autopay flags
- Multiple paychecks per month (biweekly, semi-monthly, etc.)
- "Runway" = what remains after all allocations — intentional discretionary money

**Freedom Scenarios (Three-Column Planning)**
- Three independent columns: Best Case, Likely Case, Worst Case
- Each column has its own inputs: return rate, exit age, monthly expenses, inflation, SWR, pension COLA, SS amounts, other income
- Outputs: portfolio at exit, guaranteed floor, monthly surplus/deficit
- Dashboard snapshot shows all three side-by-side

**Life Phase Buckets (Variable Expense Matrix)**
- Life phases as columns, spending categories as rows
- Toggle on/off per phase per category
- Monthly amount input per active cell
- Base expense + variable layers
- Phase totals, lifetime estimate

**State/Location Intelligence**
- State field captures for income tax estimation, cost of living context, retirement destination planning
- 9 states have no income tax — meaningful lever for retirement location decisions
- State-by-state tax table (all 50 states + DC, updated annually)
- State retirement tax comparison: "How does moving from [current state] to [retirement state] change annual tax burden?"

**Auto-Generated Milestones Engine — Full Specification**
Financial milestones calculated from user data:
- Debt payoff dates (per account)
- Coast FI achievement date
- Full FI achievement date
- Mortgage payoff date
- Emergency fund fully funded (3-month, 6-month)

Life milestones from household data:
- Age 59½ (retirement account access, no penalty)
- Age 62 (Social Security early claim eligible)
- Age 65 (Medicare eligible)
- Age 67/70 (Social Security full/maximum benefit)
- Each child: kindergarten entry (childcare cost drops), 18th birthday, college start estimate
- Pension activation age(s)

**Tax Planning & Optimization Engine — Full Specification**
- Federal + state income tax estimation
- Marginal bracket calculator (married filing jointly, single, head of household)
- Standard vs. itemized deduction comparison
- FICA (Social Security + Medicare) estimation
- Effective vs. marginal rate display
- Traditional vs. Roth contribution comparison: tax now vs. tax later math
- Roth conversion ladder planning: how much to convert per year in early retirement
- ACA income management: how portfolio withdrawals interact with ACA marketplace subsidy cliffs
- IRMAA thresholds (Medicare premium surcharges at higher income)
- Capital gains planning: long-term vs. short-term rate comparison
- 0% LTCG bracket planning for early retirees
- What percentage of Social Security is taxable based on combined income
- Pension taxation by state
- RMD (Required Minimum Distribution) projection starting at age 73

**Annual Enrollment Comparison Tool — Full Specification**
- Side-by-side analysis of health plan options
- Employee premium calculator
- Out-of-pocket maximum comparison
- HSA vs. FSA eligibility and contribution limits
- Net annual cost modeling (premium + expected utilization)
- Which combination is most cost-effective for the household
- FSA/HSA contribution optimizer
- Life insurance evaluation (employer group term vs. private term)
- Dental, vision, disability coverage comparison

**Credit Card Comparison Engine — Full Specification**
- Side-by-side comparison of up to 4-5 cards
- Benefits value calculator: select which features you'd actually use, total the value
- Annual fee vs. rewards value analysis
- Transfer partners for points/miles with redemption value estimates
- Sign-up bonus calculator (with minimum spend requirement)
- Responsible credit education integrated:
  - Credit card decision tree (is a credit card right for me?)
  - Credit score fundamentals
  - How to open a card responsibly
  - Understanding APR and the true cost of carrying a balance
  - When NOT to open a credit card
- No paid placements — purely educational comparison

**Social Security Optimization Calculator**
- Dedicated breakeven analysis at 62/67/70 by claiming age
- Exact earnings history input
- Spousal benefit coordination
- Survivor benefit planning

**Medicare Planning Tool**
- Coverage decisions at 65
- Gap coverage options
- Medicare Advantage vs. Supplement comparison
- IRMAA surcharge planning

**Home Sale Proceeds Planner**
- Net proceeds calculation
- Capital gains overview
- 1031 exchange basics
- Where proceeds should go in the Life Graph

**Quarterly Estimated Tax Calculator**
- For freelancers, self-employed, investment income
- Safe harbor calculation
- Due date calendar integration

**Renting vs. Buying Decision Engine**
- True cost comparison including opportunity cost of down payment
- Break-even timeline
- Market conditions context

---

### Calendar — Full Specification

**The Ready Calendar / Navigation Calendar**
- Full household calendar replacing Google Calendar
- Per-household-member color coding (each person has their own color layer)
- Toggle views: Financial, Household, Children, Work, All
- Family combined view + individual views
- Recurring events, reminders, tasks
- Mobile-first design
- Sharing with permission tiers:
  - Owner: full edit/view
  - Household member: full edit own layer, view others
  - Caregiver/babysitter: view designated calendars + shift signup
  - Read-only guest
- Babysitter/childcare shift management:
  - Post available shifts
  - Caregivers sign up
  - Confirmation and reminder notifications
- Financial calendar layer: bill due dates, paydays, annual fees, subscription renewals auto-populated
- Milestone layer: all auto-generated milestones appear on calendar
- Partner integrations: Google Calendar export, Apple Calendar export
- Future: Skylight/shared display integration for home display screen

---

### Division of Household Labor — Full Specification

- Walk through every household responsibility category: home maintenance, childcare, meal planning, finances, scheduling, medical, etc.
- Assign tasks/categories to household members with agreed ownership
- Weekly and monthly checklists per assigned member
- Grocery lists (shared, real-time, assigned)
- Chores and household tasks with completion tracking
- Regular re-evaluation prompts (quarterly or at life stage transitions)
- Integration with Calendar: tasks auto-populate assigned member's calendar
- Mobile-accessible so tasks can be checked off on the go
- Tracks balance of labor over time — surfaces imbalances without judgment
- Structured as task/accountability software, not card-based

---

### Children's Planning — Full Specification

- Individual profile per child (name, birth year, school status)
- Expense tracker by child: childcare, activities, medical, clothing, school fees
- Activity planner/comparison tool:
  - Add multiple activities per child
  - One-time vs. recurring cost toggle
  - Compare options side-by-side (cost, time commitment, season)
  - Equipment/supply costs attached
  - Summer camp planning and cost tracking
- 529 education savings calculator with state deduction analysis
- College cost projection by school and major
- Childcare cliff modeling (when childcare costs drop at kindergarten entry)

---

### Young Adult / Early Career — Full Specification

**College Decision Engine**
- Major selection → career trajectory → earning potential projector
- Uses real labor market data (BLS, salary databases)
- 10-year and 20-year earning trajectory by field
- Cost comparison: 4-year university vs. community college transfer vs. trade school vs. certificate/bootcamp
- Student loan calculator:
  - Federal vs. private loan comparison
  - Income-driven repayment projection
  - Total interest paid over loan lifetime
  - Time-to-payoff at different income levels
  - PSLF eligibility tracker (Public Service Loan Forgiveness)
- College cost vs. income recoupment timeline: "How long until your degree pays for itself?"
- Scholarship and aid planner

**Life & Career Alignment Assessment**
- Interest + values assessment
- Maps to career clusters with earnings data
- "If you pursue [career], here's what the financial trajectory looks like"

**Early Career Financial Starter Kit**
- First job financial setup checklist:
  - Set up direct deposit
  - Enroll in 401k (contribute at least to employer match)
  - Open Roth IRA
  - Open HYSA for emergency fund
  - Understand your pay stub
  - Understand your benefits
- Credit fundamentals for first-time users
- Renting your first apartment: budgeting, lease terms, security deposits
- Starter budget template
- Financial vocabulary glossary

---

### Pay Transparency & Career Path Tool — Full Specification

- Job title market rate data by geography
- Compensation range by experience level
- Promotional track modeling: current role → next role → 5-year trajectory
- Internal vs. external move comparison (compensation + total comp)
- Negotiation planning tool: current offer, market rate, target range, talking points
- Career switching cost calculator (re-education, transition period, long-term upside)

---

### Viral / Sharing Features

- "See your life phases" shareable visualization from the Life Profile
- Life phase completion share triggers ("I just completed my Krovos Life Profile")
- Referral program: users receive credit for referred subscribers
- Annual Life Graph share: "here is how my situation changed this year"

---

### Financial Modes (Overlay System)

These Financial Modes overlay any life phase and trigger specific toolsets:

| Mode | Who It's For | What It Activates |
|---|---|---|
| Debt-Free | Paying off debt is the priority | Debt tracker, avalanche/snowball, payoff timeline |
| FI/FIRE | Aggressive savings, early retirement | Coast FI, FIRE projections, SWR calculator |
| Family | Kids, childcare, education funding | Children's planning, parental leave, 529 |
| Self-Employed | Variable income, quarterly taxes | Quarterly tax calc, SEP IRA, business finances |
| Starting Over | Divorce, job loss, relocation | Rebuilding plan, credit rebuilding, single income adjustment |

---

### Bundles (Future Packaging Concept)

- Young Professional Bundle: Core + Early Career module
- Growing Family Bundle: Core + Household + Children's Planning
- Pre-Retirement Bundle: Core + Tax Planning + SS Optimizer + Medicare
- The Full System: All modules at meaningful discount

---

### Marketing Statistics (From Business Plan)

- 73% of Americans report money as their top stressor
- 130M+ Americans need financial planning but can't access/afford a human advisor
- 82% of adults want personalized guidance but can't afford an advisor
- 91% of millennials say they would pay for a "life guide" if affordable
- $47B personal finance and life wellness market (2026)
- 180M+ US adults in active life transition

---

### IP & Legal Notes (From Roadmap)

- "Runway" (term for discretionary spending): conduct formal trademark clearance before launch
- Division of Labor system: built as task/accountability software, not card-based — structurally distinct from Fair Play card deck IP
- All financial content: educational framing only. Disclaimer on every financial calculation page
- Credit Card Engine: no paid placements or referral fees — purely educational comparison
- College Decision Engine: uses publicly available labor market data (BLS, O*NET) — cite sources


---

## ADDITIONAL TOOLS FROM READY SYSTEM HTML BUILD

*The following were built and working in the original HTML prototype.*

**Childcare Bubble / Temporary Phase Tracking**
- Childcare expense isolated as a temporary phase cost, not a permanent lifestyle expense
- Countdown display: months remaining until childcare drops off
- Total remaining childcare outflow calculated
- When expense drops, savings rate automatically recalculates
- Progress bar showing percentage of childcare phase elapsed
- "Cliff date" projected and freed capital modeled forward

**Household Weekly Matrix**
- 7-day grid (Mon-Sun) per household member
- Click any cell to add a note, routine, or task block for that day
- Tracks recurring household routines visually
- Designed for household operations visibility

**Horizon Expense Buffer**
- Separate container for temporary 2-4 year large expenses
- Isolates upcoming large costs from long-term FI planning
- Examples: car upgrade, home renovation, relocation costs
- Each item has amount + target date
- Total reserve needed calculated across all horizon items
- Prevents large one-time expenses from disrupting FI projections

**FIRE Spectrum (Three Variants)**
- Lean FIRE: 75% of FI spend target — frugal early retirement
- Standard FIRE: full FI spend target — your baseline
- Fat FIRE: 150% of FI spend target — comfortable retirement
- Each shows projected retirement age based on current trajectory

**Timeline Bridge Calculator**
- Calculates gap years between one partner's retirement and the other's pension/SS activation
- Models exact bridge fund capital required to cover the gap
- Timeline visualization: Person A retirement → Person B retirement → Pension/SS activates → Full income restored
- Critical for dual-income households with staggered retirement timelines

**Lever Analysis — What Moves the Needle Most?**
- Three levers analyzed side-by-side:
  - Save 10% more per year → years saved vs. base case
  - Spend 10% less in retirement → years saved vs. base case
  - +1% return assumption → years saved vs. base case
- Shows user which lever has the highest impact on their specific trajectory

**Year-by-Year Projection Table**
- Complete table from current age through retirement
- Columns: Year, Age (Person A), Portfolio Value, Annual Contribution, FI Progress %, Status
- Milestone rows highlighted (Coast FI achieved, FI achieved, pension activation, SS start, Medicare age)
- Color-coded surplus/deficit

**Live Savings Rate Calculator**
- Calculates and displays savings rate in real time as user enters income and savings
- Shows on questionnaire as user types — immediate education moment
- Net income basis (savings / net take-home, not gross)

**Staggered Retirement Tracking**
- Two-person household support with independent retirement ages
- Person A and Person B each have their own:
  - Current age
  - Target retirement age
  - Income
  - Pension details
  - Social Security estimate
- System manages staggered timelines automatically across all projections

**Dynamic Debt Ledger**
- Payoff timelines recalculate dynamically with any extra principal payment
- Not rigid amortization — each extra dollar is immediately reflected
- Visual debt cards per account
- Avalanche and Snowball toggle with real-time recalculation
- Monthly interest cost display per account
- Weighted average APR across all debts
- Debt-free target date updates as extra payments change


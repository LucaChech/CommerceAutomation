# Requirements Transcript — Brother's Business (Tobacco Commerce, Quito, Ecuador)

## Source
Cleaned and structured from voice transcript between project owner and brother (business owner).

---

## Key Requirements Identified

### 1. Order Management
- Clients place orders (currently via WhatsApp or direct contact)
- System should handle the full order intake process
- Future goal: system could also request courier pickup for completed orders

### 2. Payment Tracking & Installment Management
- Clients often pay in installments (e.g., $1000 total debt, agreed $250/week starting on date X)
- System should track agreed payment schedules (amount, frequency, start date)
- When a client sends a payment, the system should automatically:
  - Acknowledge receipt
  - Confirm the math (e.g., "Perfect, thanks. That was $1000 minus $250, $750 remaining")
  - Update the outstanding balance
- **Payment reminders**: System should proactively remind both the business owner and the client of upcoming payment due dates
- Essentially: automated accounts receivable with payment plan support

### 3. Bank Reconciliation (Conciliación Bancaria)
- Every bank transaction (incoming or outgoing) must be matched to an invoice
- Example incoming: "$250 received on March 8 at 2:35 PM corresponds to invoice #101"
- Example outgoing: "$100 paid out corresponds to invoice #104 from [supplier name]"
- Full traceability of all bank movements — this is described as a major pain point ("un lavoraccio")
- Each bank movement must be declared/tracked (regulatory or accounting requirement)

### 4. Invoice Generation
- System should automatically generate invoices for orders
- Goal: eliminate the need for a dedicated employee doing invoicing
- Invoices tied to orders, which then feed into bank reconciliation (requirement #3)

### 5. Client Portal (Web)
- A web portal with login credentials for clients (wholesalers and retail locations/"locales")
- Clients can either:
  - Write directly (e.g., via WhatsApp) and the system responds on behalf of the owner
  - Log into the portal and manage orders/payments through a self-service interface
- Portal should be managed by the system end-to-end
- **Portal and other channels (WhatsApp, etc.) coexist** — portal is an additional option, not a replacement

---

## Business Context Notes
- **Client types**: Wholesalers ("grossisti") and retail locations ("locali")
- **Communication channel**: Currently WhatsApp-heavy
- **Pain points**: Manual invoicing, manual bank reconciliation, manual payment tracking
- **Implicit need**: The brother wants to reduce headcount or free up employee time by automating back-office tasks

---

### 5b. Client Portal — Additional Details
- **Role-based access**: Users register and declare their type (end consumer, retail location/locale, or wholesaler/grossista)
- **Different price lists per role** — each user type sees different pricing
- Some products currently don't have prices set — this needs to be addressed
- **Order flow from portal**: Client logs in → places order → order is sent to an email → warehouse employees access that email and prepare the order → invoice generated
- **Santiago** (possibly an employee or developer) could handle the authentication/registration part, but brother is reconsidering his role — unclear, to be revisited

### 6. Invoicing — Personnel Note
- Invoice generation currently handled with help from Aura (brother's girlfriend)
- Potentially she could be given access to handle invoicing through the system, or it could be automated entirely

### 7. Promotions & Business Intelligence
- Brother says he **doesn't have time to think about promotions** — wants the system to handle this
- **Slow-moving inventory detection**: System should connect to accounting/inventory data and identify products that aren't selling (e.g., 200 out of 1000 SKUs sitting idle)
- **Automatic discounting**: Apply discounts or promotions to slow-moving products on the website automatically
- **Marketing strategy generation**: System should propose and execute promotional campaigns, e.g.:
  - Themed discount weeks by product category ("Bong discount week", "Grinder discount week")
  - Seasonal or monthly promotional calendars
- **Loyalty/membership programs**: System should design programs that are:
  - Beneficial to the client
  - Don't lose the business money
  - Examples mentioned: repurchase incentives (spend $X → get a discount coupon on next purchase within a date range)
  - Reference model: Tigotà / shopping center loyalty programs
- **Key point**: Not just suggesting promotions — brother wants the system to **think them up AND execute them automatically**

---

## People & Roles

### Internal employees (3)
- **Johnny** — Most senior employee, acts as supervisor. Prepares quotes/estimates ("preventivi"): brother forwards orders to him, Johnny sets prices based on client history, asks brother for pricing on new products or products new to a client. Once quote is done, passes it to the warehouse guys.
- **Guglielmo** — Warehouse/fulfillment, prepares orders
- **Jeremy** — Warehouse/fulfillment, prepares orders

### External / Non-employees (3)
- **Aura** — Brother's girlfriend, helps with admin and management tasks (loads inventory into Iconta)
- **Santiago** — Community manager (freelance). Manages social media (mainly Instagram), the web page, product catalogs, and online sales. When a client orders via the website, Santiago receives it, sends screenshot to brother to get pricing, then manages the client. Currently being "re-evaluated" by the brother.
- **Rodrigo** — External accountant ("commercialista"). Handles tax declarations for the state (VAT/IVA and imports)

### Total: 7 people including the brother (3 internal + 3 external + brother)

### 8. Accounting System & Inventory — Current State (Iconta)
- **Current accounting system**: **Iconta** (Ecuadorian accounting software)
- Inventory is managed within Iconta, not separately
- Products have been fully loaded into Iconta — each item has quantity and cost
- **Iconta is used for**: invoicing, inventory management, transport documents (guías de remisión), credit notes
- **Data import/export**: Supports bulk upload via pre-formatted Excel template; can also export data to Excel
- **API**: Iconta apparently has some API capability (can connect to WhatsApp, supports product registration via API calls), but unclear how complete it is
- **Reliability issues**: System crashes when loading many products at once, sometimes doesn't recognize items, general stability complaints — brother is not fully satisfied
- **Who does what in Iconta**:
  - Brother: mainly uses it for sales reference, provides pricing
  - Aura (girlfriend): loads inventory/products
  - Johnny: handles invoicing (new person mentioned — likely an employee)

### 9. Accounting System Migration — Key Considerations
- Brother had previously explored this with ChatGPT and concluded **Odoo** is the most recommended option
- **Brother is willing to switch from Iconta** if it enables better automation medium-term, despite the migration effort (recreating all clients, products, etc.)
- **Decision criteria** for choosing a system:
  1. **Cost-benefit**: If a more expensive system enables significantly more automation, the cost is justified
  2. **Ecuador compliance**: System must be legally valid for Ecuadorian tax authorities (SRI)
  3. **Invoicing compliance**: Must support legally valid electronic invoicing in Ecuador
- **Ecuador regulatory clarification** (partially confirmed with accountant, follow-up appointment on Tuesday):
  - **State-recognized system required for**: electronic invoicing, tax receipts ("comprobantes"), and tax reports ("reportes tributarios")
  - **Internal inventory tracking**: Can apparently use any system for internal purposes (stock tracking, purchase costs). The state-recognized system is needed for fiscal declarations, not necessarily day-to-day inventory management
  - This is still being clarified — brother will confirm with accountant
- **Possible hybrid approach**: Use a more capable system (Odoo?) for internal operations + keep a compliant system only for legally required functions (invoicing, tax reports)
- **Odoo & Ecuador**: ChatGPT indicated Odoo may support Ecuador localization, but needs verification

---

## Questionnaire Answers

### Q1. How many employees (including yourself)?
- **7 total**: Brother + 3 internal employees + 3 external collaborators

### Q2. Roles?
- See "People & Roles" section above

### Business Name
- **Apta Imports** (mentioned in context of the website)

### Order Flow (from questionnaire context)
1. Client places order (WhatsApp, web, etc.)
2. Brother forwards order to **Johnny**
3. Johnny prepares the quote ("preventivo") with prices based on client history
4. For new products or new-to-client products, Johnny asks brother for the price
5. Johnny sends completed quote to **Guglielmo** and **Jeremy**
6. They prepare/pack the physical order

### Online Sales Flow
1. Instagram drives traffic → client redirected to **Apta Imports website**
2. Client places order on website → order arrives via email
3. These are usually small orders (end consumers)
4. **Santiago** receives the order, screenshots it, asks brother for pricing
5. Santiago then manages the client interaction

### Q3. Roughly how many active customers?
- **~500** (rough estimate, taken "with a pinch of salt")

### Q4. Split between wholesale and retail?
- **Wholesalers**: Very few — roughly **~10 clients** (~2% of total)
- **Retail/locales**: The vast majority (~98%)

### Q7. Order channels ranked by frequency:
1. **WhatsApp** (most frequent) — clients send:
   - Text lists with product names (often approximate/informal names — need flexibility to interpret)
   - Screenshots of the product catalog
   - Photos of handwritten lists (e.g., "one carton of blueberry, two cartons of chocolate")
2. **In-person visits** (tied for second) — clients come to the warehouse/showroom:
   - They point out products, Johnny photographs each item and sends photo + quantity to a **group chat** (WhatsApp group with brother + employees)
   - Johnny then converts those photos + quantities into an **Excel quote** (quantity, product, unit price, total)
   - Quote sent to client → client approves → order proceeds
3. **Online orders** (tied for second) — via website or Instagram:
   - Website orders come through directly
   - Instagram inquiries: Santiago gets client's phone number → moves to WhatsApp → manages sale there
   - Both ultimately funnel through WhatsApp/Santiago
4. **Phone calls** (least frequent) — mostly for negotiating special payment terms, not for placing orders

### Q8. How many orders per day?
- **Average**: 3–5 orders per day
- **Maximum**: ~10 (rare, possibly never actually reached)
- No historical data tracked — this is an estimate

### Q8b. Order complexity & pricing pain point
- Orders can be large — example: one client with 2 retail locations sends 2 separate lists of ~150 products each
- **Pricing is not uniform** — varies per client based on:
  - **Credit terms**: Clients who take longer credit (e.g., 6 months) get charged higher prices to compensate for the financing risk
  - **Client's retail context**: Clients in shopping centers sell at higher margins, so brother charges more because they can absorb it
  - **Relationship/negotiation**: Different clients get different rates for the same product
- **The main time sink is NOT responding to messages — it's building the quote**:
  - Determining the right price per client per product
  - Interpreting informal/incorrect product names from clients
  - Clarifying ambiguities ("did you mean this product or that one?")
  - For a 50-item order, this takes a very long time
- **Key need**: A single pricing database where prices are pre-defined per client (or client tier), so quotes can be generated automatically without brother's involvement each time

### Q8c. Pricing system — current state
- **No centralized price list exists** per client or tier
- **Current strategy shift**: Brother is trying to simplify from many price points to just two tiers (one price for retail/locales, one for wholesalers) — but unsure if this is a good strategy and hasn't implemented it yet
- **How pricing works today**:
  - Johnny looks up the **client's order history** in Iconta (the accounting system)
  - He finds what price was charged to that specific client last time for each product
  - He copies those prices into the new quote Excel
  - There is no "product X costs Y" master list — it's always "what did we charge this client last time?"
- **This is unsustainable** with ~1200 SKUs and ~500 clients — brother acknowledges he needs to systematize pricing but hasn't had time to dedicate to it

### Pricing — Deep Dive (Critical Context)

#### Market pressure
- Market has become highly competitive, partly due to actors who undercut prices aggressively (some suspected of money laundering — they don't care about margins, just moving volume)
- These actors buy at wholesale (e.g., $9.50) and resell at near-cost (e.g., $10), destroying the value chain
- Brother was selling same product at $22 retail while competitors offer it at $13
- Result: lost clients who see the brother as "too expensive" compared to the undercut prices they get from rogue wholesalers
- Retail clients ("locales") get squeezed — if a wholesaler sells to them at near-cost, they won't buy from the brother at a higher price

#### Previous pricing structure (before market disruption)
- **3-tier volume pricing per product** for retail clients:
  - **Per-unit price** (less than half a display, e.g., 1–5 units)
  - **Half-display price** (e.g., 6–11 units)
  - **Full display price** (e.g., 12+ units, where display size varies by product)
- **Alternative: order-total-based pricing** for clients ordering many different SKUs in small quantities:
  - $0–$500 total order → unit price (same as <half display)
  - $501–$1000 total order → mid-tier price
  - $1000+ total order → best price (same as full display) — even if buying just 1 unit per SKU
  - Logic: rewarding large mixed orders the same as bulk single-product orders

#### Current state
- Previous pricing structure has collapsed under market pressure
- Brother is trying to simplify to just 2 prices: one for wholesalers, one for retail — but not sure this is the right approach
- Also lost pricing data when a computer was lost/broken
- Per-client pricing still happens ad hoc: if a client has been "touched" by a price-cutting wholesaler, brother must match or come close; untouched clients allow more margin
- Frequent negotiation — some clients push hard on price, get small discounts to keep the business
- **Every client ends up with slightly different pricing** — this is the core reason pricing isn't systematized

#### What's needed
- Define **minimum margins** from cost price to:
  - Wholesale selling price
  - Retail selling price
  - End-consumer selling price
- A pricing engine that can handle rules + exceptions while maintaining minimum profitability
- Flexibility to adjust per-client when market conditions demand it, but with guardrails

#### Pricing strategy direction (emerging)
- **Wholesale prices exist and are defined** — all wholesalers get the same (minimum) price. This data is available now.
- **Retail prices are the problem** — no systematic strategy yet, currently ad hoc per client
- **Key insight from brother**: Narrowing the gap between wholesale and retail prices would reduce the risk of being undercut by wholesalers who resell to retailers at near-wholesale prices
- Brother has been postponing this decision due to workload — keeps getting pushed aside by incoming orders
- **Possible pragmatic approach**: Set fixed retail prices and accept that some clients won't buy ("if I sell, I sell; if I don't, so be it") — brother sees this as the only viable solution but struggles with it because he needs the revenue
- **Competition**: Some competitors import directly (cutting out the brother entirely), adding further price pressure

#### Implication for development
- **Wholesale pricing data is available now** — can be used immediately
- **Retail pricing requires a strategic decision** by the brother before it can be systematized
- Development can proceed on other modules (bank reconciliation, invoicing, order intake) while pricing strategy is resolved
- The system could help the brother *make* the pricing decision: analyze cost data, margins, and suggest tier structures — then let him approve

### Q7b. Order approval & payment flow:
- Quote ("preventivo") is sent to client for approval
- **New/unknown clients**: Must pay before order is shipped
- **Known clients**: Credit terms negotiated, typically **30 days credit** (brother pushes for max 30 days)
- Payment terms discussed verbally or via WhatsApp

### Q6. Do you sell online?
- **Yes**, through multiple channels:
  - **Website** (Apta Imports): Functions as an e-commerce with product catalog and shopping cart. Client places order, but payment is not yet integrated into the site.
  - **Instagram → Website**: Social media drives traffic to the site
  - **Instagram → WhatsApp**: Some clients contact via Instagram, Santiago moves them to a dedicated WhatsApp for online sales, handles the transaction there (e.g., custom products like blunt wraps with custom text, cushions, etc.)
- **Payment**: Currently via bank transfer only. Client confirms order, gets a bank account number, transfers payment. Brother must manually confirm receipt.
- **Future plan**: Integrate a **payment gateway** (like credit card processing, similar to Amazon checkout) into the e-commerce site
- **Site status**: Not fully finished yet — cart works, but payment flow is manual. Santiago manages online sales end-to-end for now.

### Q5. How many different products (SKUs)?
- **~1200** (rough estimate, includes some inactive products that need to be cleaned up)

### Key Observation: Pricing Bottleneck
- **Brother is the single source of truth for all pricing** — Johnny asks him, Santiago asks him
- No centralized, accessible price list that others can use autonomously
- This is a clear automation opportunity

---

### 10. Architecture & Maintainability Concern
- Brother wants a **clear view of the full architecture** before building starts — not building block by block without a plan
- Concerned about building something that misses a critical aspect and becomes unusable
- Wants the system to be **correctable** — if we later discover a missed requirement, it should be possible to adjust without starting over
- Was reassured somewhat by the idea that Claude writes the code from prompts (making iteration easier), but still wants architectural clarity upfront

---

### Data the brother agreed to provide
- **Wholesale prices**: Can export from Iconta (available now)
- **End-consumer prices**: Can export from Iconta (available now)
- **Cost prices** (what he pays for products): Can export from Iconta, just needs to clean out inactive SKUs — relatively quick
- **Retail prices**: Needs to create **two tiers** manually (not yet systematized):
  - **Tier 1**: Lower price for price-sensitive / high-volume / long-credit retailers
  - **Tier 2**: Higher price for less price-sensitive retailers
  - This is more work — requires manually assigning a price per product per tier

---

## Transcript Coverage
- **Questionnaire sections covered**: Section 1 (Q1–Q6) fully, Section 2 partially (Q7–Q8, plus deep pricing discussion)
- **Stopped at**: Question 9 (WhatsApp order specifics)
- **Next session**: Continue from Q9 onward

*More sections will be added as additional transcript parts are processed.*

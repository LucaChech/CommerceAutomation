# General Product Requirements — Commerce Automation Suite

## Source
Extracted from `transcript_cleaned.md` (brother's business case), filtered for requirements that generalize across the commerce sector and beyond.

---

## Core Product Modules

### 1. Multi-Channel Order Intake
- Collect orders from multiple channels: WhatsApp, web, email, social media, in-person
- Normalize all orders into a unified internal format regardless of source
- Support varied input types: text lists, photos, screenshots, handwritten lists, informal product names
- Automatic acknowledgment and confirmation to the client
- Future: trigger courier/logistics pickup for completed orders

### 2. Automatic Quote/Estimate Generation
- Given an order and a client, instantly produce a priced quote using the pricing engine (module #3)
- Fuzzy matching of informal/approximate product names to the product catalog
- Quote ready for review or sent directly to client for approval
- Approved quotes feed into invoicing (module #5) and order fulfillment
- Eliminates manual quote-building as the primary operational bottleneck

### 3. Tiered Pricing Engine
- Support multiple price lists by client role (e.g., wholesale, retail, end consumer)
- Volume-based pricing tiers per product
- Order-total-based pricing tiers (e.g., orders over $X get better rates across all items)
- Per-client price overrides for negotiated rates
- Minimum margin guardrails: prevent selling below a configurable floor relative to cost
- Pricing strategy advisor: analyze cost data, margins, and market conditions to suggest tier structures

### 4. Payment Tracking & Installment Management
- Track agreed payment schedules: amount, frequency, start date, outstanding balance
- Automatic balance updates when payments are received
- Payment acknowledgment to the client with updated remaining balance
- Proactive payment reminders to both business owner and client
- Support for credit terms (e.g., net 30 days) and installment plans
- Essentially: automated accounts receivable with payment plan support

### 5. Invoice Generation
- Auto-generate invoices from approved quotes/orders
- Link invoices to orders, payments, and bank transactions for full traceability
- Pluggable compliance layer: support different local tax/invoicing regulations via configuration, not hardcoding
- Goal: eliminate manual invoicing as a dedicated task

### 6. Bank Reconciliation
- Automatically match bank transactions (incoming and outgoing) to invoices
- Full traceability: every bank movement linked to a specific invoice, client, or supplier
- Support for partial payments and installment matching
- Reporting for accounting/regulatory purposes
- Pluggable bank integration layer to support different banks and formats

### 7. Promotions Engine
- Automatic discounting: apply promotions to slow-moving products on sales channels
- Marketing campaign generation: propose and execute themed promotions (e.g., category discount weeks, seasonal calendars)
- Loyalty/membership programs: design incentive programs that benefit clients without eroding margins (e.g., repurchase coupons, spend thresholds)
- Autonomous operation: system thinks up promotions AND executes them, not just suggests
- Coordinate with Business Intelligence (module #8) for data-driven promotion targeting

### 8. Business Intelligence & Analytics
- Slow-moving inventory detection: identify products that aren't selling based on inventory/sales data
- Sales trend analysis: track performance by product, category, channel, and time period
- Margin analysis: monitor profitability across products, clients, and pricing tiers
- Demand forecasting: predict future sales patterns to inform purchasing and promotions
- Actionable insights: surface recommendations that feed into other modules (promotions, pricing, procurement)

### 9. Social Media Management
- Automated content creation and scheduling across channels: Instagram, email newsletters, Facebook, etc.
- Post product updates, promotions, new arrivals, seasonal content
- Coordinate with promotions engine (module #7): when a promotion is created, automatically push to social channels
- Maintain consistent brand voice and visual identity
- Analytics: track engagement, reach, and conversion

---

## Cross-Cutting Concerns

### Configurability
- All modules must be configurable per deployment — no hardcoded business logic specific to one client, sector, or geography
- Tax/compliance rules, pricing structures, channel integrations, and workflows should be parameterized

### Integration Architecture
- Modules should be independently deployable but composable
- Must integrate with existing accounting/ERP systems (not replace them) via pluggable adapters
- Support for data import/export (Excel, CSV, API)

### Multi-Channel Communication
- Unified communication layer across WhatsApp, email, web portal, social media
- System can respond on behalf of the business owner across channels
- Channel-agnostic: adding a new channel should not require rewriting business logic

---

## Notes
- Requirements derived from a real tobacco commerce business in Ecuador, but deliberately abstracted for general commerce applicability
- The generalization guardrail from `CLAUDE.md` applies: every design decision should be evaluated against diverse commerce verticals (clothing retail, food wholesale, electronics e-commerce, etc.)
- Sector-specific or geography-specific features (e.g., Ecuador SRI compliance) belong in the pluggable configuration layer, not in core modules

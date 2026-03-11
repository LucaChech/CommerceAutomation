# AI Consulting Business — Project Context

## Note on web searches
When asked to perform a web search NEVER default back to training knowledge because it is not up to date. If main agents or subagents do not have permission to do web searches please tell me so and abort. 

## Project Overview

This project is the foundation of a **freelance AI automation consultancy**. The goal is to develop a **suite of ready-made automation products**, each targeting a specific phase of the typical workflow in a commerce business. These products serve as both the core offering and a portfolio to kickstart the consultancy.

### Product Strategy

Rather than starting from scratch with each client, the approach is to build a **modular product line** — a set of standalone but composable automation tools that cover the key operational areas of a commerce business. Each product automates a well-defined workflow phase, can be sold independently, and can be combined for end-to-end coverage.

### Product Ideas

- **Order Management & Collection**: Automatically collect orders from multiple channels (WhatsApp, email, web, etc.), normalize them into a unified format, and send automatic replies/confirmations to customers.
- **Inventory & Stock Management**: Automate stock tracking, low-stock alerts, reorder triggers, and synchronization across sales channels.
- **Accounting & Invoicing**: Automate invoice generation, expense categorization, tax calculations, and integration with accounting software.
- **Customer Communication**: Automated responses, follow-ups, and status updates across channels — keeping customers informed without manual effort.
- **Supplier & Procurement**: Automate purchase order generation, supplier communication, price comparison, and delivery tracking.

### Target Market

- **Primary sector**: Commerce businesses (wholesale and retail)
- **Company size**: SMEs — large enough to have real operational pain, too small for a dedicated IT department
- **Geography**: Initially Veneto region, northern Italy, with potential to expand

---

## Development Status

### Current Phase: Product Development

The project has shifted from market research to **building the first products**. Prior research (see `background/`) confirmed the market opportunity; the focus is now on developing working automation tools.

### First Client: Brother's Tobacco Commerce Business (Quito, Ecuador)

Development is grounded in a **real business case** — the owner's brother runs a tobacco products commerce business in Quito, Ecuador. This provides direct access to a real business owner for first-hand requirements gathering, feedback, and testing.

**Why this matters**: Working with a live business avoids building in a vacuum. Real workflows, real pain points, real feedback.

### ⚠️ Generalization Guardrail

**Critical design principle**: The products must be built for the **commerce sector broadly**, not just for one tobacco shop in Quito. While the brother's business is the development testbed, every design decision should be evaluated against general commerce needs.

**Claude must actively flag** when a proposed solution appears to be:
- Too specific to tobacco products or Ecuadorian regulations
- Tailored to a single business's idiosyncratic workflow rather than common commerce patterns
- Hard to adapt for other commerce verticals, geographies, or business sizes

When in doubt, ask: *"Would this work for a clothing retailer in Verona? A wholesale food distributor? An online electronics shop?"* If the answer is no, the solution needs to be more generic or made configurable.

### Next Steps

- **Define and scope the first product** — select the most impactful workflow to automate (likely order management) and define its MVP
- **Build and iterate** — develop the first tool end-to-end, test against the brother's real workflow
- **Validate generality** — ensure the product works beyond the single test case
- **Package for deployment** — make the product easy to demo, configure, and deploy for clients
- **Expand the suite** — once the first product is validated, move on to the next workflow area

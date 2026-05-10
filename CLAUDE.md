# CLAUDE.md — Digital Retail Hub

**Project:** Digital Retail Hub  
**Owner:** Vasko Kacorovski  
**Created:** 2026-05-10 09:22 UTC  
**GitHub:** https://github.com/vaskockorovski/digital-retail-hub  
**Linear:** https://linear.app/vasko-automation/issue/VAS-799/digital-retail-hub  

---

## Quick Context

Centralized platform for unified e-commerce management across multiple channels (Shopify, Printful, Etsy). Single source of truth for inventory, orders, fulfillment, and analytics. Solve the fragmentation problem where data lives in separate systems.

**Problem:** Currently managing Void Optimised and Joinery Shopify stores manually. Data is fragmented. Need unified dashboard + API to sync inventory and orders across platforms.

---

## Goals

- [ ] Unified inventory dashboard (Shopify + Printful + Etsy)
- [ ] Order management across channels
- [ ] Fulfillment automation (Printful integration)
- [ ] Analytics dashboard (sales, margins, performance per channel)
- [ ] API for platform integrations
- [ ] Webhook handlers for real-time sync

---

## Tech Stack

**Frontend:** Next.js + Tailwind + Shadcn UI  
**Backend:** Supabase (Postgres) + Node.js API  
**Integrations:** Shopify API, Printful API, Etsy API, Stripe  
**Deployment:** Vercel  
**Database:** Supabase (PostgreSQL with RLS)  

---

## Phase 1: MVP (Weeks 1-4)

### 1.1: Architecture & Schema Design
- [ ] Database schema (products, variants, inventory, orders, channels)
- [ ] API design (REST endpoints for CRUD)
- [ ] Authentication (JWT + Supabase auth)
- [ ] Data flow diagram (webhook → sync → dashboard)

### 1.2: Shopify Integration
- [ ] OAuth flow for Shopify store connection
- [ ] Sync products, variants, inventory
- [ ] Sync orders and fulfillment status
- [ ] Webhook handlers (product updates, order created, fulfillment updated)

### 1.3: Printful Integration
- [ ] Printful API authentication
- [ ] Link Printful products to Shopify variants
- [ ] Order submission to Printful
- [ ] Fulfillment status sync (polling → webhook)

### 1.4: Unified Dashboard (Basic)
- [ ] Store overview (total inventory, pending orders)
- [ ] Product listing with inventory across channels
- [ ] Order queue (unfulfilled, pending)

### 1.5: Testing & Documentation
- [ ] API test suite (Shopify, Printful, Etsy endpoints)
- [ ] Integration tests (full order flow)
- [ ] API documentation (OpenAPI/Swagger)

---

## Phase 2: Analytics & Optimization (Weeks 5-8)

### 2.1: Analytics Dashboard
- [ ] Sales by channel (Shopify vs Etsy vs direct)
- [ ] Profitability analysis (cost per product, margin by channel)
- [ ] Fulfillment metrics (time to ship, error rate)
- [ ] Customer analytics (repeat rate, AOV)

### 2.2: Etsy Integration
- [ ] Etsy OAuth flow
- [ ] Sync products and inventory
- [ ] Order sync and fulfillment

### 2.3: Inventory Management
- [ ] Stock allocation rules (how to distribute across channels)
- [ ] Low stock alerts
- [ ] Auto-reorder workflow (Printful)

### 2.4: Automation
- [ ] Auto-tag orders (high-value, repeat customer, etc.)
- [ ] Auto-create Printful orders when Shopify order arrives
- [ ] Auto-update inventory across channels (near real-time)

---

## Phase 3: Advanced Features (Weeks 9-12)

### 3.1: Multi-Store Management
- [ ] Manage multiple Shopify stores (Void + Joinery + future stores)
- [ ] Per-store analytics
- [ ] Bulk operations (update pricing, inventory across stores)

### 3.2: Pricing & Margin Optimization
- [ ] Automated pricing rules (cost + margin %)
- [ ] Channel-specific pricing (Etsy vs Shopify)
- [ ] Promotion management

### 3.3: Fulfillment Automation
- [ ] Batch order submission to Printful
- [ ] Fallback fulfillment (if Printful out of stock, suggest alternative)
- [ ] Custom fulfillment (ship your own items)

### 3.4: Customer Portal (Optional)
- [ ] Order tracking (across channels, unified)
- [ ] Customer history
- [ ] Wishlist / pre-order workflow

---

## Success Criteria

**MVP (End of Phase 1):**
- [ ] Void Optimised inventory visible in dashboard
- [ ] New Shopify orders auto-sync and create Printful orders
- [ ] Inventory deduplication (single item visible once per variant)
- [ ] Zero manual data entry for order workflow

**Phase 2 (End of Phase 3):**
- [ ] 3+ channels managed (Shopify stores + Etsy)
- [ ] Profitability tracked per product and channel
- [ ] Auto-fulfillment working (Shopify → Printful in <5 min)
- [ ] Case study ready (revenue impact, time saved, margin improvement)

---

## Risks & Mitigations

| Risk | Mitigation |
|------|-----------|
| API rate limits (Shopify, Printful, Etsy) | Implement caching + queue jobs for batch operations |
| Inventory sync delays | Polling every 5 min + webhook handlers for real-time |
| Fulfillment errors | Validation checks before Printful submission + logging |
| Multi-store complexity | Start with 1 store (Void), add Joinery in Phase 2 |

---

## Success Measures

1. **Time saved:** <5 min from order to fulfillment (vs 15 min manual)
2. **Inventory accuracy:** 100% sync across platforms (no oversells)
3. **Revenue visibility:** Margin per product + channel (before: guesswork)
4. **Scaling:** Can add new store in <1 hour (vs 1 day manual setup)

---

## Next Steps

1. Confirm Shopify + Printful + Etsy API access
2. Design database schema (product, variant, inventory, order, channel models)
3. Start Phase 1.1 (architecture design)
4. Create GitHub project board

---

**Questions for Claude Code:**
- Should we use RLS or application-level authorization for multi-store setup?
- Webhook queue best practice: Bull, BullMQ, or Supabase realtime?
- Cache strategy for product inventory: Redis vs in-memory vs Supabase?

---

_Project brief created: 2026-05-10 09:22 UTC_

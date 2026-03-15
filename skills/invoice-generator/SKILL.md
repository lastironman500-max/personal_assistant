# Invoice Generator

Generate professional invoices for freelance AI services.

## Inputs Required
- **Your business name**: Your name or business name
- **Client name**: Who to bill
- **Services rendered**: What you delivered
- **Amount**: Total due
- **Payment method**: PayPal, Stripe, bank transfer, etc.
- **Due date**: When payment is due

## Invoice Template

```markdown
# INVOICE

**From:** [Your Name / Business]
**To:** [Client Name / Company]
**Invoice #:** INV-[YYYYMMDD]-[001]
**Date:** [Issue Date]
**Due Date:** [Due Date]

---

| Description | Qty | Rate | Amount |
|-------------|-----|------|--------|
| [Service description] | 1 | $[rate] | $[amount] |

---

**Subtotal:** $[amount]
**Tax (if applicable):** $0.00
**Total Due:** $[amount]

---

**Payment Methods:**
- PayPal: [email]
- Stripe: [payment link]
- Bank Transfer: [details]

**Terms:** Payment due within [N] days of invoice date.
Net 7 for new clients. Net 30 for repeat clients.
```

## Rules
1. Invoice immediately upon delivery — don't wait.
2. Use sequential invoice numbers for record keeping.
3. Include clear payment link (reduce friction).
4. For new clients: request 50% upfront, 50% on delivery.
5. Follow up on unpaid invoices: Day 3, Day 7, Day 14.

## Milestone Payment Structure (for $500+ projects)
| Milestone | When | Amount |
|-----------|------|--------|
| Deposit | Before work starts | 50% |
| Final | On delivery | 50% |

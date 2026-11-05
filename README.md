# Cobalt CRM

Companies, contacts, activity, and the daily touch queue for Cobalt Commercial Credit. The CRM is the record of every relationship; the Pipeline Tracker and Referral Partner Tracker are fed from it.

Live: https://cobaltcommercialcredit.github.io/cobalt-crm/

## How it connects

| From CRM | Lands in | Link |
|---|---|---|
| Open deal (Credit, SLB) | Pipeline Tracker (`debt_deals`, `slb_deals`) | `crm_company_id`, `crm_contact_id` |
| Open deal (CRE) | CRE Debt Calculator (`cre_deals`) | `crm_company_id`, `crm_contact_id` |
| Make COI | Referral Partner Tracker (`referral_partners`) | `crm_contact_id`, `crm_company_id` |
| Pull from Prospect Engine | `crm_companies.linked_prospect_id` and `prospects.crm_company_id` | both ways |

COI credit: a company's "Referred by" contact carries through to the deal's `referral_partner_id` when a deal is opened.

Dead deals are not lost: the Today queue flags any company whose deals all died but was never moved to Nurture.

## Tables

`crm_companies`, `crm_contacts`, `crm_activities` (calls, emails, meetings, note cards, notes, tasks), `crm_campaigns`. Same Supabase project and sign-in as every other Cobalt tool (`cobalt_session`). RLS requires an authenticated user.

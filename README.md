# Supply Chain RAG Chatbot

## Chatbot URL
https://cloud.flowiseai.com/chatbot/da7972bf-66a5-4263-a43a-567eae1ae012

## Github URL
https://github.com/scriptforge-ds/scm-assistant-bot


## Models Used

| Component  | Model                        | Provider        |
|------------|------------------------------|-----------------|
| LLM        | gemini-2.5-flash             | Google AI Studio|
| Embeddings | gemini-embedding-001         | Google AI Studio|


## Chunk Configurations

| Config | Chunk Size | Overlap | PDF Chunks | CSV Chunks |
|--------|------------|---------|------------|------------|
| A      | 500        | 50      | 35         | NA         |
| B      | 1000       | 200     | 18         | NA         |

**Selected:** Config B


## Q&A

**Q1: Which Tier-3 suppliers have an active disruption flag, and what response level applies per policy?**

> 
No Tier-3 suppliers with an active disruption flag were found.

However, according to policy, when a supplier has an Active Disruption flag, the response level depends on the supplier's risk level and the type of disruption:

Level 1 — Monitor: Applies to Low Risk suppliers with a disruption flag. Requires weekly status updates and a 15% adjustment to safety stock.
Level 2 — Manage: Applies to Medium Risk suppliers with a disruption flag. Involves bi-weekly escalation calls, a 30% adjustment to safety stock, and placing an alternate supplier on 48-hour readiness notice.
Level 3 — Activate: Applies to High Risk suppliers with any disruption flag, or any supplier with two simultaneous disruption flags. Triggers immediate escalation to the CPO, activation of an alternate supplier for a minimum of 40% of volume within 10 business days, a 50% adjustment to safety stock, and a full Root Cause Analysis (RCA) within 15 business days.
Certain disruption categories, such as export control restrictions, active labor strikes, regulatory enforcement actions, and port closure events exceeding 72 hours, automatically require a Level 3 response regardless of the supplier's risk level.


**Q2: Which suppliers qualify for the annual Volume Rebate Program and how many are there?**

>
I am unable to identify which suppliers qualify for the annual Volume Rebate Program or how many there are, as the available data does not contain the necessary information to assess suppliers against the full eligibility criteria (OTD at or above 93.0% for a full calendar year, Defect Rate below 0.5% for a full calendar year, and Sustainability Score at or above 85 for a full calendar year).

**Q3: Which region has the highest total PO value, and does it breach the concentration limit?**

> 
The region with the highest total PO value is APAC, with a total PO value of 1,050,000.

The policy states that "No single region (APAC, EMEA, LATAM, NA) may account for more than 45% of total annual procurement spend." However, I do not have information on the total annual procurement spend, so I cannot determine if APAC breaches the concentration limit.


**Q4: Which suppliers are on Supplier Watch List (SWL) status and what does it restrict?**

> 
There are no suppliers currently on the Supplier Watch List (SWL) status.

Suppliers are placed on SWL status if their Compliance Score falls below 60 at any audit. SWL status limits new Purchase Order (PO) issuance to 20% of the prior quarter's volume.


**Q5: Which product category has the highest average defect rate and does it exceed the Tier-2 limit?**

>
The product category with the highest average defect rate is Packaging Materials at 4.5%. This exceeds the Tier-2 maximum permissible defect rate of 2.50%.


## What I'd Improve

**1. Use a CSV agent instead of embedding the CSV**
Embedding 2000 rows and doing semantic search is not reliable for calculations like averages, totals, and rankings. A CSV agent runs actual queries on the data and always returns exact numbers.

**2. Try more chunk sizes**
Only tested two configurations due to API limits. More experiments would help find the best chunk size for this type of policy document.

**3. Use a stronger model**
The current model sometimes gives incomplete answers on complex multi-condition questions. A more capable model would handle these better.

**4. Structured output**
Add a fixed output format so answers always include the supplier name, metric value, policy threshold, and whether it was violated regardless of how the question is asked.
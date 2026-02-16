# GA4 E-commerce Funnel Audit
GA4 Funnel Exploration project with drop-off analysis, measurement audit, and UX recommendations.

## Project Overview
This project analyzes the e‑commerce conversion journey using Google Analytics 4 (GA4) Funnel Exploration.
The goal was to understand where users drop off in the purchase process, compare performance across devices, and identify potential measurement inconsistencies in the tracking setup.

The analysis is based on the GA4 Google Merch Shop demo property, using the last 28 days of data.
The funnel includes the key e‑commerce events:

- view_item  
- add_to_cart  
- begin_checkout  
- add_payment_info  
- purchase  

The project includes:

- Funnel setup documentation  
- Drop‑off analysis  
- Device‑level performance comparison  
- Measurement audit  
- UX and tracking recommendations  

## Funnel Setup
The funnel was built using GA4’s Funnel Exploration tool.
The goal was to analyze the full e‑commerce journey from product view to purchase.

### Funnel steps included:
1. **view_item** – Product detail page viewed  
2. **add_to_cart** – Item added to cart  
3. **begin_checkout** – Checkout process started  
4. **add_payment_info** – Payment information entered  
5. **purchase** – Transaction completed  

### Settings used:
- **Open funnel:** Enabled  
- **Breakdown:** Device category  
- **Date range:** Last 28 days  
- **Visualization:** Standard funnel  

### Screenshot of the funnel:
![Funnel Screenshot](screenshots/funnel.png)

## Drop-off Analysis
The funnel shows significant user drop-offs across the e-commerce journey.
The analysis below highlights where users abandon the process and what these patterns may indicate.

### 1. view_item → add_to_cart (72.8% drop-off)
Only 27.2% of users who view a product add it to their cart.

**Possible reasons:**
- Product pages may lack persuasive elements (reviews, clear pricing, shipping info)
- Weak or poorly placed CTA buttons
- Slow loading times on mobile
- Users browsing without purchase intent

**Device insights:**
- Desktop add-to-cart rate: 29.24%
- Mobile add-to-cart rate: 20.43%

Mobile users convert significantly worse, suggesting UX friction on smaller screens.

### 2. add_to_cart → begin_checkout (50.7% drop-off)
Half of the users who add an item to the cart do not start checkout.

**Possible reasons:**
- Unexpected shipping costs
- No guest checkout option
- Confusing or cluttered cart layout
- Lack of trust signals (security badges, return policy)

### 3. begin_checkout → add_payment_info (24.8% drop-off)
One in four users abandon during checkout initiation.

**Possible reasons:**
- Too many form fields
- Missing autofill support
- Poor mobile usability
- Payment method limitations

### 4. add_payment_info → purchase (36.7% drop-off)
A large portion of users who enter payment info do not complete the purchase.

**Possible reasons:**
- Payment errors or declined cards
- Lack of trust at the final step
- No confirmation of shipping cost until late
- Users comparing prices elsewhere

### Summary
The highest friction points occur at:
- **Product → Cart**
- **Payment Info → Purchase**

Mobile users consistently underperform compared to desktop, indicating a need for mobile-first UX improvements.

## Drop-off Analysis

The funnel shows significant user drop-offs across the e-commerce journey.  
The analysis below highlights where users abandon the process and what these patterns may indicate.

### 1. view_item → add_to_cart (72.8% drop-off)

Only 27.2% of users who view a product add it to their cart.

**Possible reasons:**
- Product pages may lack persuasive elements (reviews, clear pricing, shipping info)
- Weak or poorly placed CTA buttons
- Slow loading times on mobile
- Users browsing without purchase intent

**Device insights:**
- Desktop add-to-cart rate: 29.24%
- Mobile add-to-cart rate: 20.43%

Mobile users convert significantly worse, suggesting UX friction on smaller screens.

---

### 2. add_to_cart → begin_checkout (50.7% drop-off)

Half of the users who add an item to the cart do not start checkout.

**Possible reasons:**
- Unexpected shipping costs
- No guest checkout option
- Confusing or cluttered cart layout
- Lack of trust signals (security badges, return policy)

---

### 3. begin_checkout → add_payment_info (24.8% drop-off)

One in four users abandon during checkout initiation.

**Possible reasons:**
- Too many form fields
- Missing autofill support
- Poor mobile usability
- Payment method limitations

---

### 4. add_payment_info → purchase (36.7% drop-off)

A large portion of users who enter payment info do not complete the purchase.

**Possible reasons:**
- Payment errors or declined cards
- Lack of trust at the final step
- No confirmation of shipping cost until late
- Users comparing prices elsewhere

---

### Summary

The highest friction points occur at:
- **Product → Cart**
- **Payment Info → Purchase**

Mobile users consistently underperform compared to desktop, indicating a need for mobile-first UX improvements.

## Measurement Audit

The goal of the measurement audit is to verify whether all e‑commerce events fire correctly and consistently.  
A funnel is only reliable if the underlying tracking is accurate.

Below is the checklist used to validate the GA4 implementation.

### Event Coverage Checklist

| Event | Expected | Status |
|-------|----------|--------|
| view_item | Fires on product detail page | ✔️ Present |
| add_to_cart | Fires when user adds item to cart | ✔️ Present |
| begin_checkout | Fires when checkout starts | ✔️ Present |
| add_payment_info | Fires when payment info is entered | ✔️ Present |
| purchase | Fires on successful transaction | ✔️ Present |

All core e‑commerce events are firing, which allows the funnel to function correctly.

---

### Parameter Audit

Each event should include key parameters for accurate revenue reporting and attribution.

| Parameter | Why it matters | Expected | Status |
|-----------|----------------|----------|--------|
| item_id | Identifies product | Required | ✔️ Present |
| item_name | Product name | Required | ✔️ Present |
| currency | Needed for revenue | Required | ✔️ Present |
| value | Total value of event | Required | ✔️ Present |
| items[] array | Contains product details | Required | ✔️ Present |

The GA4 demo store includes all required parameters, making it suitable for analysis.

---

### Potential Measurement Risks

Even though the demo property is well‑implemented, real-world setups often face issues such as:

- Duplicate events firing twice  
- Missing value or currency parameters  
- purchase event firing without items[]  
- begin_checkout firing too early or too late  
- add_payment_info firing only on certain payment methods  
- Missing enhanced measurement events on mobile  

These are common problems that can distort funnel accuracy.

---

### Conclusion of Audit

The GA4 demo store provides a clean and reliable dataset.  
All required events and parameters are present, allowing for accurate funnel analysis and drop‑off evaluation.

## Recommendations

Based on the funnel performance and measurement audit, several improvements can enhance both user experience and data quality.

### UX Recommendations

1. **Improve mobile product page usability**
   - Mobile users show significantly lower add‑to‑cart rates.
   - Increase CTA button size, improve spacing, and reduce scroll depth.

2. **Show shipping costs earlier**
   - Unexpected fees are a major cause of cart abandonment.
   - Display estimated shipping on product and cart pages.

3. **Simplify checkout flow**
   - Reduce the number of form fields.
   - Enable autofill and guest checkout.
   - Add progress indicators to reduce uncertainty.

4. **Strengthen trust signals**
   - Add security badges, return policy highlights, and payment provider logos.
   - Reinforce credibility at the payment step.

5. **Optimize payment step**
   - Provide multiple payment methods.
   - Improve error handling and user feedback for failed transactions.

---

### Tracking Recommendations

1. **Validate event timing**
   - Ensure begin_checkout fires only when the user truly starts checkout.
   - Confirm add_payment_info fires consistently across all payment methods.

2. **Monitor duplicate events**
   - Check for double‑firing add_to_cart or purchase events.

3. **Ensure value and currency parameters are always present**
   - Missing parameters can distort revenue reporting.

4. **Track additional funnel micro‑steps**
   - Example: view_cart, select_shipping, payment_error.
   - These help identify more granular friction points.

5. **Implement enhanced measurement on mobile**
   - Scroll, click, and engagement metrics help diagnose mobile UX issues.

---

### Summary of Recommendations

Improving mobile UX, simplifying checkout, and strengthening trust signals will reduce drop‑offs.  
Ensuring consistent event tracking will make funnel data more reliable and actionable.

## Conclusion

This project demonstrates how GA4 Funnel Exploration can be used to analyze user behavior across the e‑commerce purchase journey.  
By identifying major drop‑off points, comparing device performance, and auditing event tracking quality, we gain a clear understanding of where users struggle and how the experience can be improved.

The analysis highlights:
- Significant friction between product view and cart
- Mobile users performing worse than desktop users
- A major drop‑off at the payment stage
- The importance of accurate event tracking for reliable insights

The recommendations provided offer both UX and technical improvements that can meaningfully increase conversion rates and data quality.  
This project reflects a complete end‑to‑end analytics workflow: from data exploration to actionable insights.




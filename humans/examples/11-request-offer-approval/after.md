[Up](../readme.md)

# After: Request, Assessment, Approval and Payment

The team first identifies the visible elements and then places them into known flow shapes.

## The assembly palette

The experience is assembled from:

- a **Presenter** for offered items and the request summary;
- **Players or renderers** for the selected offer, question set, Evidence item and Comment;
- **Actions** for select, save, add evidence, submit, return, recommend, approve, decline and cancel;
- **Action zones** for applicant actions, assessor actions, approver actions and finance hand-off;
- **States** such as draft, submitted, information requested, under assessment, recommended, approved, declined, sent for payment and settled;
- **Events** such as submitted, information requested, recommended, approved and payment acknowledged; and
- **Brokers** that connect the presentation and flow coordination to the Request, Evidence, decision and FMIS capabilities.

The page is a composition of these elements. It is not the architecture itself.

## Part A: Prepare and submit

The applicant follows a BREAST flow:

1. **Browse** available offers;
2. **Read** the offer requirements and questions;
3. **Edit** the request answers;
4. **Add** Evidence and supporting information;
5. **Submit** the completed request; and
6. **Transition** the request from draft to submitted.

The submitted request contains a versioned answer set and references to the Evidence available at submission. The applicant may no longer change submitted information unless the request is returned for more information or another explicit correction path is used.

Evidence and Comments are nested capabilities. They have their own visibility, classification, storage and audit rules, while the Request provides their context.

## Part B: Assess and decide

The service side follows a separate flow:

1. receive the submitted request;
2. check completeness and eligibility;
3. **Return for information** if a required answer or Evidence is missing;
4. assess the request and record findings;
5. **Recommend** approval or decline;
6. **Approve** or decline under the applicable authority; and
7. publish the decision and emit the next event.

Return for information is not an error in the applicant's form. It is a recognised state and a deliberate transition back to Part A. Recommendation is not approval. Keeping them separate makes authority, audit and separation of duties visible.

## Part C: Fulfil and pay

An approved request enters a separate fulfilment and payment flow:

1. create the approved fulfilment instruction;
2. send the required contract to the FMIS;
3. record acceptance, rejection or a communication failure;
4. retry or reconcile an uncertain hand-off; and
5. record the payment or fulfilment outcome.

The approval flow does not need to know every FMIS detail. A broker or integration capability owns the external contract and reconciliation behaviour.

## Reuse without forcing it

At the first level, this is simply a clear decomposition of one real journey. The team can build the Request, Evidence, decision and payment boundaries separately and test each hand-off.

At the second level, repeated request capabilities can share a coordinator for loading, questions, evidence, validation, state changes, permissions and common actions. Offer-specific rules remain in a small capability adapter.

At the advanced level, a Presenter can work with a read Player and a write Player. A Broker can connect those Players to the Request, Evidence, decision and FMIS capabilities. The common action zones, loading, errors, transitions and event handling can then be solved once for many request-like experiences.

A commercial service request may use the same broad shape: choose an offer, answer requirements, attach evidence, submit, assess, approve or decline, then fulfil and settle. The team should compare the contracts before reusing the flow. Similar screens are not enough by themselves.

## What changed

The first version treated one page as one journey. The improved version identifies a palette of reusable elements and separates three related flows. The business content remains specific. The engineering shape becomes recognisable, testable and reusable.

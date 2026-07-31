# Before: An Offer Request Becomes One Long Journey

A service offers a funded item. A person selects it, answers questions, uploads evidence and submits a request. Staff then check it, ask for more information, recommend a decision and send approved requests to a finance system.

The first implementation treats this as one large Request screen and one large service:

- offer selection, questions, evidence, comments and approval are all handled together;
- save and submit use the same command shape;
- returning a request for more information is a flag on the same record;
- approval is a button beside editing;
- payment hand-off is called directly from the approval handler;
- a second commercial request copies the whole journey and changes a few labels; and
- the team cannot easily see which parts are shared and which parts are specific to this offer.

The visible page may be understandable to its first users. The system is difficult to test and extend because preparation, assessment, decision and payment have become one tangled journey.

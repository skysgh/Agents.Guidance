# First Look at the Client Experience

A business screen can look like one large thing. It is usually made from smaller, familiar parts. Seeing those parts helps the team ask better questions before code spreads assumptions across the client and service systems.

You do not need to remember the technical names. First understand the jobs the parts perform. A visible experience commonly includes movement between steps, collection or page framing, one record or representation, questions and actions, state and feedback, and a connection to the service that does the authoritative work.

The words used in an experience may mean different things in different problem areas. This is called polysemy. The useful boundary begins with the [Domain](../../reference/glossary.md#domain), the [Capability](../../reference/glossary.md#capability) it enables and the functions within that capability; the client component and service boundary can then be discussed without letting one screen decide the whole meaning.

## The simple picture

```text
experience
  -> movement between steps
      -> collection or page framing
          -> one record or visual representation
              -> questions, actions and state changes
      -> connection to the service that does the authoritative work
```

In the more precise vocabulary, these parts may be called:

- **View:** the experience people recognise;
- **Coordinator:** moves between steps or surfaces;
- **Presenter:** frames a collection, page, tree or sequence;
- **Player:** operates one capability or record through the consumer experience;
- **Renderer:** turns data or a definition into visible UI;
- **Questions and Inputs:** information needed to proceed;
- **Actions:** things a person or system asks to happen;
- **States and State Changes:** where something is and how it moves;
- **Feedback and Evidence:** what happened and what must later be proved; and
- **Broker:** connects the experience to a service or external system.

The names are useful when the team needs precision. Understanding the jobs comes first.

## A small example

A request page may contain a Presenter showing the selected offer and summary, a Player for request answers, a collection of Evidence Players, an Action Zone for the applicant, a visible state such as draft or submitted, feedback explaining missing information and a Broker connecting the experience to the Request capability.

The page remains one experience for the user. The client palette helps the team see the different responsibilities inside it while the service capability retains its business rules, permissions, durable state and evidence.

## Continue when ready

- [Client UX Palette](./ux-palette.md) explains the elements and their relationships.
- [Common Flows](../../orientation/flows.md) shows recurring journey shapes such as BREAD/ST and BREAST.
- [Request and approval example](../../examples/11-request-offer-approval/before.md) shows a complete decomposition.
- [Client Implementation Vocabulary](./implementation-vocabulary.md) gives more precise terms and implementation correspondence.
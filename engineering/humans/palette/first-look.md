# The Palette: First Look

## Why this helps

A business screen can look like one large thing. It is usually made from smaller, familiar parts.

Seeing those parts helps the team ask better questions before code spreads assumptions across the system. It also helps people reuse work instead of solving the same problem in a slightly different way each time.

You do not need to remember the technical names. First understand the jobs the parts perform.

The words used in a screen may mean different things in different problem areas. This is called polysemy. First identify the Domain, then the Capability it enables, then the Functions within that capability. The [Guidance Glossary](../glossary.md) explains these ideas.

The same caution applies to words such as **Role** and **System**. A business role is not automatically a system authorisation role, and a digital system is only one part of the wider organisational and legal setting. Qualify the word before designing the boundary.

## The simple picture

```text
experience
  -> movement between steps
      -> collection or page framing
          -> one record or visual representation
              -> questions, actions and state changes
      -> connection to the service that does the work
```

In the more precise vocabulary, these parts are called:

- **View**: the experience people recognise;
- **Coordinator**: moves between steps or surfaces;
- **Presenter**: frames a collection, page, tree or sequence;
- **Player**: operates one capability or record;
- **Renderer**: turns data or a definition into visible UI;
- **Questions and Inputs**: information needed to proceed;
- **Actions**: things a person or system asks to happen;
- **States and State Changes**: where something is and how it moves;
- **Feedback and Evidence**: what happened and what must later be proved; and
- **Broker**: connects the experience to the service or external system.

The names are useful when the team needs precision. Understanding the jobs comes first.

## How to use the palette

Choose an operation or experience that already makes sense to you, such as preparing a Request, reviewing an approval or finding a record in a list. Look at it as a person would first. Then notice what moves the person between steps, what frames a collection or page, what shows one record, what actions are available, what questions or evidence are needed, which states the capability can occupy, what feedback explains the result and which service or external system performs the work.

You are not being asked to redesign the whole system. You are learning to see the pieces that are already present. Write down what you notice in ordinary language. A new technical abstraction is not required for every observation; the value is in recognising the shape before deciding whether any part should be shared.

## A small example

A request page may contain:

- a Presenter showing the selected offer and the request summary;
- a Player for the request answers;
- a Player for each Evidence item;
- an Action Zone for the applicant;
- a State such as draft or submitted;
- Feedback explaining missing information; and
- a Broker connecting the page to the Request service.

The page is still one experience for the user. The palette helps the team see the different responsibilities inside it.

## What this gives the team

The team can now discuss the experience without arguing first about class names or frameworks. Business people can explain the meaning of the questions and states. Developers can check whether the boundaries can be implemented. Testers can check actions and transitions. Operations can identify external dependencies and recovery needs.

That shared picture is the first achievement. The detailed terms and reusable implementation patterns can come later.

## Continue when ready

- [Palette Elements](./elements.md) explains the job of each part.
- [Palette Relationships](./relationships.md) explains how the parts connect.
- [Common Flows](../flows.md) shows recurring flow shapes such as BREAD/ST and BREAST.
- [Request and approval example](../examples/11-request-offer-approval/before.md) shows a complete decomposition.
- [Palette and Presenter/Player/Coordinator terms](./technical-terms.md) explains the frontend vocabulary.

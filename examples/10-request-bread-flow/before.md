# Before: A Request Screen Becomes a Large Special Case

A team receives a request to build a Request page. The page has fields, an attachment area, comments, buttons for submit and approve, and a history panel.

The team builds the page from top to bottom. The controller receives all button calls. The service loads the request, evidence and comments together, decides which buttons to show, saves changes, uploads files, sends notifications and changes state.

The design grows around the screen:

- adding Evidence requires another branch in the Request service;
- Comments use a different set of rules hidden inside the page code;
- submit and approve are treated as ordinary updates;
- one button works from the page but not from another client;
- the next Request-like feature copies much of the same code; and
- the team cannot easily say which parts are reusable and which parts are unique to this Request.

The screen may work. The system has no recognised journey shape, so every new capability starts as a new special case.

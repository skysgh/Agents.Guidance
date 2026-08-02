# Before: A Working API Behind a Failing SPA

The service API works in integration tests. A browser SPA can load a request, display its fields and send a submission. The team calls the feature complete because the server returns a successful response and the main demonstration reaches the final page.

In real use, the client has become a second and mostly invisible system:

- one large page owns navigation, input, output, service calls, permissions and business state;
- the client stores access tokens in browser-accessible storage so requests are easy to make;
- a successful HTTP response is displayed as "submitted" before the service outcome is understood;
- a slow or interrupted request loses entered information and gives no recoverable state;
- keyboard users cannot reach one of the action zones, and validation messages are not connected to their fields;
- the page combines applicant, assessor and approver actions because they use the same request object; and
- browser tests cover the happy path but do not prove the client-service contract, CSRF behaviour, stale assets or recovery after a failed hand-off.

The service may be sound in isolation. The delivered consumer experience is not. The client has taken on responsibilities without naming its system boundary, its component contracts or the evidence needed to trust it.
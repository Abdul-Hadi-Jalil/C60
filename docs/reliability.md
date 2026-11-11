# Reliability model

- A run ledger records jobs, attempts, landed objects, checks, and completion.
- Retries use delayed queue messages and source-specific ceilings.
- Point-in-time sources stop retrying across day boundaries.
- Asynchronous report providers distinguish pending work from failed work.
- Raw objects are create-only. Identical retries are accepted; conflicting content is rejected.
- Operational rules alert on missing daily captures, exhausted retries, failed checks, and unexpected runtime errors.

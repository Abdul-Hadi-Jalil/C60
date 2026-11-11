# Security model

- Runtime services authenticate with managed identity.
- CI/CD uses workload identity federation rather than client secrets.
- Source credentials remain in Key Vault.
- The warehouse uses private networking and controlled identity-based access.
- Storage shared keys are disabled where supported.
- Public documentation excludes account numbers, infrastructure names, production schedules, business data, and secret identifiers.

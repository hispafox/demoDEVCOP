# Templates

## Commit message template

Subject:

`docs: summarize real outcome`

Body:

- what was delivered
- why the change was needed
- docs or code affected
- issue references

Example:

`docs: define REST strategy and API contract`

- document the technical decision for serving the MVP REST API in Fortran
- add the initial endpoint contract for processes and states
- update kickoff docs to reflect resolved work
- refs: #8, #9

## Issue closure comment template

Use this structure when closing an issue:

- state that the issue is completed
- list delivered outputs
- point to the repo files that carry the evidence
- state that the acceptance criteria are covered

Example:

This issue is completed and documented in commit `<sha>`.

Delivered:
- technical decision for the MVP
- build tool selection
- initial testing approach

Evidence in repo:
- `docs/...`
- `README.md`

The acceptance criteria are covered by the published documentation.

## Next issue handoff comment template

Use this structure on the next issue:

- list already resolved dependencies
- state the next implementation goal
- point to the documents that define the starting constraints

Example:

Work already consolidated:
- strategy documented and closed
- API contract documented and closed

Next block:
- create the Fortran skeleton with build and tests

Starting references:
- `docs/estrategia-tecnica-rest-fortran.md`
- `docs/contrato-endpoint-procesos-estados.md`

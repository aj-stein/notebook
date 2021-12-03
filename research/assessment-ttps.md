# Techniques, Tactics, and Procedures for Assessment

## What tactics do we have for assessment?

### NIST Standards

- Risk Management Framework 800-53A

## What techniques and procedures do we use? Do 
## What tools do we use for assessment?

### Manual

### Automated

- SCAP tools (under general standards 1.2 and 1.3) [validated under NIST SVP](https://csrc.nist.gov/projects/scap-validation-program/validated-products-and-modules)
- Community and industry tools for security testing:
    - Ansible
    - Chef
    - InSpec
    - Puppet

## How do we communicate assessment intent and results?
## Open Questions

- Is the subject, action, and object tuple simple enough to describe the whole of assessment models (especially automated ones)?
- Do we need pre-determined properties of an assessment subject (custom app, container, server, cloud infra) before we assess them?
- Do we need to pre-determine necessary (and mandatory in OSCAL) action details for a rule or can we generalize them?
# Techniques, Tactics, and Procedures for Assessment

## What do we mean by assessment?

## What tactics do we have for assessment?

### NIST Standards

#### Risk Management Framework and SP 800-53A

Does 800-53A mean the same thing when we say assessment framework?

<details>
<summary>References from 800-53A Rev. 5 DRAFT re the what and how of assessment</summary>

> The assessment process is an information-gathering activity of the as-implemented state of
the system or common controls, not a security- or privacy-producing activity. Organizations
determine the most cost-effective implementation of the assessment process by applying the
results of risk assessments, considering the maturity and quality level of the organization’s risk
management processes, and taking advantage of the flexibility in the concepts described in
this publication.

> Assessment results can be obtained from many activities that occur routinely during the system development life
cycle. For example, assessment results are produced during the testing and evaluation of new system components
during system upgrades or system integration activities. Organizations can take advantage of previous assessment
results whenever possible, to reduce the overall cost of assessments and to make the assessment process more
efficient.

> If a system component product is identified as providing support for the implementation of a
particular control in [SP 800-53], then evidence produced during the product testing,
evaluation, and validation processes (e.g., security or privacy specifications, analyses and test
results, validation reports, and validation certificates)12 is used to the extent that it is
applicable.

</details>

## What techniques and procedures do we use? Do 
## What tools do we use for assessment?

### Manual

### Semi-Automated (Computer-Assisted)

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
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

> Assessment results can be obtained from many activities that occur routinely during the system development lifecycle. For example, assessment results are produced during the testing and evaluation of new system components during system upgrades or system integration activities. Organizations can take advantage of previous assessment results whenever possible, to reduce the overall cost of assessments and to make the assessment process more efficient.

> If a system component product is identified as providing support for the implementation of a particular control in [SP 800-53], then evidence produced during the product testing, evaluation, and validation processes (e.g., security or privacy specifications, analyses and test results, validation reports, and validation certificates)12 is used to the extent that it is applicable.

> Organizations carefully consider the potential impacts of employing the assessment procedures defined in this publication when assessing the security and privacy controls in operational systems.

> Product assessments (also known as product testing, evaluation, and validation) are typically conducted by independent, third-party testing organizations. Assessments examine the security and privacy functions of products and established configuration settings. Assessments can be conducted to demonstrate compliance with industry, national, or international information security and privacy standards and developer/vendor claims.

> Establishing an appropriate set of expectations before, during, and after an assessment is paramount to achieving an acceptable
outcome

> Organizations consider both the technical expertise and level of independence required in selecting security and privacy control assessors.28 Organizations ensure that assessors possess the required skills and technical expertise to successfully carry out assessments of system specific, hybrid, and common controls.

</details>


#### NISTIR 8011-1

<details>
<summary>References from 8011-1 re the what and how of assessment</summary>

> While the defect check assesses the individual controls or control items that work together to achieve a purpose, at the same time the defect check also tests the overall effectiveness of the controls working together as a sub-capability. In NISTIR 8011, defect checks are designed so that there is one defect check for each defined sub-capability.

> The difference in the level of focus—between defect checks and determination statements—has a significant impact on how a defect, once discovered, is interpreted. The difference relates to the sensitivity and specificity of the result.

> A sensitive test is one which finds all of the cases where a defect occurs; that is, it has a low false negative rate.

> A specific test is one which does not report a defect when one is not present; that is, it has a low false positive rate.

> Because defect checks measure the result to be achieved by a set of controls, defect checks can be very specific, at the purpose level of abstraction, about whether that result was achieved. However, failure to achieve the result does not imply that ALL the controls or control items 
supporting that capability or sub-capability failed. Thus, while the defect check is specific at the purpose or sub-purpose level of abstraction, it is not specific at the control or control item level 
of abstraction. 

> Completeness means the extent to which the security-related information includes assessment of all relevant defects on all assessment objects (within a defined scope such as a capability). Relevant defects are defects that produce significant risk, e.g., the top two orders of magnitude. Incomplete metrics tend to bias the results by underestimating total risk.

> Timeliness means the extent to which the security-related information has been refreshed within the last X hours or days (as determined/required by the organization. Data must be collected (and defects mitigated) faster than the attacker(s) can act, in order to be able to stay ahead of their ability to compromise a system.

> For the agency dashboard to generate effective to-do lists for responding to defects, the dashboard requires the functionality to identify the specific operational role (person or group) responsible for responding to each defect (maintained as part of the desired state specification).

</details>

#### 800-115 Technical Guide to Information Security Testing and Assessment

<details>
<summary>800-115 views on different kinds of assessment</summary>
An information security assessment is the process of determining how effectively an entity being assessed (e.g., host, system, network, procedure, person—known as the assessment object) meets specific security objectives. Three types of assessment methods can be used to accomplish this—testing, examination, and interviewing. Testing is the process of exercising one or more assessment objects under specified conditions to compare actual and expected behaviors. Examination is the process of checking, inspecting, reviewing, observing, studying, or analyzing one or more assessment objects to facilitate understanding, achieve clarification, or obtain evidence. Interviewing is the process of conducting discussions with individuals or groups within an organization to facilitate understanding, achieve clarification, or identify the location of evidence. Assessment results are used to support the determination of security control effectiveness over time.
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
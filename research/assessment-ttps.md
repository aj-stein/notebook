# Techniques, Tactics, and Procedures for Assessment

## What do we mean by assessment?

When people discuss the notional kinds of assessment, they overload the word. Within NIST, and more specifically how the Risk Management Framework series frames these concepts, there are two loosely categorized types of this activity.

1. Control Assessment (the RMF Assess Step activity): the macro-level process of reviewing top-down how a system is designed and implemented to meet control objectives through capabilities. This activity is high-level, where abstracted requirements (having policies, procedures, standards, and baselines for use of validated cryptography in system design and implentation) define objectives that can be applied to a variety of heterogenous designs and implemented systems (a 25 year batch application on a mainframe using FIPS-140-2 at the operating system and middleware level and the batch application leverages that; a Function-as-a-Service application with managed infrastructure in a modern IaaS/PaaS solution in a public cloud environment with the provider's hardware, operating system, virtualization platform, virtualized OS, and HTTPS API endpoints using FIPS-140-2 validated solutions)

1. Security testing and examination (many colloquially call this assessment and self-assesment, depending on who performs it): this is a more generalized view of a collection of tactical and operational acts focused on a system or its sub-systems. These are tangible checks for the state and state changes of micro-level properties of a system. The self-assessment and assessment acts support Control Assessments and the RMF Assess Step activity.

Discussion of assessment is complicated because, in the security industry primarily in the US public sector, both are described interchangeably and NIST RMF practicioners see the two on a continuum, but are distinctly different. They should be discussed separately.

### Assessment and Control Assessment (NIST RMF)

## What tactics do we have for assessment?

### NIST Standards

#### Risk Management Framework and SP 800-53A

##### 800-37r2

<details>
<summary>Use of Automation in the Execution of the RMF</summary>
Organizations should maximize the use of automation, wherever possible, to increase the speed, effectiveness, and efficiency of executing the steps in the Risk Management Framework (RMF). Automation is particularly useful in the assessment and continuous monitoring of controls, the preparation of authorization packages for timely decision-making, and the implementation of ongoing authorization approaches—together facilitating a real-time or near real-time risk-based decision-making process for senior leaders. Organizations have significant flexibility in deciding when, where, and how to use automation or automated support tools for their security and privacy programs. In some situations, automated assessments and monitoring of controls may not be possible or feasible.
</details>

<details>
<summary>Is a RMF Assessment temporal or can it be reused? (RMF 800-37 Assessment Step FAQ)</summary>
Can results from a previous control assessment be leveraged for (re-)authorization purposes? It may be possible to leverage recent control assessment results provided that the assessment was conducted according to
organizationally accepted assessment methodologies and depending on what was assessed and how much time elapsed since the
previous assessment. The security and privacy assessment plans play an important role in validating the recent assessment results. Note, however, that a control assessment is a snapshot in time, meaning that the security and privacy posture captured by the assessment reflects the posture at the time the assessment was performed. For additional guidance on the re-use of assessment results, see NIST SP 800-53A, Revision 4, Assessing Security and Privacy Controls in Federal Information Systems and Organization.
</details>

<details>
<summary>What is the outcome of a security and privacy control assessment?<summary>Is a RMF Assessment temporal or can it be reused? (RMF 800-37 Assessment Step FAQ)</summary>
What is the outcome of a security and privacy control assessment?
Security and privacy control assessments verify that selected controls are implemented correctly, operating as expected, and recorded appropriately (e.g., in security and privacy plans). The deficiencies in the implementation of security and privacy controls should be prioritized by the potential risks they convey to the system, components, and organization.
</details>

<details>
<summary>What is control assessment? (800-37 Assessment Step FAQ)</summary>
Why assess controls?
There are two primary motivations for assessing security and privacy controls: 1) to ensure that the security and privacy controls for managing risk are in place and producing the desired outcomes and 2) to provide the authorizing official with the information needed to make an authorization decision. Control assessment verifies that the safeguards are in place and working as planned, providing system management and Authorizing Officials with an overall security and privacy posture of the system. Control assessments may be conducted as controls are implemented in early stages of the system development in order to identify issues with controls early in the development process.
</details>

<details>
<summary>Assessor Criteria (800-37 Assessment Step FAQ)</details>
Who assesses the controls?
The assessment of security and privacy controls is conducted by assessors who are not only familiar with the Risk Management Framework and the controls in the NIST SP 800-53 [SP 800-53r5] control catalog but are also proficient in conducting control effectiveness assessments per NIST SP 800-53A [SP 800-53A] or equivalent. Preferably, the assessor should understand (or be capable of understanding) the system to be assessed, including its business/mission and operating environment, among other items. It may be necessary for assessors to possess specialized skills or knowledge to help ensure that assessment results are reflective of the actual current system security and privacy posture (e.g., if the system includes database services, the assessor should be knowledgeable about the particular database in use). Controls implemented to achieve both security and privacy objectives may require a degree of collaboration between security and privacy control assessors. An independent, third-party assessor is not required to assess systems categorized as low impact but is required to assess moderate and high impact systems to maintain impartiality. In accordance with OMB Circular A-130 [OMB A130], the senior agency official for privacy serves as the control assessor for the privacy controls and is responsible for conducting an initial assessment of the privacy controls prior to system operation and for assessing the controls periodically thereafter at a frequency sufficient to ensure compliance with privacy requirements and to manage privacy risks. The senior agency official for privacy can delegate the assessment functions, consistent with applicable policies. An independent evaluation of privacy controls is not required. However, an organization may choose to employ independent privacy assessments at the organization’s discretion.

How are assessors selected?
Assessors are selected for their technical expertise related to the type of system or component they are assessing as well as for their experience in all steps of the Risk Management Framework, including the assessment and authorization steps and the tasks that support them. 

Why is assessor independence important?
Assessors need to be free of any undue influence from officials associated with the systems, components, and organization whose controls are being assessed. Assessors need to make impartial decisions on security and privacy assessment results and provide the authorizing official with unbiased information so that informed risk-based decisions concerning the system and the organization can be made. In accordance with OMB Circular A-130 [OMB A130], an independent evaluation of the privacy program and practices is not required. However, an organization may choose to employ independent privacy assessments at its discretion. For more information, see NIST SP 800-53, Revision 5, CA-2(1) CONTROL ASSESSMENTS | INDEPENDENT ASSESSORS [SP 800-53r5], and NIST SP 800-53B [SP 800-53B]. 
</details>

<details>
<summary>Re the value of self-assesment for RMF Control Assessment (800-37 Assessment Step FAQ)</summary>
Organizations can conduct self-assessments with two caveats. First, while internal assessors can be employed to conduct self-assessments, assessors should not conduct assessments under the management control of their supervisors. While it may not be considered a conflict of interest, undue influence by supervisors may create scenarios in which deficiency information may be affected. Second, self-assessments can be used to assess low impact systems, while independent assessors should be employed for moderate and high impact systems. Even though self-assessments may be conducted for low impact systems, the assessor’s technical expertise and required skills should be at the same level as the assessment for moderate and high impact systems. In accordance with OMB Circular A-130 [OMB A130], an independent assessment of privacy controls is not required. For more information, see NIST SP 800-53, Revision 5, CA-2(1) CONTROL ASSESSMENTS | INDEPENDENT ASSESSORS [SP 800-53r5], and NIST SP 800-53B
[SP 800-53B].
</details>

<details>
<summary>Using self-assessment in the Develop Phase of the SDLC (800-37 Assessment Step FAQ)</summary>
Can controls be applied and assessed during the development process?
Yes, identifying security and privacy requirements, selecting and implementing controls, and assessing implemented controls for effectiveness during the development phase of the system development life cycle (SDLC) is an efficient and effective process for reducing risk to the system, component, and the organization. Controls should be implemented during the development phase of the SDLC to verify that they meet requirements and produce expected outcomes. Conducting control assessments during the development phase of the SDLC provides efficiency as security and privacy requirements are identified and recorded and corresponding controls are identified, implemented, and assessed, thereby reducing risks to the system, component, and organization. Common controls identified prior to system development can also be incorporated into the SDLC.

Can the results of control assessments conducted during the system development life cycle be
used?
Yes, the results of security and privacy control assessments conducted during the system development life cycle (SDLC) can be used for the authorization package. If assessments conducted during the SDLC identify any deficiencies, these can be captured in the security and privacy plans or be mitigated prior to the assessment. If there are no identified deficiencies from assessments conducted during the SDLC, then these security and privacy controls may not need to be re-assessed. 
<details>

<details>
<summary>Organizations support system control assessments through scaling enterprise-wide solutions and/or automation (800-37 Assessment Step FAQ)</summary>
 How can organizations support system control assessments?
Organizations can support system control assessments through the provision of enterprise solutions that can automate some of the tasks associated with not only security and privacy control assessments but with risk assessment (e.g., vulnerability assessments). Organization-wide security and privacy solutions may also include governance, risk management, and compliance applications that support assessment and authorization activities (e.g., plan of action and milestone tracking, configuration management tools). In addition to enterprise solutions and enterprise security services, organizations may provide the workforce for supporting control assessments, including independent control assessment teams.
</details>

##### 800-53A

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

<details>
<summary>Goals of technical security assessment and examination</summary>
To accomplish technical security assessments and ensure that technical security testing and examinations provide maximum value, NIST recommends that organizations:
- Establish an information security assessment policy. This identifies the organization’s requirements for executing assessments, and provides accountability for the appropriate individuals to ensure assessments are conducted in accordance with these requirements. Topics that an assessment policy should address include the organizational requirements with which assessments must comply, roles and responsibilities, adherence to an established assessment methodology, assessment frequency, and documentation requirements.
- Implement a repeatable and documented assessment methodology. This provides consistency and structure to assessments, expedites the transition of new assessment staff, and addresses resource constraints associated with assessments. Using such a methodology enables organizations to maximize the value of assessments while minimizing possible risks introduced by certain technical assessment techniques. These risks can range from not gathering sufficient information on the organization’s security posture for fear of impacting system functionality to affecting the system or network availability by executing techniques without the proper safeguards in place. Processes that minimize risk caused by certain assessment techniques include using skilled assessors, developing comprehensive assessment plans, logging assessor activities, performing testing off-hours, and conducting tests on duplicates of production systems (e.g., development systems). Organizations need to determine the level of risk they are willing to accept for each assessment, and tailor their approaches accordingly.
- Determine the objectives of each security assessment, and tailor the approach accordingly. Security assessments have specific objectives, acceptable levels of risk, and available resources. Because no individual technique provides a comprehensive picture of an organization’s security when executed alone, organizations should use a combination of techniques. This also helps organizations to limit risk and resource usage.
- Analyze findings, and develop risk mitigation techniques to address weaknesses. To ensure that security assessments provide their ultimate value, organizations should conduct root cause analysis upon completion of an assessment to enable the translation of findings into actionable mitigation techniques. These results may indicate that organizations should address not only technical weaknesses, but weaknesses in organizational processes and procedures as well.
</details>

<details>
<summary>Different assessment technqiues and relationship to NIST 800-53, OSTMM, other methodologies</summary>
Several accepted methodologies exist for conducting different types of information security assessments. References to several of these methodologies are found in Appendix E.2 For example, NIST has created a methodology—documented in Special Publication (SP) 800-53A, Guide for Assessing the Security Controls in Federal Information Systems—which offers suggestions for assessing the effectiveness of the security controls outlined in NIST SP 800-53.3 Another widely used assessment methodology is the Open Source Security Testing Methodology Manual (OSSTMM).4 Because there are numerous reasons to conduct assessments, an organization may want to use multiple methodologies. This publication offers recommendations for technical testing and examination techniques that can be used for many assessment methodologies and leveraged for many assessment purposes.
</details>

<details>
<summary></summary>
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
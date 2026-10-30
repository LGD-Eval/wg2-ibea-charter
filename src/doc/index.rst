.. raw:: latex

   \pagestyle{plain}
   \thispagestyle{plain}

.. _wg-charter:

FG-TIDA WG2: Identity, Behaviour and Enforcement for AI Agents (IBEA)
=====================================================================


Charter Information
-------------------

.. list-table::
   :header-rows: 0
   :widths: 30 70

   * - **Charter version**
     - 0.31

   * - **Date**
     - 2026-10-30

   * - **Status**
     - Draft (provisional working group, subject to approval at the first FG-TIDA meeting)


1. Group Information
--------------------

..
   MANDATORY

.. list-table::
   :header-rows: 1
   :widths: 38 62

   * - Field
     - Content

   * - Working group name and acronym
     - WG2: Identity, Behaviour and Enforcement for AI Agents (IBEA); name to be confirmed by the co-chairs

   * - FG-TIDA theme(s) covered
     - FG-TIDA/themes#4 and FG-TIDA/themes#6, joined in FG-TIDA/themes#36, with any further themes grouped into this working group by the FG-TIDA management

   * - Chair(s) / co-chairs
     - Artur Hecker (Huawei Technologies); Cyril Gorlla (CTGT). Provisional, subject to approval at the first FG-TIDA meeting

   * - Editor(s) of the main deliverables
     - Cyril Gorlla (CTGT), deliverables 2 and 4; other editors to be agreed by the working group

   * - Mailing list
     - Moderated WG2 list, to be created by the FG-TIDA Secretariat

   * - Repository and issue tracker
     - https://github.com/fg-tida-wg2 (charter: wg2-ibea-charter)

   * - Charter status and version
     - Draft, version 0.3


2. Background and Problem Statement
-----------------------------------

..
   MANDATORY

A verified identity and a valid authorization say little about what an AI agent will do on a given task. At the same time, the non-deterministic, creative nature of AI agents is the characteristic trait that distinguishes them from usual software. Four problems follow:

1. **For AI Agents, identity does not determine behaviour.** An AI agent that passes every identity and authorization check can still take an action outside the authority it was granted.
2. **Agents morph.** For the AI agents, a re-run is generally not the same as the run: the very same agent might give a different response to the same repeated request, even if its model, used tools and composition do not change. If major components or agent configuration change (e.g., used model, guard rails, etc), then such changed response is well documented and can be expected (e.g., varying accuracy and precision for various models; various configurations might consider or ignore exchange history, etc). In general, an identity issued at one point says less about the agent that acts later.
..
   [AH] Comment: it seems to be that 1 and 2 is semanticallythe same. However, we do miss a point on enforcement. We have a point on revocation and audit/check afterwards as 3. and 4. below, but we do not have anything on the actual enforcement or on the expression of it, correct?

3. **Revocation does not reliably stop conduct.** Revoking an identity takes effect only where a relying party checks it again before the next action. Besides, revoking rights from an agent might limit its operational freedom to an extent, where its sheer presence might be questioned: one designs a ICT system with agents because of "known unknowns". Trying to push everything within the known action space contradicts the departing point of known unknowns in the system.
4. **Determinations are not portable.** Where an action can be checked at all, the result is usually an internal log entry that another party can neither recompute nor rely on.

Existing work proposes agent identity (ITU-T X.1285, X.402, IETF WIMSE, IETF AgentProto, W3C Agentic Web Charter, Poppy/PACT), what it may access in general (XACML and attribute-based access control, PACT JWT) and what platform it runs on (IETF RATS, TC, Secure Enclaves). None of this solves the problem with morphing AI agents vs. a security policy expression presented above. Besides, none of the works above determines, at the moment a specific action is taken, whether that action conforms to the authority it was taken under, in a form a third party can check. The working group addresses the gap with expressing and enforcing a security policy where objects and subjects could be AI agents.
..
   [AH] Comment: the original text saying that the gap is that the third party cannot check sounds too much like audit or remote attestation terrain. The original scope of this WG was larger and different from it. Whether a 3rd party can check it is actually secondary to us (and primary to WG1). We are interested in how policy enforcement can be done with agents. I added a phrase before and changed the phrase with the gap, but I still think it should be reviewed. 

Its central object is bounded: one action, checked when it is taken against a pinned reference, producing a verdict that a relying party can recompute.
..
   [AH] Comment: not sure about this single target either.


3. Goals
--------

..
   MANDATORY

* The working group will describe the problem: terminology, environment, threat cases and a requirements set against which every solution path is assessed.

* The working group will specify requirements for the action-time verdict: its vocabulary and semantics, adjudication when obligations collide, the attested absence of evaluation, and appraisal of a carried verdict by a relying party. It will specify requirements, not encodings or protocols.

..
   [AH] Comment: Action-Time verdict is too narrow for me. The follow up text potentially too broad. What we need is: how do we enforce a classically expressed security policy with agents as subjects/objects OR how do we write the security policy such that it can be enforced? Am I reading it wrong?

* The working group will describe and compare solution paths against the shared requirements, starting with identity based on (unchangeable) agent design properties and continuing to a security policy expressed as intent independent of the subjects/objects involved but concentrating on the wanted and unwanted outcomes instead.

* The working group will maintain shared evaluation fixtures so that paths can be compared on the same cases.

* The working group will consider previous efforts and state of the art such as, e.g., ITU-T X.1285, OASIS XACML, IRTF RFC 9315, IETF RATS and EAT, and IETF WIMSE wherever they apply. Other state of the art will be added as the WG starts its work.


4. Scope and Non-Goals
----------------------

In Scope
~~~~~~~~

* Characterization of the identity-behaviour-enforcement mismatch, grounded in use cases submitted to FG-TIDA.

* Requirements for the action-time verdict: identify, fix, limit, permit, remediate, block, escalate and indeterminate; attested absence as a statement outside the verdicts; the handling of an escalated action while it is pending; and the verdict when the connection an action relies on has been withdrawn.

..
   [AH] Comment: not sure I understand all of the above: "verdict when the connection an action relies on has been withdrawn"? Is a bit hard to process, but overall it sounds still too much as evidence for the aftermath.

* State of the art of the relevant standardization and research efforts on agent identity and cryptographic methods on behavioural enforcement.

* Identity schemes for agents whose composition changes, based on design invariants and their dependencies.

* Expression of security policy as intent, and the coexistence of intent-based and legacy security policies at a common enforcement point.

* Further solution paths proposed for the same problem, such as least-agency enforcement with structural and semantic predicates and cryptographic enforcement boundaries, assessed against the same requirements.

* Shared fixtures and test cases for comparing paths, including use on the FG-TIDA use-case testbed.


Out of Scope / Non-Goals
~~~~~~~~~~~~~~~~~~~~~~~~

* The working group will not define encodings, schemas, wire formats or protocols.

* The working group will not rank, certify or recommend products, nor run evaluations as a service.

* The working group will not make legal determinations of any party's standing or liability.

* The provenance and standing of the authority behind a reference is addressed by the work under FG-TIDA/themes#5. This working group consumes the authored reference.

* The record that carries a verdict, and the properties any carried claim needs, are addressed by the work under FG-TIDA/themes#1.

* Remote attestation mechanisms are addressed by FG-TIDA WG1.

* Release authority for escalated actions, and human oversight operations generally, are addressed by the work under FG-TIDA/themes#16.

* The declaration of collective-choice operators is addressed by the work under FG-TIDA/themes#18; the design-time method for choosing them is addressed by SG17 Question 1 (X.dmst).

* Population-scale reading of verdicts is addressed by the work under FG-TIDA/themes#21.

* Whether a connection between parties should exist and remain in force is addressed by the work under FG-TIDA/themes#29.

* Identity issuance and lifecycle in general are addressed by ITU-T X.1285 and related SG17 work.

..
   [AH] Comment: good work on that. Thanks!


5. Programme of Work and Deliverables
-------------------------------------

..
   MANDATORY

.. list-table::
   :header-rows: 1
   :widths: 6 29 45 20

   * - #
     - Deliverable
     - Short description
     - Input documents

   * - 1
     - Problem statement and requirements (technical report)
     - Terminology, threat cases and the requirements set against which every path is assessed.
     - FG-TIDA/themes#4, #6 and #36; submitted use cases

   * - 2
     - Action-time conformance verdict: requirements (technical specification)
     - Verdict vocabulary and semantics, adjudication under collision, attested absence, pending escalation and fallback, and relying-party appraisal, including rejection classes for defective records.
     - FG-TIDA/themes#6 task 3 outline; appraisal checks contributed on #6; least-agency requirements contributed on #4

   * - 3
     - Solution paths: description and comparative analysis (technical report)
     - Design-trait identity, intent-expressed policy and its coexistence with classical policy, and further admitted paths, each assessed against deliverable 1.
     - FG-TIDA/themes#4 paths one and two; #6 tasks 1 and 2; #26

..
   [AH] Comment: should we separate it in two different deliverables? I am thinking that some structured identity is very different from intent-based security policy.

   * - 4
     - Shared evaluation fixtures (technical report with versioned fixture set)
     - Versioned cases with expected outcomes, digests for each record, and negative controls, usable across paths and on the use-case testbed.
     - TIDA6-FX fixture posted on FG-TIDA/themes#6; FG-TIDA/use-cases#4 mappings


6. Milestones
-------------

..
   MANDATORY

.. list-table::
   :header-rows: 1
   :widths: 30 70

   * - Target date
     - Milestone

   * - First FG-TIDA meeting, Paris (2026-12)
     - Charter presented; outline of deliverable 1 available in the repository.

   * - Second FG-TIDA meeting, Geneva (2027-01)
     - First draft of deliverable 1 and outline of deliverable 2 available; deliverable 4 fixture set at version 0.3.

   * - Third FG-TIDA meeting (2027)
     - Deliverable 1 agreed by the working group; first drafts of deliverables 2 and 3 available.

   * - Fourth FG-TIDA meeting (2027)
     - Deliverables 2 and 4 agreed by the working group and submitted to the FG-TIDA plenary.

   * - Final FG-TIDA meeting
     - Deliverable 3 agreed and submitted to the FG-TIDA plenary.


7. Coordination, Dependencies and Liaisons
------------------------------------------

..
   MANDATORY

.. list-table::
   :header-rows: 1
   :widths: 35 65

   * - Group / Organization
     - Coordination or dependency

   * - Work under FG-TIDA/themes#1
     - Record format that carries a verdict and attested absence.

   * - Work under FG-TIDA/themes#5
     - Authored reference and the standing of its author.

   * - Work under FG-TIDA/themes#16
     - Release of escalated actions and handling of indeterminate verdicts.

   * - Work under FG-TIDA/themes#18 and #21
     - Declared operators that verdicts are checked against, and population-scale reading of verdicts.

   * - Work under FG-TIDA/themes#44
     - Binding of evaluation results to the artefact, method and moment, shared with verdict records.

   * - FG-TIDA WG1
     - Verdicts and design invariants as claims an attestation can carry.

   * - ITU-T SG17 Question 1 and Question 16
     - X.dmst (design-time aggregation), XSTR.magAI-behavior and X.aplm-aia, complemented without duplication.

   * - IETF RATS and WIMSE
     - Followed as adjacent work; no liaison established.


8. Terminology
--------------

..
   OPTIONAL

The working group will use the common FG-TIDA terminology where applicable. New terms will be communicated to the FG-TIDA terminology and use cases working group.

.. list-table::
   :header-rows: 1
   :widths: 30 70

   * - Term
     - Meaning

   * - Reference
     - The pinned, versioned statement of authority that an action is checked against.

   * - Verdict
     - The result of checking one action against a reference: permit, remediate, block, escalate or indeterminate.

   * - Attested absence
     - An attributed statement that no check was performed, distinct from any verdict and never read as permission.

   * - Appraisal
     - A relying party's check that a carried verdict is attributed, current and consistent with its own record.


9. Working Methods
------------------

..
   OPTIONAL

Each deliverable will be tracked in its own issue in the working group repository. Fixtures will be versioned, with a digest for every record, and changes to expected outcomes will be listed in a changelog. Virtual interim calls will be held between plenary meetings. Contributions folded into a deliverable will remain attributed at clause level.


10. Security and Privacy Considerations
---------------------------------------

..
   OPTIONAL - RECOMMENDED

The deliverables will address the following: a verdict or reference can disclose policy that its owner needs to keep confidential, so verification without full disclosure is required; the evaluator that issues a verdict is itself an attack surface, including for injected instructions; a suppressed verdict must be distinguishable from the absence of any check; and identifiers built from design invariants can make agents and their operators linkable.


11. Success Criteria and Conclusion
-----------------------------------

..
   OPTIONAL

The working group will have completed its chartered work when deliverables 1 to 4 have been submitted to the FG-TIDA plenary.

Following completion, the deliverables may be offered as input to ITU-T Study Groups or other relevant standards bodies, as decided by the Focus Group.


12. Revision History
--------------------

..
   MANDATORY

.. list-table::
   :header-rows: 1
   :widths: 18 22 60

   * - Version
     - Date
     - Change

   * - 0.1
     - 2026-10-26
     - First draft on the FG-TIDA charter template, from the first pass of 6 October 2026 and FG-TIDA/themes#36

   * - 0.2
     - 2026-10-27
     - WG2 designation, provisional co-chairs and repository added

   * - 0.3
     - 2026-10-30
     - Moved into the WG2 repository; destination of deliverables left open, per the co-chairs' preparation meeting

   * - 0.31
     - 2026-10-30
     - Wording changes all over the document, extension to morphing even if SW composition is unchanged as per Theme #4, extension beyond "third party can check", as before the check by a third party comes the question of the enforcement through the second party. Provided some comments in the text, see in edit mode.

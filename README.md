# BPMN-models-Assign_2
# BPMN Assignments – Business Process Modeling and Workflow Design

## 1. Introduction

This repository contains two BPMN (Business Process Model and Notation) assignments developed to demonstrate the design, analysis, and representation of real-world business processes.

Business processes often involve multiple participants, tasks, decisions, communications, and exceptional situations. BPMN provides a standardized graphical notation for representing these activities in a structured and understandable manner.

The two assignments focus on different application domains:

1. **Student Project Approval & Allocation System** – Models the submission, validation, evaluation, approval, and faculty allocation of student project proposals.
2. **Logistics & Shipment Exception Management System** – Models shipment booking, parcel pickup, transportation, delivery, and the handling of exceptions such as failed pickups, damaged parcels, lost shipments, and unsuccessful deliveries.

Both diagrams demonstrate how BPMN can be used to organize activities, define participant responsibilities, represent decision-making, and manage alternative process outcomes.

---

## 2. Assignment 1: Student Project Approval & Allocation System

### 2.1 Overview

The Student Project Approval & Allocation System represents the workflow followed when student teams submit project proposals and obtain approval from the review committee before receiving a suitable faculty guide.

The process begins when a student team submits a project proposal. The proposal undergoes validation and screening before being evaluated by the review committee. Depending on the evaluation result, the proposal may be approved, rejected, or returned for revision.

Once approved, the system checks faculty availability and domain expertise, sends an allocation request, and records the final allocation after the faculty member accepts.

### 2.2 Objectives

- Standardize the project proposal submission and approval process.
- Validate proposal forms and student team requirements.
- Reduce duplicate or highly similar project topics.
- Establish a structured proposal evaluation mechanism.
- Support proposal revisions, rejections, and resubmissions.
- Match approved projects with suitable faculty guides.
- Provide notifications and reminders at important stages.
- Maintain a record of successful faculty allocations.

### 2.3 Participants and Responsibilities

**1. Student / Team**

- Submit the project proposal.
- Correct errors identified during validation.
- Revise the proposal when requested.
- Resubmit the corrected proposal for further processing.

**2. Project Coordinator**

- Screen submitted project proposals.
- Handle requests for late submission approval.
- Coordinate the initial proposal review process.

**3. Review Committee (including HoD)**

- Evaluate project proposals.
- Review the suitability and feasibility of the proposed topic.
- Decide whether a proposal should be approved, revised, or rejected.

**4. Faculty Guide**

- Receive the project allocation request.
- Review and respond to the allocation request.
- Accept the request to supervise the approved project.

**5. Project Management System**

- Validate proposal forms and team rules.
- Check topic similarity.
- Check faculty availability and domain compatibility.
- Allocate a faculty guide and send notifications.
- Send reminders when the evaluation exceeds the expected time.
- Record the final project allocation.

### 2.4 Detailed Workflow

#### Step 1: Project Proposal Submission

The process starts when a project proposal is required. The student team performs the *Submit Project Proposal* task and submits the necessary project details.

#### Step 2: Form and Team Validation

The Project Management System executes *Validate Form & Team Rules*. It checks whether the proposal contains the required information and whether the team satisfies the applicable rules.

An exclusive gateway, *Form & Rules Valid?*, determines the next step:

- **Valid:** The proposal proceeds for screening.
- **Invalid:** The invalid-team-rules path terminates the process.
- **Correctable form error:** The proposal can follow the resubmission route.

#### Step 3: Proposal Screening

The Project Coordinator performs *Screen Proposal* to verify that the submitted proposal is suitable for further consideration.

The diagram also represents a late-submission approval request and a timer event for handling deadline-related situations.

#### Step 4: Topic Similarity Checking

The system performs *Check Topic Similarity* to identify whether the proposed project topic is similar to existing projects. This helps reduce duplication and supports a more effective project selection process.

#### Step 5: Committee Evaluation

The Review Committee performs *Evaluate Proposal* and examines the proposal before reaching the *Proposal Approved?* exclusive gateway.

The gateway represents three possible outcomes:

- **Approved:** The proposal proceeds to faculty allocation.
- **Revise:** The proposal is returned to the student team for correction and resubmission.
- **Rejected:** A rejection notice is sent, and the process ends at the *Proposal Rejected* event.

A timer boundary event is attached to the evaluation task to represent the handling of delayed evaluations through a committee SLA reminder email.

#### Step 6: Faculty Availability and Domain Matching

For an approved proposal, the system performs *Check Guide Availability & Domain Match*.

This activity checks whether a suitable faculty guide is available and whether the guide's area of expertise matches the project topic.

The system then performs *Allocate Faculty Guide* and *Send Allocation Request*.

#### Step 7: Faculty Response

The faculty member receives the allocation request and performs *Accept Allocation Request*.

The *Guide Accepted?* exclusive gateway determines the next action:

- **Yes:** The system sends the approval and allocation notice.
- **Declined:** The workflow returns towards guide availability and domain matching so that another suitable guide can be considered.

#### Step 8: Final Allocation

After the faculty member accepts the allocation, the system performs *Record Final Allocation*.

The process concludes at *Project Allocated Successfully*, indicating that the approved project has been assigned to a faculty guide.

### 2.5 Important BPMN Elements Used

- **Start Event:** Indicates the beginning of the project approval process.
- **User Tasks:** Represent activities performed by people, such as proposal submission and evaluation.
- **Service Tasks:** Represent system operations, such as form validation and topic similarity checking.
- **Exclusive Gateways:** Represent decisions involving validation, approval, and faculty acceptance.
- **Timer Events:** Represent deadline-related triggers and evaluation delays.
- **Message Tasks:** Represent rejection notices, allocation requests, and approval notifications.
- **End Events:** Represent successful allocation, proposal rejection, or process termination.

### 2.6 Expected Outcome

The workflow provides a structured method for managing student project proposals, ensuring that proposals are validated and evaluated before faculty allocation. It also represents alternative paths for revisions, rejection, late submission handling, and faculty allocation decisions.

---

## 3. Assignment 2: Logistics & Shipment Exception Management System

### 3.1 Overview

The Logistics & Shipment Exception Management System represents the complete lifecycle of a shipment, from booking and parcel pickup to transportation and final delivery.

The process includes normal shipment operations as well as exception-handling mechanisms for unsuccessful pickups, damaged parcels, lost shipments, and failed or refused deliveries.

Parallel gateways coordinate concurrent activities, while exclusive gateways determine the appropriate route based on the shipment's status. Timer boundary events represent time-based exceptions, such as shipment tracing and loss investigation.

### 3.2 Objectives

- Organize shipment booking and validation.
- Calculate shipping charges and arrange parcel pickup.
- Coordinate pickup scheduling and driver assignment.
- Support parcel scanning and tracking updates.
- Represent concurrent shipment activities.
- Handle pickup retries and booking cancellation.
- Manage shipment damage and insurance-related claims.
- Initiate tracing and investigation for potentially lost shipments.
- Capture delivery outcomes and proof of delivery.
- Handle return-to-sender operations.
- Close successful shipments and generate invoices.

### 3.3 Participants and Responsibilities

**1. Shipper / Customer**

- Initiate the shipment booking process.
- Provide shipment details required for booking.

**2. Control Tower / Dispatcher**

- Validate shipment booking information.
- Calculate shipment charges.
- Schedule parcel pickup and assign a driver.
- Manage pickup rescheduling and retry limits.
- Send tracking status updates.
- Close successfully delivered shipments and generate invoices.

**3. Pickup Agent**

- Collect the parcel from the shipper.
- Scan the parcel to record its entry into the logistics workflow.

**4. Hub / Warehouse**

- Sort parcels according to their destinations.
- Coordinate line-haul transportation.
- Support the identification and handling of damage or shipment-loss exceptions.

**5. Delivery Agent**

- Send an out-for-delivery notification.
- Attempt parcel delivery.
- Capture proof of delivery.
- Support the return-to-sender process when delivery is refused or unsuccessful.

**6. Recipient**

- Represents the intended receiver of the parcel.
- The recipient lane is included in the diagram, although no explicit activity is currently placed within it.

**7. Claims Department**

- Process refunds or claims associated with shipment exceptions.
- Handle the claims path represented in the workflow.

### 3.4 Detailed Workflow

#### Step 1: Shipment Booking

The process begins at *Shipment Booking Created*. The customer performs the *Book Shipment* task to initiate the delivery request.

#### Step 2: Booking Validation and Charge Calculation

The dispatcher performs *Validate Booking & Calculate Charges* to check the booking details and calculate the applicable shipment charges.

After validation, the workflow proceeds to *Schedule Pickup & Assign Driver*.

#### Step 3: Parallel Processing and Tracking Updates

The *Parallel Split* gateway divides the process into concurrent branches.

One branch sends a tracking status update, while the other supports the remaining shipment-handling activities.

The *Parallel Join* gateway later synchronizes the tracking and successful delivery branches before shipment closure.

#### Step 4: Parcel Pickup and Retry Handling

The Pickup Agent performs *Collect & Scan Parcel*.

The workflow contains a pickup success/failure decision and a rescheduling mechanism. If a pickup attempt fails, the dispatcher can arrange another attempt through *Reschedule Pickup*.

An exclusive gateway controls retry handling:

- **Retry:** Another pickup attempt is arranged.
- **Maximum retry reached:** The system executes *Cancel Booking & Charge Fee* and ends at *Booking Cancelled*.

#### Step 5: Hub Sorting and Transportation

The parcel enters the *Hub Sorting & Line-Haul Transport* subprocess.

This subprocess represents the transportation stage in which parcels are sorted and moved through the logistics network towards their destination.

The subprocess also contains boundary events for handling time-related and damage-related exceptions.

#### Step 6: Shipment Damage and Insurance Handling

When the damage-related boundary event is triggered, the workflow reaches the *Insured?* exclusive gateway.

- **No:** The shipper is notified of the damage.
- **Yes:** The workflow proceeds to the Claims Department's *Process Refund / Claim* activity.

This branch represents different handling paths according to insurance status.

#### Step 7: Lost Shipment Investigation

A timer boundary event can trigger the *Run Tracing & Search Sub-Process* when a shipment remains unresolved for the specified period.

The investigation aims to trace the shipment and determine its status. The represented path ends at *Declare Shipment Lost*.

#### Step 8: Out-for-Delivery Notification

For shipments continuing through the normal delivery process, the Delivery Agent performs *Out for Delivery Notice* to notify the recipient that the parcel is approaching delivery.

#### Step 9: Delivery Attempt and Proof of Delivery

The Delivery Agent performs *Deliver Parcel & Capture Proof of Delivery*.

The subsequent exclusive gateway evaluates the delivery outcome:

- **Delivered:** The flow proceeds to the parallel join.
- **Refused / Failed:** The parcel is routed to *Return to Sender & Hold at Depot*, after which that path ends.

Proof of delivery serves as a record of successful parcel handover.

#### Step 10: Shipment Closure

After the successful delivery branch and tracking-update branch are synchronized, the dispatcher performs *Close Shipment & Generate Invoice*.

The workflow ends at *Shipment Delivered*, representing successful completion of the shipment process.

### 3.5 Important BPMN Elements Used

- **Start Event:** Initiates shipment booking.
- **User Tasks:** Represent human activities such as booking, parcel collection, and delivery.
- **Service Tasks:** Represent automated activities such as booking validation and shipment closure.
- **Send Tasks:** Represent tracking updates and delivery notifications.
- **Exclusive Gateways:** Control pickup retry, insurance, and delivery outcome decisions.
- **Parallel Gateways:** Split and synchronize concurrent activities.
- **Timer Boundary Events:** Represent time-based exceptions during transportation.
- **Subprocesses:** Group transportation and tracing activities.
- **End Events:** Represent delivery, cancellation, loss declaration, or return-related outcomes.

### 3.6 Exception-Handling Scenarios

The diagram includes several alternative paths that demonstrate how a logistics workflow can respond to unexpected situations.

| Scenario | Represented response |
|---|---|
| Pickup failure | Reschedule pickup or retry the attempt |
| Retry limit reached | Cancel the booking and charge a fee |
| Shipment damaged | Check insurance status and notify the shipper or process a claim |
| Shipment potentially lost | Run tracing and search activities |
| Delivery refused or unsuccessful | Return the parcel to the sender and hold it at the depot |
| Delivery successful | Synchronize required branches, close the shipment, and generate the invoice |

### 3.7 Expected Outcome

The workflow provides a structured representation of shipment operations and exception handling. It shows how normal delivery activities interact with tracking, cancellation, insurance claims, loss investigation, and return-to-sender procedures.


## 4. BPMN Concepts Demonstrated

### Pools and Lanes

A pool represents the overall participant or process, while lanes divide the responsibilities of the participants or departments within it.

### Events

Events represent occurrences that initiate, affect, or terminate process execution. These include start events, end events, timer events, and boundary events.

### Tasks and Activities

Tasks represent individual units of work performed by people or systems. Examples include submitting a proposal, validating booking details, scanning parcels, and recording an allocation.

### Exclusive Gateways (XOR)

Exclusive gateways select one outgoing route based on the conditions of a decision. They are used for proposal approval, faculty acceptance, pickup retry decisions, insurance checks, and delivery outcomes.

### Parallel Gateways (AND)

Parallel gateways allow multiple branches to proceed concurrently or synchronize incoming branches. They are particularly important in the shipment workflow.

### Boundary Events

Boundary events are attached to the boundaries of tasks or subprocesses and represent events that occur while those activities are in progress.

### Message Tasks

Message tasks represent communication, such as sending approval notices, rejection notices, tracking updates, and out-for-delivery notifications.

### Subprocesses

Subprocesses group related activities into a single process element to keep the main diagram organized and easier to understand.

### Sequence Flows

Sequence flows connect BPMN elements and show the order in which activities, decisions, and events are executed.

---

## 5. Learning Outcomes

Through these assignments, I gained an understanding of:

- Representing real-world business processes using BPMN.
- Organizing responsibilities through pools and lanes.
- Modeling human and automated activities.
- Representing business decisions through exclusive gateways.
- Modeling concurrent activities using parallel gateways.
- Representing time-based triggers and boundary events.
- Designing alternative process paths for exception handling.
- Modeling notifications and communication between activities.
- Structuring complex workflows using subprocesses.
- Documenting business processes clearly and systematically.

---

## 6. Conclusion

These two assignments demonstrate how BPMN can be applied to different real-world business processes.

The Student Project Approval & Allocation System focuses on proposal validation, evaluation, decision-making, and faculty allocation. The Logistics & Shipment Exception Management System focuses on shipment operations, concurrent processing, delivery tracking, and exception handling.

Together, the assignments demonstrate how BPMN provides a standardized visual approach for understanding workflow sequences, participant responsibilities, business decisions, and exceptional situations.




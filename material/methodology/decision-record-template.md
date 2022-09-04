# Introduction
This documents contains a template for decision records in order to guide a development team to fill-out all important aspects of a decision they make. To
keep track of all decision help people who are new to the team or externals of the product to understand why certain decision have been made and what
consequences these decisions incorporate. Decision records need be stored as long as they are relevant for that product. When writing a decision record try to stay
lean, meaning the documentation should try to stay as concise as possible.
## When is a decision record is required?
Very generally you could say that a decision record should be written whenever a decision of impact is made; it is up to each team to align what defines an
impact. Even decisions with small impact can be worthy of documenting. Following questions can help you find out if decision needs to be recorded:
* Could the problem that is solved by the decision reoccur?
* Should a new team member know about the decision in order to be able to work on the product?
* Could another team learn or reuse the solution provided by this decision?
* Is the company or it's customer impacted by the decision?
It might also be helpful to consult decisions in self organising teams in order to evaluate wether your decision is within the scope of your team.

# Template

| Status        | Not started / In Progress / Decided / Deprecated / Superseded                                                                                                 |
|---------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Owner         | <owner> // who needs this deicison                                                                                                                            |
| Contributors  | <contributers>                                                                                                                                                |
| Approved      | <approver> // when approval is mandatory                                                                                                                      |
| Due date      | <date> or <event when it needs to be decided> // does the decision has a deadline? if the decision has no urgency, then the decision does not need to be made |
| Revision date | <date> or <event when it needs to be reevaluated> // try to set up a meeting where you can review the decision based on the experience you gained             |
| Decision      | In the context of <use case/ user story>, facing <concern> we decided for <option> and neglected <other options>, to achieve <system qualities/desired consequences / desired consequences>, accepting <downside / undesired consequences>, because <additional rationale>. |

## Problem
Describe the problem you're trying to solve and explain why it's important.
* What is the problem?
* What is the impact of the problem?
* What would the consequence if the problem is not solved?
* Who is impacted by the problem?

## Options
|             | Option 1                                                   | Option 2  | Option ... |
|-------------|------------------------------------------------------------|-----------|------------|
| Pros & Cons | + <advantage> 
                - <disadvanatage>                            |           |            |
| Consequence | * Are there any constraints concluding?                    |           |            |
| Impact      | * Is a system impacted? * Is a person or a group impacted? |           |            |
|             |                                                            |           |            |
|             |                                                            |           |            |
|             |                                                            |           |            |

## Decision
Explain why you decided for the option of your choice. You could highlight which advantages or disadvantages that lead you to your decision. The
consequence for this decision and who is impacted by them should be further elaborated.
//example sentence for the decision
Follow up
List when you should revise the decision. Overtime we gain new knowledge that enables us to review past decision.
* e.g.: As soon as <criteria> is met we will check <aspect> of this decision in order to <action>.
* e.g.: After <due date> we will check <aspect> of this decision in order to <action>.

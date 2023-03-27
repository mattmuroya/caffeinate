# Behavior-Driven Development (BDD)

My follow-along repo for
[LinkedIn's BDD course](https://www.linkedin.com/learning-login/share?account=137796258&forceAccount=false&redirect=https%3A%2F%2Fwww.linkedin.com%2Flearning%2Fbehavior-driven-development%3Ftrk%3Dshare_ent_url%26shareId%3DUpzZ5KYhRXe8RdtxQ4eq5g%253D%253D).

Behavior-driven development (BDD) is a software development methodology that
emphasizes the user's perspective. It is rooted in Agile principles,
facilitating and aligning software development with customer needs.

## Agile

The [Agile Manifesto](https://agilemanifesto.org/) comprises these foundational
concepts:

- Individuals and interactions over processes and tools
- Working software over comprehensive documentation
- Customer collaboration over contract negotiation
- Responding to change over following a plan

### User stories

User stories are informal descriptions of a software feature written from the
perspective of a user developed during the consult stage. They generally follow
the "five Ws":

> As {who/what/where}
>
> I {want}
>
> because {why}

For example:

> As {a user of Acme.com}
>
> I {want to be able to access content on my phone}
>
> because {I might not always have my computer}

User stories help developers understand the goals of features; it emphasizes end
user perspectives to guide development of features that people actually want.

### Acceptance criteria

Acceptance criteria are the formalized the requirements outlined in user stories
that must be met for the product to be "acceptable" from the user's perspective.

They are defined as a set of statements with established PASS/FAIL results for
both functional and non-functional requirements.

- Basis for testing
- Written by clients, POs, and/or dev team
- Reviewed by dev team prior to testing

Types acceptance criteria can vary. Some examples:

- List-driven or rule oriented—useful for creating a backlog
- Illustrated or scenario-oriented—useful for translating testing into a format
  that can drive BDD

## Principles of behavior-driven development

In 1976, a book titled _Software Reliability_ promoted the separation of
development from testing, posting that developers should never test their own
code.

Kent Beck, the creator of the "extreme programming" (XP) development
methodology, is attributed with "rediscovering" test-driven development (TDD) as
an evolution of methodologies dating back to the 60s. Beck created the SUnit
unit testing framework for use with the Smalltalk programming language, with
which he began promoting TDD:

- Developers should "write their own unit tests, one per class" and "spend
  25%-50% of their time developing test"
- "Start with a test so we know when we are done"

### TDD process

1. Write a failing test.
2. Write the code that allows for a passing test.
3. Refactor if necessary.
4. Repeat until you have working software with all tests are passing.

### Where does TDD fall short?

- Doesn't specify what to test, how much, and how to understand failing tests?
- No clear guidelines can lead to confusion and misunderstandings

Behavior-driven development (BDD) helps us to focus on what matters in the TDD
process and avoid unnecessary—or even detrimental—work.

### Introduction of BDD

BDD is attributed to a 2006 blog post titled _Introducing BDD_ written by Dan
North for _Better Software_ magazine.

BDD **takes principles from TDD and Agile, combining the needs of business
analysts and developers into a single framework**. It emerged as a new paradigm
for software development at addresses some of the shortcomings of traditional
software development (siloed teams, unclear on what to test, how to test, or
even requirements to build against).

With BDD, business needs are defined _in code_, making them testable; it
replaces the concept of "tests" with "behaviors," helping to resolve ambiguity
about what to test.

- Provides direction in what needs to be tested
- Clarifies to business stakeholders

North encouraged writing tests expressively, usually in the form of a sentence
that declares what a test is checking—comprehensively describing the _behavior_
of the system you are building.

BDD is a tool for building the correct product that end user will love; or at
least, that does what it is expected to do.

### Starting points for BDD

- POs understand what product they desire
- Some/most of the acceptance criteria have been defined
- User stories have been defined

One simple and effective method of clarifying ambiguity with acceptance criteria
is known as **example mapping**, which uses color-coded index cards to visually
map out (1, yellow ) the user story, (2, blue) the specific rules which
constrain the specific scope of the story (the acceptance criteria), (3, green)
concrete examples of the user story within the context of each particular rule,
and (4, red) questions that arise but cannot be immediately answered.

### Concrete examples/scenarios

Concrete examples of user stories (BDD scenarios) should be very specific,
fleshed out, and full of context:

> As a barista, I came into work Monday morning to run through our inventory, I
> noticed we were low on Colombian Dark Roast. So, I logged into our inventory
> management system and ordered two large bags of Colombian Dark Roast. The next
> Monday, the bags were delivered by our local distributor.

Concrete examples should contain:

- Names
- Context
- Situational awareness

Concrete examples are used to derive _scenarios_ that describe the system
behavior in the context of specific preconditions of the user story.

Acceptance criteria:

- Address what defines a working system (i.e. "I can place an order for
  Colombian Dark Roast")
- Written as PASS/FAIL

Scenarios:

- Define _initial conditions_ for acceptance criteria (i.e. "I am out of Dark
  Roast, placing an order results in order confirmation/delivery")
- States the trigger of that scenario and expected outcome

### Scenario format

- Scenario: a user story
- Given: some set of initial conditions
- When: an event occurs
- Then: an outcome is expected

## BDD Process

BDD seeks to clarify how features should be built and tested through shared
understanding of requirements, behaviors, and acceptance criteria. These
criteria are then translated into specific, testable statements used to verify
the system behavior.

### Three amigos

The primary perspectives (POs, development, QA) of any Agile project should meet
periodically to seek and discuss shared understanding about goals and increment
before, during, and after each increment of work. These meetings are commonly
referred to as "Three Amigos" workshops, huddles, or the triad.

- Build shared understanding of work increments
- Identify confusion/issues
- Define clear acceptance criteria marking completion of an increment
- Allows for buy-in from each perspective

## Gherkin

Acceptance criteria need to be translated into executable tests to verify system
behavior and confirm that we're on track building the right thing.

[Gherkin](https://docs.cucumber.io/gherkin) is a human- and business-readable,
domain-specific programming language the describes your software's behavior, but
now how the behavior is implemented (black-box)

- Automates testing
- Acts as concrete examples documentation

### Syntax/keywords

Gherkin files are similar to YAML in that they use keywords and indentation to
organize statements. The basic keywords in a Gherkin file are:

- `feature`: Name and (optional) brief description of the feature. Every Gherkin
  file begins with the `feature` keyword.
- `scenario`: Single concrete example of how the system should behave written as
  PASS/FAIL. Each `feature` generally has 5-20 scenarios.
- `given`: Describes context for the `scenario`; provides initial preconditions
  before the rest of the example unfolds.
- `when`: An event enacted on the system by some actor (person, system event,
  etc.) leading to a particular outcome.
- `then`: The expected system behavior/outcome of the `scenario` in this
  context.

Putting this information into a Gherkin file acts as documentation for your
concrete examples and your acceptance criteria. When the file is parsed, it is
connected to a series of definitions for the `given`, `when`, and `then` steps
that are mapped to your application's functionality.

### Translate a scenario into Gherkin

Here is an example of a user story:

> Story: Customer pays with a credit card.
>
> As a sales associate, I should be able to process payments when given a credit
> card.

This story is translated into scenarios using "declared dephrasing," meaning
that it doesn't reference the particulars of a user interface or sequence of
steps. Scenarios **describe the behavior of the system under specific initial
conditions**.

> Scenario 1: Total charge is over $2 credit card minimum
>
> **Given** Maria orders $3 of coffee from Li, **when** Maria pays with a credit
> card, **then** Li should process the payment.

> Scenario 2: Total charge is under the $2 credit card minimum
>
> **Given** Maria orders $1 of coffee from Li, **when** Maria pays with a credit
> card, **then** Li should NOT process the payment.

These are two scenarios that describe the behavior of the system in the context
of the user story "Customer pays with a credit card" derived from the concrete
examples of when the order is above/below the $2 minimum.

Phrasing acceptance criteria as a scenario in Gherkin allows it to be parsed by
BDD frameworks like Cucumber

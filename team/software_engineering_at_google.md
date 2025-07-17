Software Engineering at Google
Lessons Learned from Programming Over Time

Hyrum’s Law:
With a sufficient number of users of an API, it does not matter what you promise in the contract:
all observable behaviors of your system will be depended on by somebody.

## Ch 1 What is software engineering?

* Software engineering is programming integrated over time.
* Software engineering is the mutliperson development of multi version programs
* Hyrums law: with a sufficient number of users of an api, it does not matter what you promise in the contract, all
  observable system behaviours will be depended on by somebody
* When programming, clever is a compliment. When software engineering, it’s an accusation.
* If a product person experiences outages or other problems as part of an infrastructure change but the problem wasnt
  surfaced by CI tests, then it is not the problem of the infrastructure change.
* If you liked it you should have put a CI test on it. The Beyonce rule.
* Knowledge sharing is viral. If you have 100 engineers writing go, a single go expert answering questions will soon
  lead to 100 engineers writing expert go.
* The more frequently you change your infrastructure, the easier it becomes to do so.
* The earlier in the development process an issue is discovered, the cheaper it is to fix. “Shift left on security”
* Should never say " do it this way because I said so. Should trade off: financial cost, resource cost,personnel
  cost,transaction cost, opportunity cost and societal costs. Aim for consensus not unanimity.
* Don't underestimate keeping engineers happy. This can have huge productivity costs, in the region of 10-20%
* If there isn't data to drive a decision, there is likely still precedent, evidence and arguement
* Time doesn’t only trigger change in technical dependencies but in data used to drive decisions too - dont be afraid to
  change your mind.

## Key Principles & TL;DR Insights

* Dimensional Difference
  Software engineering adds time, collaboration, and scalability dimensions to the raw task of programming.
* Tool/Practice Fit is Context-Dependent
  Best practices for a 10-year product don’t apply to a 10-hour script—and vice versa.
* Sustainability
  Code is sustainable if you can respond to change—even if you choose not to change.
* Hyrum’s Law
  Any observable behavior of a system will be relied on, no matter what the API contract says.
* Scalability of Human Effort
  Tasks done often should scale with policies and automation, not more people.
* Boiled-Frog Risk
  Small inefficiencies accumulate—monitor and manage them before they become crises.
* Economies of Scale Reward Expertise
  Smart solutions scale better when applied repeatedly across a system.
* Bad Reasoning
  “Because I said so” is not a valid justification for decisions in engineering.
* Data-Informed ≠ Data-Only
  Most real-world decisions are a mix of data, assumptions, experience, and debate.
* Adaptability Is Key
  Being data-driven means also being change-driven—mistakes and reversals are part of the process.

### Part II, Culture

* Be aware of the trade-offs of working in isolation.
* Acknowledge the amount of time that you and your team spend communicating and in interpersonal conflict. A small
  investment in understanding personalities and working styles of yourself and others can go a long way toward improving
  productivity.
* If you want to work effectively with a team or a large organization, be aware of your preferred working style and that
  of others.

### Part III, Knowledge Sharing

* Knowledge is critical capital in a software engineering org; sharing it builds resilience and scalability.
* Psychological safety is the foundation for effective knowledge sharing—people need to feel safe to ask, teach, and
  learn.
* Start small: Encourage asking questions, documenting answers, and sharing broadly.
* Make help accessible: Combine documented references with support from human experts.
* Recognize and reward teachers: Promote mentoring and cross-team collaboration.
* No one-size-fits-all: Use a mix of strategies (docs, mentorship, review processes, tools) tailored to your org's needs
  and maturity.

🧠 Readability: Google’s Mentorship via Code Review

* A human-driven, mandatory process where certified reviewers teach best practices through rigorous code review.
* Ensures codebase-wide consistency, maintainability, and propagation of expertise.
* Scales linearly with org growth but provides long-term benefits in quality and velocity.
* Reviewers are mentors, not gatekeepers; teaching is the priority.
* Supported by tools and static analysis to reduce repetitive feedback and focus on higher-order concerns.
* Proven by internal studies to improve engineer satisfaction, review speed, and code quality.

### Part IV, Engineering for Equity

* Bias is the default.
* Diversity is necessary to design properly for a comprehensive user base.
* Inclusivity is critical not just to improving the hiring pipeline for underrepresented groups, but to providing a
  truly supportive work environment for all people.
* Product velocity must be evaluated against providing a product that is truly useful to all users. It’s better to
  slow down than to release a product that might cause harm to some users.

### Part V, How to Lead a Team

* Don’t “manage” in the traditional sense; focus on leadership, influence, and serving your team.
* Delegate where possible; don’t DIY (Do It Yourself).
* Pay particular attention to the focus, direction, and velocity of your team.

### Part VI, Leading at Scale

* Always Be Deciding: Ambiguous problems have no magic answer; they’re all about finding the right trade-offs of the
  moment, and iterating.
* Always Be Leaving: Your job, as a leader, is to build an organization that automatically solves a class of ambiguous
  problems—over time—without you needing to be present.
* Always Be Scaling: Success generates more responsibility over time, and you must proactively manage the scaling of
  this work in order to protect your scarce resources of personal time, attention, and energy.

### Part VII, Taking Action and Tracking Results

* Before measuring productivity, ask whether the result is actionable, regardless of whether the result is positive or
  negative. If you can’t do anything with the result, it is likely not worth measuring.
* Select meaningful metrics using the GSM framework. A good metric is a reasonable proxy to the signal you’re trying
  to measure, and it is traceable back to your original goals.
* Select metrics that cover all parts of productivity (QUANTS). By doing this, you ensure that you aren’t improving one
  aspect of productivity (like developer velocity) at the cost of another (like code quality).
* Qualitative metrics are metrics, too! Consider having a survey mechanism for tracking longitudinal metrics about
  engineers’ beliefs. Qualitative metrics should also align with the quantitative metrics; if they do not, it is likely
  the quantitative metrics that are incorrect.
* Aim to create recommendations that are built into the developer workflow and incentive structures. Even though it is
  sometimes necessary to recommend additional training or documentation, change is more likely to occur if it is built
  into the developer’s daily habits.

### PART VIII, Style Guides and rules

* Rules and guidance should aim to support resilience to time and scaling.
* Know the data so that rules can be adjusted.
* Not everything should be a rule.
* Consistency is key.
* Automate enforcement when possible.

### Part IX, Code review

* Code review has many benefits, including ensuring code correctness, comprehension, and consistency across a
  codebase.
* Always check your assumptions through someone else; optimize for the reader.
* Provide the opportunity for critical feedback while remaining professional.
* Code review is important for knowledge sharing throughout an organization.
* Automation is critical for scaling the process.
* The code review itself provides a historical record.

### Part X, Documentation

* Documentation is hugely important over time and scale.
* Documentation changes should leverage the existing developer workflow.
* Keep documents focused on one purpose.
* Write for your audience, not yourself.

### Part XI, Testing Overview

* Automated testing is foundational to enabling software to change.
* For tests to scale, they must be automated.
* A balanced test suite is necessary for maintaining healthy test coverage.
* “If you liked it, you should have put a test on it.”
* Changing the testing culture in organizations takes time.

### Part XII, Unit Testing

* Strive for unchanging tests.
* Test via public APIs.
* Test state, not interactions.
* Make your tests complete and concise.
* Test behaviors, not methods.
* Structure tests to emphasize behaviors.
* Name tests after the behavior being tested.
* Don’t put logic in tests.
* Write clear failure messages.
* Follow DAMP over DRY when sharing code for tests.

### PART XIII, Test doubles

* A real implementation should be preferred over a test double.
* A fake is often the ideal solution if a real implementation can’t be used in a test.
* Overuse of stubbing leads to tests that are unclear and brittle.
* Interaction testing should be avoided when possible: it leads to tests that are brittle because it exposes
  implementation details of the system under test.

### Part XIV, Larger tests

* Larger tests cover things unit tests cannot.
* Large tests are composed of a System Under Test, Data, Action, and Verification.
* A good design includes a test strategy that identifies risks and larger tests that mitigate them.
* Extra effort must be made with larger tests to keep them from creating friction in the developer workflow.

### Part XV, Deprecation

* Software systems have continuing maintenance costs that should be weighed against the costs of removing them.
* Removing things is often more difficult than building them to begin with because existing users are often using the
  system beyond its original design.
* Evolving a system in place is usually cheaper than replacing it with a new one, when turndown costs are included.
* It is difficult to honestly evaluate the costs involved in deciding whether to deprecate: aside from the direct
  maintenance costs involved in keeping the old system around, there are ecosystem costs involved in having multiple
  similar systems to choose between and that might need to interoperate. The old system might implicitly be a drag on
  feature development for the new. These ecosystem costs are diffuse and difficult to measure. Deprecation and removal
  costs are often similarly diffuse.

### Part XVI, VCS

* Use version control for any software development project larger than “toy project with only one developer that will
  never be updated.”
* There’s an inherent scaling problem when there are choices in “which version of this should I depend upon?”
* One-Version Rules are surprisingly important for organizational efficiency. Removing choices in where to commit or
  what to depend upon can result in significant simplification.
* In some languages, you might be able to spend some effort to dodge this with technical approaches like shading,
  separate compilation, linker hiding, and so on. The work to get those approaches working is entirely lost labor—your
  software engineers aren’t producing anything, they’re just working around technical debts.
* Previous research (DORA/State of DevOps/Accelerate) has shown that trunk-based development is a predictive factor in
  high-performing development organizations. Long-lived dev branches are not a good default plan.
* Use whatever version control system makes sense for you. If your organization wants to prioritize separate
  repositories for separate projects, it’s still probably wise for interrepository dependencies to be unpinned/“at
  head”/“trunk based.” There are an increasing number of VCS and build system facilities that allow you to have both
  small, fine-grained repositories as well as a consistent “virtual” head/trunk notion for the whole organization.

### Part XVII, Code Search

* Helping your developers understand code can be a big boost to engineering productivity. At Google, the key tool for
  this is Code Search.
* Code Search has additional value as a basis for other tools and as a central, standard place that all documentation
  and developer tools link to.
* The huge size of the Google codebase made a custom tool—as opposed to, for example, grep or an IDE’s
  indexing—necessary.
* As an interactive tool, Code Search must be fast, allowing a “question and answer” workflow. It is expected to have
  low latency in every respect: search, browsing, and indexing.
* It will be widely used only if it is trusted, and will be trusted only if it indexes all code, gives all results, and
  gives the desired results first. However, earlier, less powerful, versions were both useful and used, as long as their
  limits were understood.

### Part XVIII, Build Systems

* A fully featured build system is necessary to keep developers productive as an organization scales.
* Power and flexibility come at a cost. Restricting the build system appropriately makes it easier on developers.
* Build systems organized around artifacts tend to scale better and be more reliable than build systems organized around
  tasks.
* When defining artifacts and dependencies, it’s better to aim for fine-grained modules. Fine-grained modules are better
  able to take advantage of parallelism and incremental builds.
* External dependencies should be versioned explicitly under source control. Relying on “latest” versions is a recipe
  for disaster and unreproducible builds.

[//]: # (399)
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
  
* [//]: # (163)
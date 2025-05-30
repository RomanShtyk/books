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

[//]: # (23) Software Engineering Versus Programming
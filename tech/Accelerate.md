# Accelerate - Building and Scaling High Performing Technology Organisations by Nicole Fergrson

# Chapter 1

* Why Technology Performance Matters

Companies that adopt modern software development and DevOps practices consistently outperform their competitors.
The ability to deliver software quickly, reliably, and safely is a key differentiator in today’s business world.

* Debunking the Trade-Off Myth

Traditional thinking suggests that companies must choose between speed (fast delivery) and stability (reliable systems).
Research proves that the best organizations achieve both speed and stability simultaneously.

* Measuring Software Delivery Performance

The authors introduce four key metrics that define high-performance teams:
Deployment Frequency (How often code is released)
Lead Time for Changes (Time from code commit to production)
Mean Time to Restore (MTTR) (How fast issues are resolved)
Change Failure Rate (Percentage of deployments causing issues)

* The Power of DevOps & Lean Practices

Adopting DevOps and Lean principles—like automation, continuous delivery, and cross-team collaboration—leads to better
software delivery.

* Main Takeaway
  The chapter challenges old assumptions and shows that high-performing teams can move fast and maintain stability. The
  book aims to provide data-driven insights into what makes great software teams successful.

# Chapter 2: Measuring Performance

🚀 High-performing teams deploy multiple times per day, have short lead times (hours or minutes), recover quickly, and
have low failure rates.

🐢 Low-performing teams have long release cycles (weeks or months), slow recovery times, and frequent failures.

1. The Four Key Metrics
    * Deployment Frequency – How often an organization successfully releases software.
    * Lead Time for Changes – The time it takes for a code change to go from commit to production.
    * Mean Time to Restore (MTTR) – How quickly a team can recover from failures.
    * Change Failure Rate – The percentage of deployments that cause incidents requiring fixes.

2. Moving Beyond Traditional Metrics
   Traditional software success metrics (e.g., lines of code, number of commits, or hours worked) do not accurately
   reflect delivery performance.
   Instead, focusing on the four key DevOps metrics leads to better business outcomes.
3. Stability vs. Speed: A False Trade-Off
   Many believe that faster releases lead to unstable systems, but the research shows that high-performing teams achieve
   both speed and stability.
   Good DevOps practices (e.g., automated testing, continuous integration, and trunk-based development) help teams
   release quickly without compromising reliability.

4. Main Takeaway
   The four key DevOps metrics are the best indicators of software delivery success. High-performing teams focus on
   frequent deployments, fast recovery, and low failure rates rather than outdated productivity measures.

# Chapter 3: MEASURING AND CHANGING CULTURE

1. Organization culture, three levels of culture:
    * Basic assumptions: Invisible, things that we just “know”.
    * Values: more “visible”.
    * Artifacts:
        * Mission statements.
        * Technology.
        * Formal procedures.
        * Heroes.
        * Rituals.
        * Focus on second level.
2. Ron Westrum, three types:
   +------------------------------+---------------+----------------+------------------+
   | | Pathological | Bureaucratic | Generative |
   +------------------------------+---------------+----------------+------------------+
   | Power Orientation | Power-oriented | Rule-oriented | Performance-oriented |
   | Cooperation Level | Low | Modest | High |
   | Handling of Messengers | "Shot"        | Neglected | Trained |
   | Responsibility Approach | Shirked | Narrow | Shared |
   | Bridging Between Teams | Discouraged | Tolerated | Encouraged |
   | Response to Failure | Scapegoating | Justice | Inquiry |
   | Approach to Novelty | Crushed | Leads to problems | Implemented |
   +------------------------------+---------------+----------------+------------------+

3. Good information flow is critical:
    * Answers what and when needs to be answered, in a way that can be effectively used.
4. Org culture predicts performance outcomes.
5. Bureaucracy is not bad. Ensures fairness.
6. Good culture:
    * Trust and cooperation.
    * Higher quality decision making.
    * Easy to reverse bad decisions.
    * Higher job satisfaction.
    * Change culture by first changing what people do, not try to first change how people think (John Shook).

# Chapter 4 - Technical Practices

## Technical Practices are Vital

**Not optional, not secondary.**

## Key Principles of Continuous Delivery (CD):

- **Build quality in.**
- **Small batches.**
- **People solve problems, computers do repetitive tasks.**
- **Continuous improvement.**
- **Everyone is responsible.**

## Foundations of Continuous Delivery:

- **Comprehensive configuration management:** Everything in **Version Control System (VCS)**.
- **Continuous Integration (CI).**
- **Continuous Testing.**
- **Jerry Weinberg:** *"Quality is value to some person."*

## CD Brings Higher Quality:

- **Less rework or unplanned work.**
- **Fewer bugs.**

## Practices:

### **Version Control**

- Includes **system and application configuration**.

### **Test Automation**

- **Reliable tests.**
- **Written by developers.**
- **Test-Driven Development (TDD)** is important but **not mandatory**.
- **Test Data Management.**

### **Trunk-Based Development**

- No branches older than **one day**.

### **Shift Left on Security**

- Incorporate security checks **early in the development process**.

# Chapter 5 - Architecture

## Most Important Characteristic: Loosely Coupled

A **loosely coupled** architecture means:

- **Most testing can be done without an integrated environment.**
- **Releases can happen independently of other apps they depend on.**

### **Challenges in Low-Performing Teams:**

- More likely to be integrating with **custom software** developed by another company (or outsourced).
- Often working on **mainframe systems**, limiting flexibility.

## **Biggest Contributor to Continuous Delivery (CD):**

- Teams should be able to do work **without needing to talk with anyone outside the team** → a.k.a. **proper
  cross-functional teams**.
- **Read:** *Steve Yegge’s “Platform Rant”*.

## **Scaling Engineering Organizations**

- **Loosely coupled architectures enable organizational scaling.**
- **Teams that choose their own tools perform better**, but should standardize around **architecture and infrastructure
  configuration**.

## **Role of Architects**

- Architects should **focus on engineers and outcomes**, not specific tools or technologies.

# Chapter 6 - Integrating InfoSec into the Delivery Lifecycle

## **Typical InfoSec Ratio**

- **1** InfoSec engineer per **10** infrastructure engineers per **100** developers.

## **Key Security Principles**

- **OWASP Top 10** – Awareness of the most critical security risks.
- **Building security into software** improves both **delivery performance** and **security quality**.

## **Shift Left on Security**

- **Security experts are involved earlier** and throughout the entire **DevOps process**.
- **Security teams provide**:
    - **Secure tools, libraries, and processes**.
    - **Guidance and resources** to help developers build security into their software.

## **The Rugged Manifesto**

- A mindset that promotes **resilient, proactive security** in software development.

# Chapter 7 - Management Practices

## **Origin**

- Derived from the **Lean movement**.

## **Key Practices**

### **Limit Work in Progress (WIP)**

- Helps manage flow but is **not enough on its own**.

### **Visual Management**

- Track **key quality and productivity metrics**.

### **Feedback from Production**

- Use real-world **production feedback** to drive **business decisions**.

### **Intrateam Code Reviews**

- **Best way to approve changes** → Includes **pair programming**.

# Chapter 8 - Product Development

## **The Lean Startup – Eric Ries**

- A **lightweight approach** to explore **new business models** and **product ideas**.

## **Lean Product Development**

### **Small Batches**

- Work in batches **smaller than a week**.
- Focus on **Minimum Viable Product (MVP)**.

### **Make Flow of Work Visible**

- Track progress **from business to customers**.
- Show the **status of products and features**.

### **Customer Feedback**

- Use **satisfaction metrics** to measure success.
- **Actively seek feedback** and implement it.

### **Team Experimentation**

- Teams can **experiment without external approval**.
- Teams **adjust requirements** as they learn.

# Chapter 9 - Making Work Sustainable

## **Deployment Pain and Organizational Performance**

- Where **code deployments are painful**, **organizational performance suffers**.
- To **reduce deployment pain**, apply the **same technical practices** that improve **delivery speed and stability**.

## **Reducing Burnout**

- **Foster a learning environment** → Focus on **learning over blaming**.
- **Create a strong sense of purpose**.
- **Invest in employee development**: Provide **time, space, and resources** for growth.
- **Remove obstacles** that hinder productivity.
- **Give teams authority** to make decisions that affect them.

## **Burnout Risks**

- **Overwork**
- **Lack of control**
- **Insufficient rewards**
- **Breakdown of community**
- **Absence of fairness**
- **Value conflicts**

## **Role of Leadership**

- Leaders should **change the environment**, not try to **"fix" the person**.
- Recognize the difference between **official vs. real organizational values**.

# Chapter 10 - Employee Satisfaction, Identity, and Engagement

## **Employee Net Promoter Score (eNPS) and Business Outcomes**

- A **higher eNPS** leads to **better business performance**.

## **What is eNPS?**

- **Question:** *“How likely is it that you would recommend our organization/team to a friend or colleague?”*
    - **9-10** → **Promoters** (Highly satisfied employees)
    - **7-8** → **Passives** (Neutral employees)
    - **0-6** → **Detractors** (Unhappy employees)

## **People as the Organization’s Greatest Asset**

- Employees are **critical to success**.
- **Diversity in gender and minorities** leads to **better outcomes**.

# Chapter 11 - Leaders and Managers

## **What is Leadership?**

- **Inspiring and motivating** those around you.

## **Essential for:**

- Establishing **high-trust cultural norms**.
- Supporting **developer productivity**.
- Encouraging **team experimentation and innovation**.
- **Breaking down silos** to achieve **strategic alignment**.

## **Transformational Leaders**

- **Vision** → Clear direction for where the organization should be in **5 years**.
- **Inspirational communication**.
- **Intellectual stimulation** → Encouraging creative problem-solving.
- **Supportive leadership** → Caring about employees' personal needs.
- **Personal recognition** → Acknowledging contributions.

## **Transformational Leadership Approach**

- **Appeals to followers' values and sense of purpose**.
- Encourages employees to **identify with the organization**.

## **Building a Culture of Learning**

- **Create a training budget** and **advocate for its use**.
- **Google 20% time** → Allow time for innovation.
- **Safe to fail** → Encourage calculated risks.
- **Weekly lightning talks** → Share knowledge in short sessions.
- **Brown bag sessions** → Informal learning discussions over lunch.
- **Demo days** → Showcase projects and progress.
- **Mini-conferences** → Internal events to foster learning.

[//]: # (158)

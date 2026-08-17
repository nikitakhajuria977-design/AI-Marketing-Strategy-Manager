# 🤖 AI Marketing Strategy Manager

An AI-powered **multi-agent marketing strategy platform** built using the **OpenAI Agents SDK**.

The system uses multiple specialised AI agents that collaborate to perform market research, competitor analysis, campaign planning, content strategy, campaign analytics, and optimisation.

---

## 📌 Project Overview

Modern marketing teams need to continuously analyse markets, competitors, customers, campaigns, and performance data.

This project addresses this challenge by dividing marketing responsibilities among specialised AI agents. A central **Marketing Manager Agent** receives the user's request and delegates the task to the most appropriate specialist.

The system is designed to provide:

* Market and competitor research
* Marketing campaign planning
* Budget allocation
* Content calendar generation
* Campaign performance analysis
* Marketing optimisation recommendations
* Human approval for high-impact budget decisions

---

## 🎯 Objectives

The main objectives of this project are:

* Automate market and competitor research
* Identify market trends and audience shifts
* Develop data-driven marketing campaigns
* Generate channel-specific content strategies
* Analyse campaign KPIs
* Recommend marketing and budget optimisations
* Demonstrate collaboration between specialised AI agents
* Include human approval for significant budget changes

---

## 🏗️ System Architecture

The project follows a **Manager–Specialist Multi-Agent Architecture**.

```text
                         USER
                           │
                           ▼
                ┌─────────────────────┐
                │  Marketing Manager  │
                │    Orchestrator     │
                └──────────┬──────────┘
                           │
        ┌──────────────────┼──────────────────┐
        ▼                  ▼                  ▼
┌───────────────┐  ┌─────────────────┐  ┌─────────────────┐
│ Market        │  │ Competitor      │  │ Campaign        │
│ Research      │  │ Analysis        │  │ Planner         │
│ Agent         │  │ Agent           │  │ Agent           │
└───────┬───────┘  └────────┬────────┘  └────────┬────────┘
        │                   │                    │
        └───────────────────┼────────────────────┘
                            ▼
                  ┌──────────────────┐
                  │ Content          │
                  │ Strategist Agent │
                  └────────┬─────────┘
                           │
                           ▼
                  ┌──────────────────┐
                  │ Analytics Agent  │
                  └────────┬─────────┘
                           │
                           ▼
                ┌─────────────────────┐
                │ Optimisation        │
                │ Advisor Agent       │
                └──────────┬──────────┘
                           │
                           ▼
                  Final Recommendation
                           │
                           ▼
                    Human Approval
```

This architecture is implemented in the project notebook.

---

## 🧠 AI Agents

The system contains the following specialised agents:

| Agent                         | Responsibility                                        |
| ----------------------------- | ----------------------------------------------------- |
| **Marketing Manager**         | Orchestrates the workflow and delegates tasks         |
| **Market Research Agent**     | Analyses market trends and audience shifts            |
| **Competitor Analysis Agent** | Analyses competitor positioning, pricing and channels |
| **Campaign Planner Agent**    | Creates campaign objectives, channels and budgets     |
| **Content Strategist Agent**  | Creates content strategies and calendars              |
| **Analytics Agent**           | Analyses campaign performance                         |
| **Optimisation Advisor**      | Combines insights and recommends improvements         |

The project defines six specialised agents in addition to the central Marketing Manager.

---

## 🛠️ Tools

The agents use custom Python tools to access marketing-related information and perform specific operations.

### Available Tools

* `get_market_trends()`
* `get_competitor_profile()`
* `calculate_campaign_budget()`
* `get_campaign_performance()`
* `get_current_date()`
* `log_event()`

These tools keep data-access and application functions separate from the reasoning responsibilities of the agents.

---

## 🔄 Agent Handoff

The Marketing Manager identifies the user's requirement and hands the task to a specialised agent.

Examples:

```text
Market trends
      ↓
Market Research Agent

Competitor analysis
      ↓
Competitor Analysis Agent

Campaign planning
      ↓
Campaign Planner Agent

Content calendar
      ↓
Content Strategist Agent

Campaign performance
      ↓
Analytics Agent

Optimisation / next steps
      ↓
Optimisation Advisor
```

The workflow then produces a final recommendation for the user.

---

## 🛡️ Guardrails

The project includes an **input guardrail** that checks whether the user's request is related to:

* Marketing strategy
* Market research
* Campaigns
* Content
* Analytics
* Optimisation

Unrelated requests are blocked before entering the main marketing workflow.

This helps ensure that the specialised system remains focused on its intended purpose.

---

## 📊 Structured Outputs

The project uses **Pydantic models** to produce structured outputs.

Main output models include:

* `CampaignPlan`
* `ContentCalendar`
* `PerformanceReport`
* `OptimizationRecommendation`

This allows the agents to return consistent and predictable results.

---

## 👤 Human-in-the-Loop Approval

The system includes human approval for significant budget changes.

If the proposed budget change exceeds the configured approval threshold, the optimisation agent marks:

```text
human_approval_required = True
```

This provides an additional control layer for high-impact marketing decisions.

---

## 💾 Session Memory

The project uses **SQLite session memory** to maintain relevant context across interactions.

This allows the multi-agent workflow to maintain continuity instead of treating every interaction as completely independent.

---

## 💻 Technologies Used

* Python
* OpenAI Agents SDK
* OpenAI Models
* Pydantic
* SQLite
* Google Colab / Jupyter Notebook

---

## 📁 Project Structure

```text
AI-Marketing-Strategy-Manager/
│
├── Project_2.ipynb
├── README.md
├── requirements.txt
├── architecture.md
├── .gitignore
└── LICENSE
```

---

## ⚙️ Installation

Clone the repository:

```bash
git clone https://github.com/YOUR-USERNAME/AI-Marketing-Strategy-Manager.git
cd AI-Marketing-Strategy-Manager
```

Install the required packages:

```bash
pip install -U openai-agents pydantic
```

The notebook uses the `openai-agents` and `pydantic` packages.

---

## 🔑 API Key Setup

Set your OpenAI API key as an environment variable.

### macOS / Linux

```bash
export OPENAI_API_KEY="your-api-key"
```

### Google Colab

The notebook securely prompts for the API key if it is not already configured.

**Never commit your API key to GitHub.**

---

## 🚀 Running the Project

Open:

```text
Project_2.ipynb
```

Run the notebook cells in order.

The implementation covers:

1. Environment setup
2. Brand context
3. Marketing tools
4. Structured output models
5. Specialised agents
6. Guardrails
7. Marketing Manager orchestration
8. Human approval
9. Session memory
10. End-to-end testing

These stages are defined in the project notebook.

---

## 🏢 Example Business Context

The demonstration uses a fictional fitness-app brand:

```text
Brand: Nimbus Fitness
Industry: Fitness Apps
Monthly Budget: $12,000
Target Audience: Urban professionals aged 25–40
```

The notebook also contains example market trends, competitor information, and campaign performance data for demonstrating the agent workflow.

---

## 📈 Example Workflow

A user could ask:

```text
Create a marketing strategy for our fitness app.
```

The Marketing Manager determines the appropriate workflow and delegates tasks to specialised agents.

The resulting workflow can include:

```text
Market Research
       ↓
Competitor Analysis
       ↓
Campaign Planning
       ↓
Content Strategy
       ↓
Performance Analysis
       ↓
Optimisation Recommendation
       ↓
Human Approval
```

---

## 🌟 Key Features

* 🤖 Multi-agent AI architecture
* 🔀 Agent handoffs
* 🧠 Specialised marketing agents
* 🛠️ Custom function tools
* 📊 Structured outputs
* 🛡️ Input guardrails
* 💾 SQLite session memory
* 👤 Human-in-the-loop approval
* 💰 Campaign budget analysis
* 📈 Campaign performance analysis
* 🎯 Marketing optimisation

---

## 🎓 Project Purpose

This project was developed as an **OpenAI Agents SDK Capstone Project** to demonstrate how multiple specialised AI agents can collaborate to solve a complex business problem.

It demonstrates practical concepts including:

* Agent orchestration
* Agent handoffs
* Tool integration
* Structured outputs
* Guardrails
* Memory
* Human-in-the-loop workflows

---

## 🔮 Future Improvements

Possible future enhancements include:

* Real-time market research APIs
* Live competitor data
* Social media API integration
* Real advertising platform integration
* Advanced analytics dashboards
* Persistent production database
* Web-based user interface
* Automated campaign execution
* Real-time campaign monitoring

---

## 👩‍💻 Author

**Nikita Sharma**

B.Tech Computer Science Engineering
AI/ML & Generative AI Enthusiast

---

## ⭐ Acknowledgements

Built using the **OpenAI Agents SDK** and Python ecosystem.

If you find this project useful, consider giving the repository a ⭐.

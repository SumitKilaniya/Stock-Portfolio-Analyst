# 📈 Stock Portfolio Analyst

An AI-powered **Stock Portfolio Analyst** built with **Agno** and **Streamlit**.

The application lets users enter their stock holdings and generates an AI-assisted portfolio analysis covering **portfolio valuation, profit & loss, allocation, concentration, risk signals, market context, and potential rebalancing ideas**.

> ⚠️ **Disclaimer:** This project is for educational and informational purposes only. It does not provide financial, investment, tax, or trading advice.

---

## 🚀 Features

### 📊 Portfolio Editor

Enter and manage your portfolio through a spreadsheet-style interface.

For each position, provide:

* **Ticker symbol**
* **Number of shares**
* **Average purchase price**

Holdings can be edited directly before running an analysis.

### 📈 Market Data

The application retrieves market information for the selected stocks, including:

* Current/available market price
* Company fundamentals
* Analyst ratings
* Relevant financial information
* Recent market news

Market data availability depends on the underlying data provider and may be delayed or incomplete.

### 🌐 Web-Based Market Context

The agent can search the web for additional market context when information available through the primary market-data source is insufficient.

This helps provide broader context around:

* Recent company developments
* Market-moving events
* Earnings-related news
* Industry developments
* Major company announcements

### 🧮 Portfolio Calculations

A dedicated calculator tool is used for numerical operations such as:

* Total portfolio value
* Position value
* Portfolio allocation
* Unrealized profit/loss
* Profit/loss percentage
* Position weights
* Portfolio concentration

This separates numerical calculations from the language model's reasoning and helps reduce calculation errors.

### 🧠 AI-Powered Analysis

The AI agent evaluates the portfolio and identifies potential areas of concern, including:

* High concentration in individual positions
* Sector concentration
* Large unrealized losses
* Potentially stretched valuations
* Weak analyst sentiment
* Negative company-specific developments
* Portfolio diversification concerns

The agent then provides potential rebalancing considerations based on the available information.

### 📝 Structured Portfolio Report

The analysis is presented in a structured format containing:

1. **Portfolio overview**
2. **Holdings breakdown**
3. **Current valuation**
4. **Profit & loss**
5. **Portfolio allocation**
6. **Concentration analysis**
7. **Risk flags**
8. **Market/news context**
9. **Potential rebalancing ideas**

---

## 🛠️ Technology Stack

| Component          | Technology                |
| ------------------ | ------------------------- |
| AI Agent Framework | Agno                      |
| LLM Inference      | Configurable LLM provider |
| Market Data        | YFinance                  |
| Web Search         | DuckDuckGo                |
| Calculations       | Calculator Tools          |
| Frontend           | Streamlit                 |
| Language           | Python                    |

The architecture is intentionally modular so that the model provider, market-data source, search provider, and agent configuration can be changed independently.

---

## 🏗️ High-Level Architecture

```text
                     ┌─────────────────────┐
                     │      Streamlit      │
                     │     User Interface  │
                     └──────────┬──────────┘
                                │
                                ▼
                     ┌─────────────────────┐
                     │    Portfolio Agent  │
                     │       (Agno)        │
                     └──────────┬──────────┘
                                │
              ┌─────────────────┼─────────────────┐
              │                 │                 │
              ▼                 ▼                 ▼
       ┌─────────────┐   ┌─────────────┐   ┌─────────────┐
       │  Market Data│   │ Web Search  │   │ Calculator  │
       │  /YFinance  │   │   Context   │   │    Tools    │
       └──────┬──────┘   └──────┬──────┘   └──────┬──────┘
              │                 │                 │
              └─────────────────┼─────────────────┘
                                ▼
                     ┌─────────────────────┐
                     │ Portfolio Analysis  │
                     │ & Risk Assessment   │
                     └──────────┬──────────┘
                                │
                                ▼
                     ┌─────────────────────┐
                     │ Structured Report   │
                     └─────────────────────┘
```

---

## 📋 Requirements

Before running the project, make sure you have:

* Python **3.10 or newer**
* Internet connectivity
* An API key for the configured LLM provider
* Required Python dependencies installed

---

## ⚡ Installation

Clone or download the project and navigate to its directory:

```bash
cd stock_portfolio_analyst
```

Create and activate a virtual environment:

```bash
python -m venv .venv
```

### macOS / Linux

```bash
source .venv/bin/activate
```

### Windows

```bash
.venv\Scripts\activate
```

Install the dependencies:

```bash
pip install -r requirements.txt
```

---

## 🔐 Environment Configuration

Create a local `.env` file based on the provided environment template:

```bash
cp .env.example .env
```

Then add your **own API credentials** to the `.env` file.

Example:

```env
LLM_API_KEY=your_api_key_here
```

> 🔒 **Security:** Never commit `.env`, API keys, access tokens, passwords, or other secrets to GitHub. Make sure `.env` is included in your `.gitignore`.

For example:

```gitignore
.env
.env.*
!.env.example
```

The repository should contain only placeholder values such as:

```env
LLM_API_KEY=
```

---

## ▶️ Running the Application

Start the Streamlit application:

```bash
streamlit run main.py
```

Streamlit will provide a local address where the application can be opened in your browser.

---

## 💡 How to Use

### 1. Add Your Holdings

Enter one row for each portfolio position:

```text
Ticker        Shares        Avg Buy Price
AAPL          10            180
MSFT          5             400
NVDA          8             120
```

### 2. Define Your Analysis Focus

You can optionally provide a specific question, for example:

```text
Assess my technology concentration risk.
```

or:

```text
Which position contributes most to my portfolio risk?
```

or:

```text
Analyze my portfolio diversification.
```

### 3. Run the Analysis

Click **Analyze Portfolio**.

The agent will gather the required information, perform portfolio calculations, evaluate risks, and generate a structured report.

### 4. Review the Results

The final report includes:

* Position-level valuation
* Unrealized P/L
* Portfolio allocation
* Concentration analysis
* Risk indicators
* Market context
* Potential rebalancing considerations

---

## 🧠 Agent Workflow

The portfolio analyst follows a multi-step workflow:

### Step 1 — Understand the Portfolio

The agent reads the user's holdings and identifies the individual positions.

### Step 2 — Gather Market Data

For each ticker, the agent retrieves available:

* Price information
* Company information
* Fundamentals
* Analyst data
* Recent news

### Step 3 — Perform Calculations

The calculator is used to determine:

```text
Position Value
Portfolio Value
Position Weight
Cost Basis
Unrealized P/L
P/L %
```

### Step 4 — Analyze Portfolio Structure

The agent evaluates:

* Individual position concentration
* Sector exposure
* Diversification
* Large winners/losers
* Portfolio-level risk signals

### Step 5 — Gather Additional Context

Web search can be used to find relevant developments that may not be available through the primary market-data source.

### Step 6 — Generate the Report

The agent combines the numerical results and qualitative context into a structured portfolio review.

---

## 📊 Example Analysis

A portfolio might be summarized like:

```text
Portfolio Value:        $25,430
Total Cost Basis:       $21,800
Unrealized P/L:         +$3,630
Portfolio Return:       +16.65%

Largest Position:       NVDA
Largest Sector:         Technology

Risk Flags:
• High technology concentration
• One position represents a large portion of total portfolio value
• Portfolio has limited exposure outside growth-oriented equities

Potential Considerations:
• Review position sizing
• Evaluate sector diversification
• Consider whether current allocations match the intended risk level
```

Numbers above are illustrative only.

---

## 🔧 Project Structure

A typical project structure can look like:

```text
stock_portfolio_analyst/
│
├── main.py
├── requirements.txt
├── .env.example
├── .gitignore
├── README.md
│
├── agents/
│   └── portfolio_agent.py
│
├── tools/
│   ├── market_data.py
│   ├── calculator.py
│   └── web_search.py
│
└── utils/
    └── portfolio.py
```

The exact structure may vary depending on the implementation.

---

## 🔒 Security & Privacy

This project is designed to keep credentials separate from source code.

### Never commit:

* API keys
* `.env` files
* Authentication tokens
* Passwords
* Private credentials
* Personal financial records
* Production secrets

### Recommended practice

Use environment variables for secrets:

```env
LLM_API_KEY=your_api_key_here
```

Keep the actual `.env` file local and commit only `.env.example`.

If deploying the application, configure secrets through the deployment platform's **secret/environment-variable manager** rather than placing them inside the source code.

---

## ⚠️ Data Limitations

Financial market data is not guaranteed to be real-time.

Depending on the provider, information may be:

* Delayed
* Temporarily unavailable
* Rate-limited
* Incomplete
* Incorrect in rare cases

If a ticker fails to load, retry the analysis or verify the ticker symbol.

AI-generated analysis can also contain errors. Always independently verify important financial information.

---

## ⚠️ Financial Disclaimer

This application is an **educational AI project**.

It does not constitute:

* Financial advice
* Investment advice
* Trading advice
* Tax advice
* Legal advice

Portfolio analysis and rebalancing suggestions are generated from available data and AI reasoning and should **not be treated as personalized investment recommendations**.

Always perform your own research and consult a qualified financial professional when appropriate.

---

## 🚀 Future Improvements

Potential future additions include:

* 📉 Historical portfolio performance
* 📊 Interactive allocation charts
* 📈 Benchmark comparison
* 🧮 Risk-adjusted return metrics
* 📐 Sharpe ratio and volatility analysis
* 🔄 Portfolio rebalancing simulator
* 🎯 Target allocation support
* 🏭 Advanced sector analysis
* 🌎 Multi-market support
* 💰 Dividend analysis
* 📅 Earnings-calendar integration
* 📰 News sentiment analysis
* 🤖 Multi-agent portfolio research
* 💾 Portfolio persistence
* 🔐 User authentication
* 📱 Responsive mobile interface

---

## ⭐ Why This Project?

This project demonstrates how **AI agents can combine LLM reasoning with external tools and structured financial data**.

Instead of asking an LLM to guess portfolio numbers, the system gives the agent access to specialized tools for:

```text
Market Data
     ↓
Web Research
     ↓
Numerical Calculations
     ↓
Portfolio Analysis
     ↓
Risk Identification
     ↓
Structured AI Report
```

This makes the project a practical example of **tool-using AI agents**, rather than a simple chatbot.

---

## 📌 Key Concepts Demonstrated

This project showcases several important concepts in modern AI engineering:

* AI Agents
* Tool Calling
* Structured Outputs
* LLM Reasoning
* External Data Integration
* Web Search
* Financial Data APIs
* Numerical Tool Usage
* Prompt Engineering
* Agent Workflows
* Streamlit Applications
* Environment-Based Configuration
* Modular AI Architecture

---

## 📄 License

Add an appropriate open-source license before publishing the project publicly, such as MIT, Apache-2.0, or another license that matches your intended usage.

---

### 🔐 Repository Safety Checklist

Before pushing this project to a public repository:

* [ ] Remove all real API keys
* [ ] Remove `.env` from Git tracking
* [ ] Keep `.env.example` as a template
* [ ] Remove private URLs or internal endpoints
* [ ] Remove personal portfolio/financial information
* [ ] Check Git history for accidentally committed secrets
* [ ] Verify screenshots do not contain sensitive information
* [ ] Verify logs do not expose credentials
* [ ] Add an appropriate license
* [ ] Review third-party package licenses

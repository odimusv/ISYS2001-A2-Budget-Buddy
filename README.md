# 📊 20732370 Vince Sumido

** Budget Buddy – Smart Finance Assistant

<!-- BADGES:START -->
[![curtin](https://img.shields.io/badge/-curtin-f57c00?style=flat-square)](https://github.com/topics/curtin) [![ai-assistant](https://img.shields.io/badge/-ai--assistant-blue?style=flat-square)](https://github.com/topics/ai-assistant) [![chatbot](https://img.shields.io/badge/-chatbot-blue?style=flat-square)](https://github.com/topics/chatbot) [![finance](https://img.shields.io/badge/-finance-blue?style=flat-square)](https://github.com/topics/finance) [![financial-tools](https://img.shields.io/badge/-financial--tools-blue?style=flat-square)](https://github.com/topics/financial-tools) [![budgeting](https://img.shields.io/badge/-budgeting-4caf50?style=flat-square)](https://github.com/topics/budgeting) [![gradio](https://img.shields.io/badge/-gradio-blue?style=flat-square)](https://github.com/topics/gradio) [![jupyter-notebook](https://img.shields.io/badge/-jupyter--notebook-blue?style=flat-square)](https://github.com/topics/jupyter-notebook) [![python](https://img.shields.io/badge/-python-3776ab?style=flat-square)](https://github.com/topics/python) [![rag](https://img.shields.io/badge/-rag-blue?style=flat-square)](https://github.com/topics/rag)
<!-- BADGES:END -->

Welcome to my project repository for the **ISYS2001 Final Programming Project**.

This project is called **Budget Buddy**, a Smart Finance Assistant designed to help students and young adults in Australia understand their spending habits, identify budgeting patterns, and receive practical money management suggestions.

---

## 📖 Project Overview

**Budget Buddy** is a personal finance assistant built using:

- Python in Google Colab
- [hands-on-ai](https://pypi.org/project/hands-on-ai/) for chat, RAG, and agent tool features
- [Gradio](https://www.gradio.app/) for the app interface
- pandas for loading, cleaning, and analysing transaction data

The goal of Budget Buddy is to make budgeting easier and less overwhelming. Users can upload a transaction CSV file and receive clear summaries, spending insights, and practical budgeting recommendations.

Budget Buddy includes:

- **Chatbot:** a friendly finance-focused assistant
- **RAG retrieval:** a small budgeting knowledge base
- **Agent tool:** a custom savings goal calculator
- **Gradio UI:** a simple web interface tying everything together
- **Tests:** assert-based tests covering normal data, edge cases, and errors

Budget Buddy provides budgeting education and general money management support only. It does **not** provide personal financial advice.

---

## 🧠 Problem Being Solved

Many students and young adults struggle to understand where their money is going. Transaction data can be confusing, especially when it includes refunds, subscriptions, transport costs, eating out, entertainment, and one-off purchases.

Budget Buddy helps solve this problem by turning raw transaction data into easy-to-understand financial summaries.

It helps users answer questions such as:

- How much did I spend overall?
- How much did refunds reduce my spending?
- What was my net cash impact?
- Which category did I spend the most on?
- How much of my spending was flexible or discretionary?
- What spending areas could I reduce first?
- How long will it take me to reach a savings goal?
- What small budgeting actions can I take next?

---

## ✅ Main Features

### 1. Transaction Data Cleaning

Budget Buddy can load transaction data from a CSV file or a pandas DataFrame.

It handles:

- Dollar signs in amounts
- Commas in large amounts
- Negative refund amounts
- Missing values
- Invalid dates
- Invalid amount formats
- Blank rows
- Missing required columns
- Zero-dollar transactions

Required CSV columns:

```text
Date, Amount, Category, Description
```

Example transaction data:

```csv
Date,Amount,Category,Description
2026-05-01,$14.50,Food,Grill'd Perth Lunch
2026-05-02,$89.99,Entertainment,Steam Game Purchase
2026-05-03,$45.20,Groceries,Coles Supermarket
2026-05-04,$120.00,Transport,SmartRider Top Up
2026-05-05,-$25.00,Refund,Amazon Refund
2026-05-06,$9.90,Subscriptions,Spotify Premium
```

---

### 2. Spending Analysis

Budget Buddy analyses cleaned transaction data and calculates:

- Total spending
- Total refunds
- Net cash impact
- Category totals
- Category percentages
- Transaction counts
- Average transaction size
- Top spending category
- Largest transaction
- Discretionary spending
- Practical business-focused insights

---

### 3. Financial Recommendations

Budget Buddy generates professional but easy-to-understand recommendations based on the spending analysis.

Recommendations include:

- Spending observations
- Category-specific savings opportunities
- Flexible spending suggestions
- Weekly budgeting actions
- Subscription review prompts
- A realistic action plan

The recommendations are written in a friendly, encouraging, and non-judgemental tone.

---

### 4. Finance Chatbot

Budget Buddy includes a finance-focused chatbot that can:

- Explain spending patterns
- Answer budgeting questions
- Use transaction analysis context
- Suggest realistic savings strategies
- Encourage better money habits

The chatbot is designed to be supportive and clear. It does not pretend to be a licensed financial adviser.

---

### 5. RAG Knowledge Base

Budget Buddy includes a small financial knowledge base using retrieval-augmented generation.

The knowledge base includes:

- Budgeting basics
- Spending category guidance
- Savings strategies
- A latest transaction summary if uploaded analysis data exists

If RAG indexing is unavailable, Budget Buddy uses a keyword-search fallback so the app can still answer questions.

---

### 6. Custom Savings Goal Calculator

Budget Buddy includes a custom savings calculator that asks for:

- Current savings
- Monthly contribution
- Target amount

It calculates:

- Remaining amount needed
- Months required to reach the goal
- Approximate years required
- User-friendly encouragement

The calculator handles:

- Dollar signs
- Commas
- Invalid values
- Negative values
- Zero monthly contributions
- Cases where the savings goal has already been reached

---

### 7. Gradio Interface

Budget Buddy uses a Gradio interface with clear tabs:

1. **Upload & Analyse CSV**
2. **Budget Buddy Chat**
3. **Financial Knowledge Base**
4. **Savings Goal Calculator**
5. **About & Safety**

The interface is designed to be simple enough for non-technical users.

---

## 📂 Suggested Repo Layout

You may adapt this structure or create your own. Clarity and organisation are graded in the rubric.

```text
/README.md               ← this file
/assignment.pdf          ← official assignment specification
/starter_notebook.ipynb  ← main Google Colab notebook
/example_diary.md        ← sample Developer’s Diary entries
/data/                   ← sample transaction CSV files
/tests/                  ← test scripts or assert-based tests
/ai-conversations/       ← weekly AI Evidence Packages
/docs/                   ← pseudocode, design notes, planning docs
```

---

## 🚀 Getting Started

1. Open `starter_notebook.ipynb` in Google Colab.
2. Follow the six-step methodology:
   1. Understand the problem
   2. Identify inputs and outputs
   3. Work the problem by hand
   4. Write pseudocode
   5. Convert to Python
   6. Test with a variety of data
3. Load the sample transaction dataset.
4. Run the data cleaning function.
5. Run the spending analysis function.
6. Generate financial recommendations.
7. Set up the RAG knowledge base.
8. Test the savings calculator.
9. Launch the Gradio interface.
10. Run the testing section to confirm the system works correctly.
11. Add at least one meaningful GitHub commit per week from Weeks 8–12.
12. Document AI use in the Developer’s Diary.

---

## 🧪 Testing

Budget Buddy includes assert-based tests for the main project workflow.

The tests cover:

- Normal transaction data
- Refund handling
- Zero amount handling
- Missing values
- Invalid amount formats
- Invalid dates
- Missing columns
- High-spending scenarios
- Category totals
- Category percentages
- Top spending category
- Largest transaction
- Recommendation output
- RAG retrieval
- Savings calculator inputs
- Integration workflow
- Error handling

Testing shows that the project works with both normal data and edge cases.

---

## ✅ Submission Requirements

The final submission should include:

- A Google Colab notebook with the full Budget Buddy implementation
- GitHub repository with:
  - Notebook
  - README
  - Developer’s Diary
  - Weekly AI Evidence Packages from Weeks 8–12
  - Meaningful commit history
- Developer’s Diary entries that include:
  - **Artifact:** screenshot, prompt, or snippet of AI use
  - **Context:** what I was trying to achieve
  - **Reflection:** what worked, what did not work, and what I learned

---

## 🤖 AI Collaboration

AI was used as a coding and planning assistant throughout the project.

Examples of AI support include:

- Improving Python functions
- Designing the chatbot system prompt
- Creating test cases
- Planning the Gradio interface
- Debugging output formatting
- Creating RAG and agent tool logic
- Explaining code structure
- Improving README documentation

AI use is documented in the Developer’s Diary with screenshots, prompts, and reflections.

---

## 📊 Assessment Criteria Alignment

### Functionality – 30%

Budget Buddy includes:

- Transaction CSV upload
- Data cleaning
- Spending analysis
- Finance chatbot
- RAG retrieval
- Custom savings calculator tool
- Gradio interface

### Testing & Debugging – 20%

The project includes tests for:

- Normal cases
- Edge cases
- Invalid inputs
- Error handling
- Full workflow integration

### AI Collaboration & Progress – 20%

AI use is documented through:

- Developer’s Diary entries
- Evidence screenshots
- Prompt examples
- Reflection on AI-generated improvements
- Weekly commits

### Business Relevance – 15%

Budget Buddy solves a realistic finance problem for students and young adults by helping them understand and manage spending.

### Clarity & Reflection – 15%

The repository is organised with:

- Clear README documentation
- A structured notebook
- Testing section
- AI evidence
- Project explanation
- Safety disclaimer

For the full rubric, see `assignment.pdf`.

---

## ⚠️ Important Disclaimer

Budget Buddy provides budgeting education and general money management support only.

It is **not** a licensed financial adviser, accountant, lawyer, investment adviser, tax professional, or debt counsellor.

For serious debt, tax, investing, financial hardship, legal, or personal financial decisions, users should speak with a qualified professional or relevant Australian support service.

---

## 📚 Resources

- **hands-on-ai Package:** [GitHub Repository](https://github.com/michael-borck/hands-on-ai)
- **hands-on-ai Documentation:** [DeepWiki Guide](https://deepwiki.com/michael-borck/hands-on-ai)
- **For AI Assistants:** Share [this LLM context file](https://github.com/michael-borck/hands-on-ai/blob/main/LLM.txt) with ChatGPT/Claude/Copilot for better code suggestions
- **Gradio Documentation:** [https://www.gradio.app/](https://www.gradio.app/)
- **pandas Documentation:** [https://pandas.pydata.org/](https://pandas.pydata.org/)

---

## 💡 Tips

- Keep commits small and descriptive.
- Use AI as a coding partner, not a replacement for understanding.
- Keep AI evidence clear and organised.
- Test with both normal and invalid transaction data.
- Remember: **undocumented AI use = misconduct**.

Good luck, and have fun building Budget Buddy! 🎉

---

## 📜 License

The template code in this repository is licensed under the MIT License. See the [LICENSE](LICENSE) file for more details.

My own project work for Budget Buddy is submitted as part of the ISYS2001 Final Programming Project.

📓 Developer's Diary – AI Collaboration Guide

This file shows sample entries for your **Developer's Diary**. You must document your AI collaboration throughout the project development. Each entry should have:
- **Artifact**: a screenshot, GIF, or snippet of your AI interaction
- **Context**: one-sentence description of your goal
- **Reflection**: analysis of what happened, what you learned, and how you improved the solution

**Key Principle**: You're directing AI like a junior developer - always review, critique, and improve their suggestions.

**NOTE: ** I started this project late, so the entries below are written as honest catch-up reflections rather than pretending I completed weekly work earlier. I have not backdated commits. The purpose of this diary is to document how I used AI during the actual development process, how I reviewed AI suggestions, and how I improved the project.


## Foundation Skills Examples

### Entry 1 – Problem Framing and Scope
**Artifact:** ![entry1-problemframing](AI-CONVERSATIONS/entry1-problemframing.png)

**Context:** I needed to turn my general Budget Buddy idea into a clear finance problem that was realistic for the assignment


**My Initial Prompt:** "I'm building a Smart Finance Assistant called Budget Buddy for students and young adults. The problem is that many do not understand where their money goes. Help me restate the problem in plain English and identify the core user needs, but keep the scope realistic for a Python/Colab/Gradio assignment."

**AI Response Summary:** AI suggested that Budget Buddy should focus on uploaded transaction data, summarising category spending, identifying the largest spending areas, and giving simple budgeting advice.


**My Critique/Improvement:** I decided not to include bank logins, live account syncing, or complex investment tracking because they would make the project too broad. I narrowed the project to CSV transaction analysis, practical spending advice, a small RAG guide, and a savings-goal tool.

**Reflection:** This helped me learn that scoping is an important programming decision. AI gave me several feature ideas, but I had to choose a realistic set that matched the assignment and could be tested properly.


---

### Entry 2 – CSV Cleaning and Spending Analysis Code
**Artifact:** ![entry2-csvcleaninganalysis.png](AI-CONVERSATIONS/entry2-csvcleaninganalysis.png)

**Context:** I needed help creating robust Python functions for cleaning transaction data and analysing spending.


**My Initial Prompt:** Write a Python function for Budget Buddy that loads a CSV or DataFrame with Date, Amount, Category, and Description columns. It should handle dollar signs, commas, AUD text, bracketed negative amounts, refunds, invalid dates, and missing values. Use clear business-focused variable names and helpful error messages because this is for a student finance assistant.

**AI Response Summary:** AI suggested using pandas to load the data, clean the `Amount` column, convert dates, normalise categories, and group transactions by category.

**My Critique/Improvement:** The first version was too compact, so I separated the work into smaller functions: one for parsing amounts, one for loading and cleaning data, one for analysis, and one for building the report. I also added better error messages for missing columns and empty CSV files.

**Reflection:** AI was useful for structure, but I still had to make the code readable and testable. I learned that finance data can be messy, so error handling is part of the business value, not just a technical extra.

---

### Entry 3 – Realistic Sample Transaction Data
**Artifact:** ![entry3-sample-transactions](AI-CONVERSATIONS/entry3-sample-transactions1.png)


**Context:** I needed realistic transaction data so I could test Budget Buddy before using a full uploaded CSV.

**My Prompt:** "I'm building a Smart Finance Assistant called Budget Buddy for students and young adults in Australia. Create a small pandas sample transaction dataset with Date, Amount, Category, and Description columns. Include Australian-style businesses, dollar signs in amounts, different spending categories, and at least one negative refund amount so I can test data cleaning."

**AI Response Summary:** AI suggested a simple sample transaction structure using categories like Groceries, Transport, Entertainment, Coffee, and Refund. It included string amounts such as `$45.50` and a negative refund amount so the cleaning function could be tested properly.

**My Critique/Improvement:** I kept the dataset small because it was only for early testing, not final analysis. I made sure the data included messy but realistic features such as dollar signs and a negative refund because those are the kinds of issues that the later cleaning function needed to handle.

**Result:** I created `df_sample` from the sample transaction dictionary and used it to test the cleaning and analysis functions in the notebook.

**Reflection:** This helped me see that test data should not be too perfect. By adding a refund and dollar-formatted amounts early, I could check whether my later code handled real-world transaction data instead of only working on clean examples.


---

### Entry 4 – Data Loading and Cleaning Function
**Artifact:** ![entry4-data-loading-cleaning](AI-CONVERSATIONS/entry4-data-loading-cleaning.png)

**Context:** I needed a robust function to load and clean transaction data before any analysis could happen.

**My Prompt:** "Create a Python function for Budget Buddy called `load_and_clean_transaction_data(file_path)`. It should load CSV transaction data or accept a pandas DataFrame with Date, Amount, Category, and Description columns. Handle dollar signs, commas, missing values, invalid dates, blank rows, refunds, and data validation. Include clear business-focused error messages suitable for a student finance assistant."

**AI Response Summary:** AI suggested using pandas to read the CSV, check for required columns, clean the Amount column, convert dates, fill blank categories and descriptions, and raise clear errors for missing or invalid data.

**My Critique/Improvement:** I improved the suggestion by allowing the function to accept both file paths and DataFrames, because the notebook tests use DataFrames as well as CSV files. I also added row numbers in error messages so users can find the problem in their CSV more easily. I added `Transaction_Type` and `Month` columns to support later analysis.

**Result:** The final function loads transaction data, validates required columns, converts amounts and dates, handles missing text fields, identifies expenses and refunds, and returns a clean DataFrame ready for analysis.

**Reflection:** AI gave me a useful structure, but I had to think about the user experience. Clear error messages are important because Budget Buddy is meant for non-technical users who may not understand pandas errors.


---

### Entry 5 – Spending Analysis Function
**Artifact:** ![entry5-spending-analysis](AI-CONVERSATIONS/entry5-spending-analysis.png)

**Context:** I needed to turn cleaned transactions into useful spending summaries and business insights.

**My Prompt:** "Create a Python function called `analyze_spending_patterns(df)` for Budget Buddy. It should analyse spending by category, calculate total spending, refunds, net spending, category totals, transaction counts, average transaction size, percentages, top spending category, largest transaction, discretionary spending, and practical business insights. Format the result as a dictionary that can be used by a report generator and Gradio UI."

**AI Response Summary:** AI suggested grouping transactions by category, calculating totals and percentages, identifying the top category, and returning analysis results in a dictionary.

**My Critique/Improvement:** I changed the logic so positive expenses and negative refunds are handled separately. This prevents refunds from hiding the user’s real spending patterns. I also added a zero-spending case, discretionary categories, a date range, and a list of written business insights.

**Result:** The function now returns a complete analysis dictionary with category summaries, refund information, top spending areas, discretionary spending, and user-friendly insight text.

**Reflection:** This entry helped me learn that financial analysis is not just about calculating totals. The way refunds and categories are treated changes the meaning of the results, so I had to review the AI logic carefully.

---


### Entry 6 – Business Insights and Recommendations Report
**Artifact:** ![entry6-business-recommendations](AI-CONVERSATIONS/entry6-business-recommendations.png)


**Context:** I needed to convert the analysis dictionary into practical advice that a user could understand.

**My Prompt:** "Based on spending analysis data for Budget Buddy, create a Python function called `generate_financial_recommendations(analysis_data)`. It should generate professional financial recommendations for a personal finance app user. Include total spending, refunds, net cash impact, top spending category, category-specific savings opportunities, spending pattern observations, an action plan, and a short disclaimer that this is budgeting education, not personal financial advice."

**AI Response Summary:** AI suggested creating a formatted report with a spending summary, key observations, and action recommendations based on the largest categories.

**My Critique/Improvement:** I made the recommendations more specific by adding different advice for coffee, dining, entertainment, groceries, transport, and utilities. I also added a no-positive-spending branch so the report does not break when the user uploads mostly refunds or zero-value transactions.

**Result:** The final report uses clear Markdown headings, dollar formatting, realistic 5–10% saving suggestions, and a practical next step for the user.

**Reflection:** AI was useful for producing professional wording, but I had to make the recommendations match the actual data structure. This showed me that business reports need both correct numbers and language that feels useful to the end user.

---


### Entry 7 – Financial Advice Chatbot Personality
**Artifact:** ![entry7-finance-chatbot](AI-CONVERSATIONS/entry7-finance-chatbot.png)

**Context:** I wanted Budget Buddy to answer user questions in a friendly but responsible finance-focused style.

**My Prompt:** "Help me create a system prompt for a friendly, professional financial advisor chatbot called Budget Buddy. It should help students and young adults in Australia understand their spending, give practical budgeting suggestions based on transaction analysis, be encouraging and non-judgemental, avoid pretending to be a licensed financial adviser, and suggest professional help for serious debt, tax, investing, or hardship issues."

**AI Response Summary:** AI suggested a chatbot personality that explains spending patterns simply, gives realistic budgeting advice, focuses on small habit changes, and avoids giving formal financial advice.

**My Critique/Improvement:** I added a fallback response in case the `hands_on_ai` chat service fails, so the app still gives a useful budgeting suggestion instead of crashing. I also kept the chatbot advice focused on categories like coffee, dining, entertainment, and savings goals so it stays aligned with the project.

**Result:** The final `create_finance_chat_personality()` function creates a Budget Buddy assistant, attaches it to `chat.say`, accepts optional analysis context, and returns a friendly fallback if the AI service is unavailable.

**Reflection:** This helped me understand that AI personality design is part of software design. The chatbot needed boundaries, tone, and safety limits, not just technical connection code.

---






## AI Collaboration Best Practices I've Learned

### 🎯 Effective Prompting Strategies
1. **Always provide business context**: "I'm building a finance assistant for..."
2. **Specify data structure**: "My CSV has columns X, Y, Z with these data types..."  
3. **Request professional formatting**: "Format output for business presentation"
4. **Ask for comments**: "Include clear comments explaining the business logic"

### 🤔 Critique Questions I Always Ask
- "Does this handle edge cases like negative amounts or missing data?"
- "Are the variable names clear for a business context?"
- "How would I explain this code to a non-technical manager?"
- "What assumptions is this code making about my data?"

### 🔄 Iterative Improvement Process
1. **Get basic working code** from AI
2. **Test with real data** and find issues  
3. **Ask AI to fix specific problems** with context
4. **Simplify complex solutions** for maintainability
5. **Add business-appropriate formatting** and error handling

### 📊 Business Value Focus
- Always connect code back to business decisions
- Format outputs for non-technical users
- Include actionable insights, not just data summaries
- Consider the end user's needs and context

---

## 📝 Documentation Template for Your Entries

Use this format for consistent diary entries:

```markdown
### Entry [Number] – [Descriptive Title]
**Artifact:** [Screenshot/code snippet/GIF of AI interaction]

**Context:** [One sentence: what you were trying to achieve]

**My Prompt:** "[Your exact prompt to AI]"

**AI Response Summary:** [Brief description of what AI provided]

**My Critique/Improvement:** [How you modified or improved the AI's suggestion]

**Result:** [What you ended up with and why it's better]

**Reflection:** [What you learned about AI collaboration, business programming, or problem-solving]
```

---

✅ **Remember**: Document your AI collaboration throughout your project development. Each entry should show learning and improvement, not just successful interactions. Show how you direct AI like a junior developer to create business-appropriate solutions.


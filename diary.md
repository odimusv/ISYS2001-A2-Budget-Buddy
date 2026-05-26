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

















d specific recommendations like "Consider meal planning to reduce dining expenses" and "Coffee purchases represent 8% of total spending - consider brewing at home."

**Reflection:** When I include business context and specify the audience (personal finance app users), AI generates much more relevant and professional output. I learned that framing requests in business terms gets business-quality responses. Now I always think about who will read the output and what decisions they need to make.

---

### Entry 4 – Data Quality and Edge Cases
**Artifact:** Screenshot of debugging session with Claude about handling messy CSV data.

**Context:** My CSV had negative amounts (refunds) and missing values that broke my calculations.

**My Problem:** "My spending analysis is giving wrong totals because some amounts are negative (refunds) and some cells are empty."

**AI Solution:** Helped me add data validation:
```python
# Handle refunds and missing data appropriately
df_clean = df.dropna(subset=['Amount_Clean'])
positive_spending = df_clean[df_clean['Amount_Clean'] > 0]
refunds = df_clean[df_clean['Amount_Clean'] < 0]
```

**Reflection:** AI helped me think about real-world data issues I hadn't considered. I learned that business data is always messy and I need to ask AI specifically about edge cases like refunds, missing values, and invalid entries. This makes my finance assistant more robust for actual use.

---

## Advanced Integration Examples

### Entry 5 – Combining Multiple AI Tools
**Artifact:** Screenshot showing integration of hands-on-ai chat with pandas analysis.

**Context:** I wanted to create a chatbot that could answer questions about spending data.

**My Approach:** Used AI to help me combine CSV analysis with hands-on-ai chat functionality.

**Key Learning:** AI helped me structure the integration, but I had to understand the business logic to make it useful. The chatbot needed to understand financial concepts, not just execute code.

**Reflection:** Integrating multiple technologies requires understanding how each piece serves the business purpose. AI can generate technical integration code, but I need to guide it toward business value.

---

### Entry 6 – Professional Error Handling
**Artifact:** Code snippet showing error handling for file uploads.

**Context:** I needed my Gradio interface to handle bad CSV files gracefully.

**AI Suggestion:** Generated try/catch blocks with business-appropriate error messages:
```python
try:
    df = pd.read_csv(file.name)
    # Analysis code...
except FileNotFoundError:
    return "Please upload a valid CSV file."
except pd.errors.EmptyDataError:
    return "The uploaded file appears to be empty. Please check your data."
```

**Reflection:** AI helped me think about user experience, not just technical functionality. Good error messages help users understand what went wrong and how to fix it. This is crucial for business applications.

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


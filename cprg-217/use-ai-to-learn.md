## How to Effectively Use AI to Learn Coding

## Without Fooling Yourself

---

### Why This Matters
- AI can speed you up **and** make you worse (if you outsource thinking)
- Your goal in school: **build skill**, not just submit assignments 
- You don't want to stagnate by trading out hard skills for quick answers.
- Treat AI like a **coach**, not a **ghostwriter**

---

### The Simple Rule (Non‑Negotiable)
- **You must understand every line of code you submit**
  - whether it comes from **AI**, **the internet**, or **a classmate**
- If you can’t explain it:
  - you can’t debug it
  - you can’t extend it
  - you don’t really “**have**” the skill

---

### What “Understand Every Line” Means
- You can explain each line’s purpose in plain English
- You can predict what happens if you:
  - remove it
  - change an input
  - change an argument passed to a function
- You know "Gotchas" of each line
- You can write a small test case to verify it

---

### Research Insight
- A study from Anthropic analyzed how different AI usage patterns relate to performance
- Key takeaway: **how** you use AI matters more than **whether** you use it
- We’ll compare low-scoring (quiz score <40%) vs high-scoring (quiz score >65%) interaction patterns  
- Source: https://www.anthropic.com/research/AI-assistance-coding-skills

---

### Low-Scoring Pattern #1

### AI Delegation

- You ask AI to write the whole solution and you submit it
- Outcomes reported in the study:
  - fastest completion
  - few or no errors
- But the hidden cost:
  - weak understanding
  - poor transfer to new problems

---

### Low-Scoring Pattern #2

### Progressive AI Reliance

- You start with a couple questions
- Then gradually hand over **all** code writing to AI
- This often *feels* like learning because you’re “involved”
- But you’re training the habit of outsourcing difficulty

---

### Low-Scoring Pattern #3

### Iterative AI Debugging

- You write some code
- Then rely on AI to:
  - diagnose bugs
  - patch logic
  - verify correctness
- You ask many questions, but mostly to **solve**, not **understand**
- Result: less practice building your own debugging muscles

---

### High-Scoring Pattern #1

### Generation-then-comprehension

- You let AI generate code *as a starting point*
- Then you:
  - paste it into your work
  - ask follow-ups to understand it
  - rewrite parts in your own words/style
- More time spent **making sense** = better learning

---

### High-Scoring Pattern #2

### Hybrid code-explanation

- You compose hybrid queries: ask for code generation along with explanations of the generated code.
- Slower, but improves comprehension
- Best when you also ask:
  - “why this approach?”
  - “what alternatives exist?”
  - “what are common mistakes here?”

---

### High-Scoring Pattern #3

### Conceptual Inquiry

- You ask only conceptual questions:
  - “What is Python F-String really doing?”
  - “When is a set better than an array?”
- You then implement yourself
- You may hit more errors, but you solve more independently
- This is *harder* short-term, *stronger* long-term

---

### The Big Shift: AI as Tutor, Not Typist
- “Write the solution” → **bad default**
- “Help me understand so I can write it” → **good default**
- Think of AI as:
  - a TA who answers instantly
  - but you still have to take the exam alone

---

### A Practical Workflow That Builds Skill
- **Step 0:** Before opening any AI coding tool, pause and carefully read the lab instructions. Make sure you **fully understand the goals, requirements, and constraints of the assignment**.
- Step 1: **Try first** (even 10 minutes)
- Step 2: Ask AI for:
  - hints
  - concepts
  - edge cases

---

### A Practical Workflow That Builds Skill

- Step 3: Implement yourself
- Step 4: Use AI to review:
  - readability
  - complexity
  - potential bugs
- Step 5: Explain your final code (out loud or in comments)

---

### “Good” Prompts

- “Give me **3 hints**, not the full solution.”
- “Explain the concept like I’m new, then give a small example.”
- “What edge cases am I missing for this function?”
- “Here is my code. Ask me questions to check my understanding.”
- “Suggest improvements, but don’t rewrite everything, just point to *where* and *why*.”

---

### “Bad” Prompts (That Kill Learning)
- “Solve this assignment.”
- “Write the full code with no explanation.”
- “Fix my code and return the corrected version only.”
- “Give me the optimal solution immediately.”

---

### Make AI Help You Debug *Better*
- Instead of: “Fix this”
- Ask:
  - “What’s the bug category? (off-by-one, null, logic…)”
  - “What’s the smallest input that breaks it?”
  - “What print statements or try...except would reveal the issue?”
  - “Give me a debugging plan; I’ll execute it.”

---

### Turn AI Into a Quizzer
- “Ask me 5 questions about my solution to test understanding.”
- “Give me a similar problem with one twist.”
- “Hide one bug in this code and challenge me to find it.”
- “Give me 3 test cases: easy, edge, adversarial.”

---

### A Quick Self-Check Before You Submit
- Can I explain the algorithm in 2–3 sentences?
- Can I trace one example by hand?
- Do I know time/space complexity (roughly)?
- Can I modify it to handle one extra feature?
- If the AI disappeared, could I rebuild it?

---

### Academic Integrity
- Cite significant AI assistance in D2L dropbox comments 
- **Only ONE rule: Do NOT submit code you can’t explain**
- Your future self pays the bill for shortcuts

---

### Key Takeaways
- **Understand every line you submit**
- Avoid low-scoring patterns:
  - delegation, gradual handoff, AI-led debugging
- Prefer high-scoring patterns:
  - generate-then-comprehend, hybrid code explanation, conceptual inquiry
- Use AI to **strengthen thinking**, not replace it

---

### Best Practices

- Explore first, then plan, then code
- Write test, give AI a way to verify its work
- Provide specific context in your prompts
- Communicate effectively

---

### AI-Assisted Coding Journey

![yegge-ai-assisted-coding-journey](./use-ai-to-learn.assets/yegge-ai-assisted-coding-journey.webp)

Credit: [Steve Yegge - Welcome to Gas Town](https://steve-yegge.medium.com/welcome-to-gas-town-4f25ee16dd04)

---

### Activity

- Pick one feature from your latest assignment (create record file, file I/O error handling, evaluate file changes, etc. )
- Without looking:
  - write what each line does in plain English
  - list 2 edge cases
  - propose 1 improvement
- Then ask AI to critique your explanation, not your code
- Post your findings to troubleshooting channel

---

### Sources

- https://www.anthropic.com/research/AI-assistance-coding-skills
- https://arxiv.org/abs/2601.20245
- https://steve-yegge.medium.com/welcome-to-gas-town-4f25ee16dd04
- https://code.claude.com/docs/en/best-practices

---

### AI Use Disclaimer

- All resource gathering and verification were completed by me.
- AI assistance was used to rewrite and refine workflow steps.
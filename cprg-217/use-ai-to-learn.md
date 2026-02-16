## How to Effectively Use AI to Learn Coding

## Without Fooling Yourself

---

### Should I Use AI While Learning to Code?

- AI coding assistants can write code incredibly well.
- But if you rely on them before understanding the fundamentals, you'll end up stuck in **vibe coding hell** with no idea how to fix anything.

---

### What is Vibe Coding?

- Vibe coding is when you ask AI to generate code, it works (or seems to work), and you move on without really understanding what happened. You're coding based on vibes. It feels right. It looks ok. Ship it.
- The term was [coined by Andrej Karpathy](https://x.com/karpathy/status/1886192184808149383) (former Director of AI at Tesla and OpenAI researcher).
- When things go well, vibe coding feels magical. But when things break, and they will break, you're left staring at code you don't understand, trying to fix a problem you can't diagnose, using tools you never learned. Welcome to **vibe coding hell**.

---

### The Parallel - Tutorial Hell

- If you've been learning to code for a while, you might have heard of **tutorial hell**. It's when you watch tutorial after tutorial, follow along perfectly, and feel like you're learning. But the moment you try to build something on your own, you freeze. You have no idea where to start.
- Tutorial hell and vibe coding hell are cousins. Both give you the *illusion* of progress without building real understanding.

---

### Two Hells

- With tutorials, you're following someone else's thinking. With AI, you're outsourcing your thinking entirely. In both cases, the crucial skill of *figuring things out yourself* never develops.
- The difference is that vibe coding hell can be even more dangerous. At least with tutorials, you're exposed to explanations. With AI, you might never see the reasoning at all. You just get the answer.

---

### Why Fundamentals Matter

- AI doesn't make fundamentals obsolete. It makes them more important.
- Think about it this way. AI is a tool, arguably the most powerful coding tool ever created. But tools amplify the skill of the person using them. Give a chainsaw to a skilled lumberjack and they'll clear a forest efficiently. Give it to someone who's never held one and, well, let's just say things won't go smoothly.
- AI is a **multiplier**, not a magic +10 button. If your skill is sitting at zero, even the fanciest AI times a hundred is **still… zero**. Gotta bring something to the table first.

---

### When You Understand the Fundamentals

- Evaluate AI output critically.
- Debug effectively.
- Adapt and extend.
- Communicate with other developers.
- Architect systems.
- Vibe code better and faster than those who don’t understand the fundamentals, and yet still ship high-quality solutions.

---

### Why This Matters

- AI can speed you up **and** make you worse (if you outsource thinking)
- Your goal in school: **build skill**, not just submit assignments 
- You don't want to stagnate by trading out hard skills for quick answers.
- Treat AI like a **coach**, not a **ghostwriter**
- Once you have the fundamentals down, AI becomes genuinely transformative.

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

### When You're Learning a New Concept

- If you're learning about loops, don't ask AI to write your loops for you. You need to write bad loops. You need to hit off-by-one errors. You need to accidentally create infinite loops and have to kill your terminal. These experiences build intuition that no amount of AI-generated code can provide.
- You need to struggle with these concepts yourself before you can meaningfully use AI to work with them.

---

### When You're Building Something

### For the First Time

- Never run external commands or programs from within a Python script before? Build one manually first. Yes, AI can generate one in seconds. But you'll learn far more by:
  - Deciding on what command to run yourself
  - Figuring out how to handle non-zero exit code
  - Dealing with output parsing and filtering
  - Implementing error handling

---

### When You Don't Understand the Problem

- If you can't explain what you're trying to do in plain English, you're not ready to ask AI for code.
- You're just hoping the AI understands your problem better than you do. Sometimes it will. Often it won't. And you **won't know the difference**.
- Don't be unpleasantly surprised when you see the feedback of your assignment if you don't even read the lab document carefully.

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

### Learn First, Accelerate Later

- **Phase 1: Learning Mode** When encountering a new concept, technology, or problem space:
  - Don't use AI to generate code
  - Do use AI to *explain* concepts if documentation is unclear
  - Write code yourself, even if it's slow and painful
  - Make mistakes and learn from them
  - Build something from scratch at least once

---

### Learn First, Accelerate Later

- **Phase 2: Competence Mode** Once you can explain the concept to someone else and build basic implementations without help:

  - Use AI to speed up repetitive tasks

  - Use AI to explore alternative approaches

  - Still review all AI-generated code critically

  - Continue learning edge cases and advanced patterns

---

### Learn First, Accelerate Later

- **Phase 3: Expert Mode** When you have deep understanding and can quickly evaluate AI output:

  - Use AI liberally for productivity

  - Focus on architecture and design decisions

  - Use AI as a thought partner for complex problems

---

### Key Takeaways

- AI is the most powerful tool to ever enter the software development world. It will change how we write code in ways we're only beginning to understand.
- But it won't change the value of understanding. If anything, as AI becomes more prevalent, the developers who truly understand what's happening under the hood will become more valuable, not less. They'll be the ones who can use AI effectively, who can catch its mistakes, who can build systems that work.

---

### Key Takeaways

- So yes, use AI. Just not yet. Learn first. Struggle first. Build understanding first. Then, when you're ready, let AI make you unstoppable.
- The fundamentals aren't a detour on your coding journey. They're the foundation everything else is built on. Take the time to build that foundation well, and you'll thank yourself for years to come.

---

### Key Takeaways

- **Understand every line you submit**
- Avoid low-scoring patterns:
  - delegation, gradual handoff, AI-led debugging
- Prefer high-scoring patterns:
  - generate-then-comprehend, hybrid code explanation, conceptual inquiry
- Use AI to **strengthen thinking**, not replace it

---

### Activity

- Pick one feature from your latest assignment (create record file, file I/O error handling, evaluate file changes, etc.)
- Now close your AI assistant and go write some code. The bugs you encounter will be your best teachers.
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
- https://code.claude.com/docs/en/best-practices
- https://codeling.dev/blog/should-i-use-ai-while-learning-to-code/

---

### AI Use Disclaimer

- All resource gathering and verification were completed by me.
- This article includes materials that were developed with the assistance of generative AI tools. These tools were used to suggest phrasing of key takeaways.
- All content was reviewed, revised and finalized by me. The final product is original and tailored to support your learning. 
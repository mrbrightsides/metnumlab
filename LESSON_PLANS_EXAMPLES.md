# 📚 LESSON PLANS & TEACHING EXAMPLES
## Contoh-Contoh Praktis Mengajar dengan RANTAI MetNumLab

---

## 📋 DAFTAR ISI

1. [Lesson Plan: Newton-Raphson Method](#lesson-plan-1-newton-raphson-method)
2. [Lesson Plan: Gauss Elimination](#lesson-plan-2-gauss-elimination)
3. [Lesson Plan: Runge-Kutta for ODEs](#lesson-plan-3-runge-kutta-for-odes)
4. [Lesson Plan: Numerical Integration](#lesson-plan-4-numerical-integration)
5. [Mini-Lessons (15-30 menit)](#mini-lessons)
6. [Workshop Activities](#workshop-activities)
7. [Group Projects](#group-projects)
8. [Assessment Examples](#assessment-examples)

---

## LESSON PLAN #1: Newton-Raphson Method

### **📊 Overview**
- **Topic:** Root Finding dengan Newton-Raphson
- **Level:** Undergraduate Year 2-3
- **Duration:** 2 sessions × 90 menit
- **Prerequisites:** Calculus I (derivatives)

---

### **SESSION 1: Introduction & Theory (90 menit)**

#### **Learning Objectives:**
Setelah sesi ini, mahasiswa dapat:
1. ✅ Explain konsep iterasi Newton-Raphson
2. ✅ Calculate 2-3 iterasi manual
3. ✅ Understand konvergensi behavior
4. ✅ Use platform untuk basic problems

---

#### **MINUTE-BY-MINUTE PLAN:**

**[0-5 min] 🔥 HOOK: Engage Students**
```
Activity: "The Guessing Game"

Setup:
1. Write di board: f(x) = x² - 2 = 0
2. "Siapa yang tau jawabannya?" (Answer: x = √2 ≈ 1.414)
3. "Ok, sekarang tanpa calculator, gimana cara dapatnya?"
4. Students brainstorm methods
5. Transition: "Ada cara smart: Newton-Raphson!"

Why this works:
- Hands-on dari awal
- Problem relatable
- Creates curiosity
```

**[5-25 min] 📚 INPUT: Core Theory**
```
Lecture + Board Work:

1. [5 min] Problem Statement
   "Kita punya f(x) = 0, tapi ga bisa solve algebraically
    Example: x³ - 5x + 1 = 0 (no simple solution)"

2. [8 min] Method Intuition
   Draw diagram di board:
   
   [Sketch showing:
    - Curve f(x)
    - Point (x₀, f(x₀))
    - Tangent line at that point
    - Where tangent crosses x-axis = x₁
    - Repeat: x₁ → x₂ → x₃ → converge!]
   
   "Idea: Use tangent line to approximate where f(x) = 0"

3. [7 min] Derive Formula
   Tangent line: y - f(x₀) = f'(x₀)(x - x₀)
   Set y = 0 (looking for x-intercept):
   0 - f(x₀) = f'(x₀)(x₁ - x₀)
   
   Solve for x₁:
   x₁ = x₀ - f(x₀)/f'(x₀)
   
   Generalize:
   x_{n+1} = x_n - f(x_n)/f'(x_n)

4. [5 min] Check Understanding
   Quick poll: "Apa yang harus ada untuk pakai method ini?"
   Expected answers:
   - Need f(x) dan f'(x)
   - Need initial guess x₀
   - Need stopping criteria (tolerance)
```

**[25-45 min] 💡 WORKED EXAMPLE**
```
Problem: Find root of f(x) = x² - 2

Step-by-step di papan tulis:

Given:
- f(x) = x² - 2
- f'(x) = 2x
- x₀ = 1 (initial guess)
- ε = 0.01 (tolerance)

Iteration 1:
x₁ = x₀ - f(x₀)/f'(x₀)
   = 1 - (1² - 2)/(2·1)
   = 1 - (-1)/2
   = 1.5

Check: |f(1.5)| = |2.25 - 2| = 0.25 > 0.01 (continue)

Iteration 2:
x₂ = 1.5 - (1.5² - 2)/(2·1.5)
   = 1.5 - (2.25 - 2)/3
   = 1.5 - 0.25/3
   = 1.4167

Check: |f(1.4167)| = 0.0069 < 0.01 ✓ (STOP!)

Answer: x ≈ 1.4167 ≈ √2

Ask class: "Berapa error-nya?"
True value: √2 = 1.41421...
Error: |1.4167 - 1.41421| = 0.00249 (very small!)
```

**[45-55 min] 💻 PLATFORM DEMO**
```
[Open platform on projector]

Narration:
"Ok, manual calculation done. Sekarang lihat gimana
 platform automate this process..."

Demo steps:
1. Navigate to Dashboard
2. Click "New Job"
3. Select method: "Newton-Raphson"
4. Click "Quick Start with Samples"
5. Select: "Polynomial Root: x³ - 6x² + 11x - 6"

Explain each field:
- Function: What we're trying to solve
- Derivative: Needed untuk formula
- Initial Guess: Our starting point
- Tolerance: When to stop
- Max Iterations: Safety limit

6. Click "Process Job"

Show results:
- Iterations table
  "Lihat gimana converge cepat!"
- Convergence chart
  "Visual representation of approach"
- Error table
  "How error decreases each iteration"
- Final solution
  "Converged in 4 iterations!"

7. Click "3D View" tab
   "Cool visualization of convergence path"

8. Show Export options
   "You can download hasil as PDF/CSV"

Total demo time: ~10 minutes
```

**[55-85 min] 👥 GUIDED PRACTICE**
```
Students open laptops (or pair up if limited devices)

EXERCISE 1: Follow the Leader (15 min)
"Exactly replicate what I just showed you"

Checklist:
□ Open platform
□ New Job → Newton-Raphson
□ Load "Polynomial Root" sample
□ Process Job
□ View all tabs (Overview, Iterations, Charts, 3D)
□ Export as PDF

Walk around room, help stuck students
Common issues:
- Login/access problems
- Browser compatibility
- Misunderstanding interface

EXERCISE 2: Modify Parameters (15 min)
"Now let's experiment!"

Task: Same function, change initial guess
Try these x₀ values:
- x₀ = 0 → What happens?
- x₀ = 5 → Still converge?
- x₀ = 10 → Faster/slower?

Group discussion questions:
"Did everyone converge to same answer?"
"What differences did you notice?"
"Kenapa initial guess matters?"
```

**[85-90 min] 🎯 WRAP-UP**
```
Summary on board:

Newton-Raphson Method:
━━━━━━━━━━━━━━━━━━━━━
Formula: x_{n+1} = x_n - f(x_n)/f'(x_n)

✅ PROS:
- Very fast (quadratic convergence)
- Few iterations needed
- Accurate results

❌ CONS:
- Need derivative f'(x)
- Sensitive to initial guess
- Can fail if f'(x) = 0

ASSIGNMENT (announced):
━━━━━━━━━━━━━━━━━━━━━━
Due: 1 week from today

Problems:
1. f(x) = x³ - x - 2 = 0
2. f(x) = e^x - 3x = 0
3. f(x) = cos(x) - x = 0

For each:
- Use platform
- Try 3 different initial guesses
- Record: iterations, final answer, observations
- Export PDF
- Write short reflection (100 words):
  "What did you learn about initial guess importance?"

Submission:
- Email PDF to [instructor email]
- Subject: "NR Assignment - [Your Name]"

PREP for next class:
□ Watch video: "Newton-Raphson Advanced"
□ Take quiz (must score ≥60%)
```

---

### **SESSION 2: Applications & Advanced Topics (90 menit)**

#### **[0-10 min] RECAP + Q&A**
```
Quick review:
1. "Who can explain Newton-Raphson in 1 sentence?"
2. "What was your biggest 'aha moment' from assignment?"
3. Answer questions about homework
```

#### **[10-30 min] REAL-WORLD APPLICATIONS**
```
Case Study 1: Engineering Design
Problem: Optimize bridge cable tension

Show actual engineering diagram
Explain: Non-linear equation dari force balance
Demonstrate: Solve using platform
Result: Optimal tension value

Case Study 2: Economics
Problem: Find break-even point

Equation: Revenue - Cost = 0
Non-linear because of volume discounts
Solve: Platform shows break-even quantity

Case Study 3: Physics
Problem: Projectile trajectory

Find angle for max range
Non-linear equation of motion
Platform: Iterate to optimal angle
```

#### **[30-60 min] ADVANCED TOPICS**
```
Topic 1: Convergence Analysis
- What makes method converge fast/slow?
- Show quadratic convergence graph
- Compare with linear methods

Topic 2: Failure Cases
- Demo: What if f'(x) = 0?
- Demo: What if oscillation?
- How to detect and handle

Topic 3: Modifications
- Newton-Raphson variants
- Damped Newton method
- Hybrid approaches
```

#### **[60-85 min] GROUP CHALLENGE**
```
Teams of 3-4 students

Challenge: "Real Engineering Problem Competition"

Scenario:
You're consultants hired by different companies.
Each team gets different problem:
- Team 1: Civil (bridge design)
- Team 2: Mechanical (gear sizing)
- Team 3: Electrical (circuit optimization)
- Team 4: Chemical (reaction equilibrium)

Tasks:
1. Understand problem (5 min)
2. Formulate equation (5 min)
3. Solve using platform (10 min)
4. Prepare 3-slide presentation (10 min)

Presentation (each team 3 min):
- Problem statement
- Method used
- Results
- Business impact

Judges: Other students vote
Prize: Bonus points!
```

#### **[85-90 min] REFLECTION**
```
Individual reflection (written):
"What is one thing you will remember about
 Newton-Raphson method 5 years from now?"

Share 2-3 responses with class

Final thoughts from instructor
```

---

## LESSON PLAN #2: Gauss Elimination

### **📊 Overview**
- **Topic:** Solving Linear Systems
- **Duration:** 90 menit
- **Prerequisites:** Linear Algebra basics

---

### **MINUTE-BY-MINUTE PLAN:**

**[0-10 min] 🔥 HOOK: Real-World Problem**
```
"The Market Problem"

Setup story:
"Kamu ke pasar beli 3 jenis buah: apel, jeruk, pisang

Hari Senin: 2 apel + 1 jeruk + 3 pisang = Rp 25.000
Hari Selasa: 1 apel + 2 jeruk + 1 pisang = Rp 20.000
Hari Rabu: 3 apel + 1 jeruk + 2 pisang = Rp 27.000

Question: Berapa harga masing-masing buah?"

Let students try to solve (2-3 min)
Most will struggle → perfect setup!

"This is a LINEAR SYSTEM. Today we learn how to solve it
 systematically using Gauss Elimination!"
```

**[10-30 min] 📚 THEORY**
```
1. Write system as equations:
   2x + y + 3z = 25
   x + 2y + z = 20
   3x + y + 2z = 27

2. Matrix representation:
   [2  1  3 | 25]
   [1  2  1 | 20]
   [3  1  2 | 27]

3. Goal: Transform to upper triangular
   [a  b  c | d]
   [0  e  f | g]
   [0  0  h | i]

4. Allowed operations:
   - Swap rows
   - Multiply row by constant
   - Add multiple of one row to another

5. Work first 2 steps di papan tulis
   Show elimination process
```

**[30-45 min] 💻 PLATFORM DEMO**
```
1. New Job → Gauss Elimination
2. Quick Start → "Basic 3×3 System"
3. Show CSV upload option
4. Show manual input
5. Process Job
6. Walk through step-by-step reduction
7. Show final solution
8. Verify solution (substitute back)
```

**[45-75 min] 👥 HANDS-ON PRACTICE**
```
EXERCISE 1: Solve the Market Problem (15 min)
Use platform to find apple, orange, banana prices

EXERCISE 2: Structural Analysis (15 min)
Engineering application:
3 beams, find tension forces
Provide system of equations

EXERCISE 3: Circuit Analysis (15 min)
Electrical network
Find node voltages using Kirchhoff's laws
```

**[75-90 min] 🎯 ANALYSIS & WRAP-UP**
```
Discussion:
1. When does Gauss fail? (singular matrix)
2. Pivot strategy importance
3. Computational complexity
4. Applications in engineering

Assignment:
- 3 problems (small, medium, large systems)
- Include one real-world application
- Due next week
```

---

## LESSON PLAN #3: Runge-Kutta for ODEs

### **📊 Overview**
- **Topic:** Solving Differential Equations Numerically
- **Duration:** 2 sessions × 90 menit
- **Prerequisites:** Differential Equations basics

---

### **SESSION 1: Introduction to Numerical ODEs**

**[0-15 min] 🔥 HOOK: Population Growth**
```
Problem Setup:
"Bacteria population doubles every hour
Start with 100 bacteria
After 5 hours, how many bacteria?"

Simple case: P(t) = 100 × 2^t
Easy to solve analytically

Now complicate:
"What if growth rate decreases as population increases?
 (limited resources)"

dP/dt = r·P·(1 - P/K)
where K = carrying capacity

This is LOGISTIC EQUATION
Can't solve analytically easily
Need numerical methods!
```

**[15-40 min] 📚 THEORY**
```
1. ODE General Form:
   dy/dx = f(x, y)
   Initial condition: y(x₀) = y₀

2. Euler's Method (simple but inaccurate):
   y_{n+1} = y_n + h·f(x_n, y_n)
   
3. Runge-Kutta 4th Order (better):
   k₁ = h·f(x_n, y_n)
   k₂ = h·f(x_n + h/2, y_n + k₁/2)
   k₃ = h·f(x_n + h/2, y_n + k₂/2)
   k₄ = h·f(x_n + h, y_n + k₃)
   
   y_{n+1} = y_n + (k₁ + 2k₂ + 2k₃ + k₄)/6

4. Work 1 iteration manually on board

5. Explain: "4 evaluasi → weighted average → accurate"
```

**[40-55 min] 💻 PLATFORM DEMO**
```
1. New Job → Runge-Kutta RK4
2. Quick Start → "Exponential Growth"
3. Explain inputs:
   - Equation: dy/dx = y (exponential)
   - Initial: y(0) = 1
   - Step size: h = 0.1
   - Range: x = 0 to 2

4. Process Job

5. Show results:
   - Numerical solution table
   - Compare with analytical (e^x)
   - Error analysis
   - Visualization graph

6. Experiment dengan step size:
   - h = 0.5 (large) → less accurate
   - h = 0.01 (small) → very accurate but slow
```

**[55-85 min] 👥 HANDS-ON**
```
EXERCISE 1: Population Growth (15 min)
Logistic equation:
dP/dt = 0.5·P·(1 - P/1000)
P(0) = 10
Find P(t) for t = 0 to 20

Questions:
- What happens long-term?
- How fast does it reach carrying capacity?
- Effect of initial population?

EXERCISE 2: Cooling Problem (15 min)
Newton's Law of Cooling:
dT/dt = -k(T - T_ambient)
T(0) = 100°C
T_ambient = 20°C
k = 0.05

Find when T reaches 30°C

EXERCISE 3: Oscillator (15 min)
Simple harmonic motion:
d²x/dt² = -ω²x

Convert to system:
dx/dt = v
dv/dt = -ω²x

Solve using platform
```

**[85-90 min] 🎯 WRAP-UP**
```
Key Takeaways:
- RK4 balances accuracy & efficiency
- Step size h controls accuracy
- Applicable to many real problems
- Platform makes solving easy!

Assignment:
1. Solve 3 ODE problems
2. Compare different step sizes
3. Analyze error vs computational cost
4. Write reflection on trade-offs
```

---

### **SESSION 2: Advanced Applications**

**[0-20 min] RECAP + SHOWCASE**
```
Students share assignment findings
Discuss step size trade-offs
```

**[20-50 min] REAL-WORLD CASES**
```
Case 1: Projectile Motion with Drag
Case 2: Chemical Reaction Kinetics
Case 3: Predator-Prey Dynamics (Lotka-Volterra)
Case 4: RC Circuit Transient Response
```

**[50-90 min] MINI-PROJECT**
```
Teams choose one application
Model it as ODE
Solve using platform
Present findings
```

---

## LESSON PLAN #4: Numerical Integration

### **📊 Overview**
- **Topic:** Simpson's Rule & Trapezoidal Rule
- **Duration:** 90 menit
- **Prerequisites:** Calculus I (integrals)

---

### **QUICK PLAN:**

**[0-10 min] HOOK**
```
"Find area under curve without integration!"
Show curve, ask: how to estimate area?
```

**[10-30 min] THEORY**
```
1. Trapezoidal Rule: Linear approximation
2. Simpson's Rule: Parabolic approximation
3. Error analysis
4. Manual calculation of 1 example
```

**[30-50 min] PLATFORM DEMO**
```
Demo Simpson's Rule
Show convergence as n increases
Compare Trapezoid vs Simpson accuracy
```

**[50-80 min] HANDS-ON**
```
Exercise 1: Polynomial (easy)
Exercise 2: Trigonometric (medium)
Exercise 3: Engineering application (hard)
```

**[80-90 min] WRAP-UP**
```
When to use which method?
Real applications
Assignment
```

---

## MINI-LESSONS (15-30 menit)

### **Mini-Lesson 1: Quick Intro to Platform**
**Duration:** 15 menit
```
[0-3 min] Show dashboard
[3-6 min] Demo one method
[6-12 min] Students try it
[12-15 min] Q&A
```

### **Mini-Lesson 2: Error Analysis**
**Duration:** 20 menit
```
[0-5 min] Types of errors
[5-10 min] Demo convergence
[10-15 min] Student experiment
[15-20 min] Discussion
```

### **Mini-Lesson 3: Method Comparison**
**Duration:** 30 menit
```
[0-10 min] Intro 3 root-finding methods
[10-20 min] Same problem, 3 methods
[20-25 min] Compare results
[25-30 min] When to use which?
```

---

## WORKSHOP ACTIVITIES

### **Workshop 1: Method Selection Challenge**
**Duration:** 60 menit

```
Setup:
10 different problems displayed
Each requires different method

Activity:
Teams compete to:
1. Identify best method for each
2. Justify choice
3. Solve using platform
4. Present reasoning

Scoring:
- Correct method choice: 5 pts
- Good justification: 3 pts
- Accurate solution: 2 pts

Winner: Team with highest score
```

### **Workshop 2: Real-World Problem Solving**
**Duration:** 90 menit

```
Scenario-based learning:
- Civil Engineering: Bridge design
- Mechanical: Heat transfer
- Electrical: Power grid analysis
- Chemical: Reactor design

Each team:
1. Gets industry problem
2. Formulate mathematical model
3. Solve using platform
4. Present to "clients" (class)
5. Defend approach
```

---

## GROUP PROJECTS

### **Project 1: Comparative Analysis**
**Duration:** 2 weeks

```
Goal: Compare multiple methods for same problem

Requirements:
1. Choose one complex problem
2. Solve using 3+ methods
3. Compare:
   - Accuracy
   - Speed
   - Ease of use
   - Convergence behavior
4. Write report (5 pages)
5. Present findings (10 min)

Grading:
- Problem complexity (20%)
- Method implementation (30%)
- Analysis depth (30%)
- Presentation (20%)
```

### **Project 2: Engineering Application**
**Duration:** 3 weeks

```
Goal: Solve real engineering problem

Process:
Week 1: Problem selection & research
Week 2: Modeling & solving
Week 3: Report & presentation

Deliverables:
- Problem statement
- Mathematical formulation
- Platform implementation
- Results & interpretation
- Real-world implications
- 10-page report
- 15-min presentation
```

---

## ASSESSMENT EXAMPLES

### **Quiz 1: Concept Check (10 menit)**
```
1. Newton-Raphson requires:
   a) First derivative
   b) Second derivative
   c) No derivatives
   d) Both derivatives

2. Which converges fastest?
   a) Bisection
   b) Secant
   c) Newton-Raphson
   d) All same

3. Gauss Elimination solves:
   a) Single equation
   b) Linear systems
   c) Differential equations
   d) Integrals

4. Simpson's Rule uses:
   a) Lines
   b) Parabolas
   c) Circles
   d) Exponentials

5. RK4 means:
   a) 4 equations
   b) 4 evaluations per step
   c) 4 unknowns
   d) 4 iterations

Answers: a, c, b, b, b
```

### **Practical Exam (30 menit)**
```
Setup:
Each student gets unique problem

Task:
1. Read problem (5 min)
2. Choose method (explain why)
3. Solve using platform (15 min)
4. Interpret results (5 min)
5. Submit report (5 min)

Grading Rubric:
□ Method selection appropriate (25%)
□ Correct implementation (30%)
□ Accurate results (25%)
□ Good interpretation (20%)
```

### **Final Project Rubric**
```
Category: Technical Accuracy (40%)
- Problem formulation correct
- Method implementation proper
- Results accurate
- Error analysis included

Category: Analysis & Insight (30%)
- Deep understanding shown
- Comparisons made
- Limitations discussed
- Alternative approaches considered

Category: Communication (20%)
- Clear writing
- Good visuals
- Logical flow
- Professional presentation

Category: Creativity (10%)
- Novel application
- Unique approach
- Extra mile effort
```

---

## 🎯 TIPS FOR CREATING YOUR OWN LESSONS

### **The 5E Model (Recommended)**
```
1. ENGAGE (5-10 min)
   - Hook students' attention
   - Connect to prior knowledge
   - Create curiosity

2. EXPLORE (15-25 min)
   - Hands-on discovery
   - Use platform to experiment
   - Guide with questions

3. EXPLAIN (15-25 min)
   - Formal instruction
   - Clarify concepts
   - Connect to theory

4. ELABORATE (20-30 min)
   - Apply to new situations
   - Complex problems
   - Real-world contexts

5. EVALUATE (10-15 min)
   - Assess understanding
   - Formative or summative
   - Reflection
```

### **Lesson Planning Checklist**
```
Before designing lesson:
□ Clear learning objectives
□ Prerequisite knowledge identified
□ Materials prepared
□ Platform functionality tested
□ Timing estimated
□ Assessment planned

During lesson:
□ Start with hook
□ Check understanding frequently
□ Allow hands-on time
□ Walk around, assist
□ Summarize key points

After lesson:
□ Collect feedback
□ Review what worked
□ Adjust for next time
□ Follow up with students
```

---

## 📖 ADDITIONAL RESOURCES

### **Templates Available:**
- Lesson plan template (blank)
- Assessment rubrics
- Group activity sheets
- Reflection prompts
- Feedback forms

### **Community:**
Share your lesson plans with other educators!
- Email: educators@rantai-metnumlab.com
- Forum: [link]
- Monthly webinars

---

**Happy Teaching! 🎓**

*Remember: Best lessons come from experience.
Start with these templates, then adapt to YOUR style and YOUR students.*

---

*Last Updated: January 2025*
*Version: 1.0*

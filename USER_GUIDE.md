# 📚 User Guide - RANTAI MetNumLab

Panduan lengkap penggunaan RANTAI MetNumLab untuk mahasiswa dan dosen.

---

## 📖 Daftar Isi

1. [Pengenalan](#pengenalan)
2. [Memulai](#memulai)
3. [Panduan Mahasiswa](#panduan-mahasiswa)
4. [Panduan Dosen](#panduan-dosen)
5. [Advanced Features](#advanced-features)
6. [Tips & Tricks](#tips--tricks)
7. [Troubleshooting](#troubleshooting)
8. [FAQ](#faq)

---

## Pengenalan

### Apa itu RANTAI MetNumLab?

RANTAI MetNumLab adalah platform pembelajaran interaktif untuk metode numerik yang memungkinkan Anda:
- ✅ Belajar 7 metode numerik tanpa coding
- ✅ Visualisasi hasil secara real-time
- ✅ Eksperimen dengan parameter berbeda
- ✅ Akses video tutorials & quiz
- ✅ Export hasil dalam berbagai format
- ✅ Menggunakan AI untuk recommendations

### Siapa yang Menggunakan Platform Ini?

**Mahasiswa**: Untuk belajar dan memahami metode numerik dengan cara interaktif  
**Dosen**: Untuk membuat assignment dan mengelola tugas mahasiswa  
**Self-learners**: Untuk eksplorasi dan eksperimen dengan numerical methods  

---

## Memulai

### 1. Akses Platform

Buka browser dan kunjungi: `https://metnumlab.elpeef.com`

### 2. Navigasi Dashboard

Dashboard utama terdiri dari:
- **Header**: Logo, navigation menu, theme switcher
- **Main Area**: Jobs list, statistics, quick actions
- **Sidebar**: Method filters, status filters

### 3. Interface Overview

```
┌─────────────────────────────────────────┐
│  RANTAI MetNumLab    [Theme] [Settings] │ ← Header
├─────────────────────────────────────────┤
│ 📊 Dashboard                            │
│                                         │
│  [New Job] [Advanced Tools] [About]    │ ← Quick Actions
│                                         │
│  ┌─────────────┐  ┌─────────────┐     │
│  │   Jobs      │  │ Assignments │     │ ← Tabs
│  └─────────────┘  └─────────────┘     │
│                                         │
│  Job #1: Newton-Raphson      [View]   │
│  Job #2: Gauss Elimination   [View]   │ ← Jobs List
│  Job #3: Simpson's Rule      [View]   │
│                                         │
└─────────────────────────────────────────┘
```

---

## Panduan Mahasiswa

### A. Membuat Job Pertama

#### Cara 1: Quick Start (Recommended)

1. **Klik "New Job"** di dashboard
2. **Klik "🚀 Quick Start with Samples"**
3. **Pilih Category**: Root Finding, Linear Systems, Integration, ODEs
4. **Pilih Method**: Newton-Raphson, Gauss, dll
5. **Pilih Sample**: Polynomial, Engineering, Physics, dll
6. **Klik "Use This Sample"**
7. **Review parameters** (sudah pre-filled)
8. **Klik "Process Job"**

**Keuntungan**: Cepat, mudah, tidak perlu input data manual

#### Cara 2: Manual Input

1. **Klik "New Job"** di dashboard
2. **Pilih Method** dari dropdown
3. **Input Data**:
   - **Root Finding**: Function & derivative (optional)
   - **Linear Systems**: Matrix (CSV/JSON atau manual)
   - **Integration**: Function, bounds, intervals
   - **ODEs**: ODE equation, initial conditions
4. **Set Parameters**:
   - Tolerance: `1e-6` (default)
   - Max Iterations: `50` (default)
   - Method-specific parameters
5. **Klik "Process Job"**

### B. Memahami Hasil Job

#### 1. Overview Tab

Menampilkan:
- **Status**: Pending, Processing, Completed, Failed
- **Method**: Metode yang digunakan
- **Solution**: Hasil akhir
- **Execution Time**: Waktu komputasi
- **Iteration Count**: Jumlah iterasi

#### 2. Iterations Tab

Tabel iterasi step-by-step:

| Step | x | f(x) | f'(x) | x_new | Error |
|------|---|------|-------|-------|-------|
| 0 | 1.0 | -3.0 | 2.0 | 2.5 | 1.5 |
| 1 | 2.5 | 2.25 | 5.0 | 2.05 | 0.45 |
| ... | ... | ... | ... | ... | ... |

**Insight**: Lihat bagaimana method converge ke solution

#### 3. Charts Tab

Visualisasi konvergensi:
- **Line Chart**: Error vs Iteration
- **Bar Chart**: Value progression
- **Scatter Plot**: Solution path

**Insight**: Understand convergence behavior

#### 4. 3D View Tab (NEW!)

Interactive 3D visualization:
- **3D Mesh**: Rotating 3D objects
- **Surface Plot**: Mathematical function surface
- **Convergence Path**: Animated iteration trajectory

**Controls**:
- **Left Click + Drag**: Rotate
- **Right Click + Drag**: Pan
- **Scroll**: Zoom
- **Animation Speed**: Adjust slider

### C. Eksperimen dengan Parameter Explorer

**Akses**: Job Detail → "Parameter Explorer" button

**Fitur**:
1. **Adjust Parameters**: Tolerance, max iterations, step size
2. **Real-time Comparison**: Lihat efek perubahan parameter
3. **Side-by-side View**: Original vs Modified results
4. **Performance Metrics**: Execution time, iterations, accuracy

**Use Case**: Understand bagaimana parameter affect convergence

### D. Export Hasil

**Akses**: Job Detail → "Download" button

**Format Tersedia**:

1. **CSV** - Iteration data untuk Excel/Sheets
   ```csv
   step,x,f_x,df_x,x_new,error
   0,1.0,-3.0,2.0,2.5,1.5
   1,2.5,2.25,5.0,2.05,0.45
   ```

2. **JSON** - Complete structured data
   ```json
   {
     "method": "newton_raphson",
     "solution": 2.0,
     "iterations": [...],
     "metadata": {...}
   }
   ```

3. **Text Report** - Human-readable summary
   ```
   RANTAI MetNumLab - Job Report
   =============================
   Method: Newton-Raphson
   Solution: 2.0
   Iterations: 5
   Execution Time: 15ms
   ```

4. **PDF Report** - Professional formatted (uses browser print)

### E. Belajar dari Theory Materials

**Akses**: Dashboard → "📚 Theory Materials" tab

**Konten**:
- Konsep dasar metode numerik
- Penjelasan 7 metode dalam Bahasa Indonesia
- Formula matematika dengan LaTeX
- Algoritma step-by-step
- Contoh aplikasi real-world

**Struktur**:
```
1. Pengenalan Metode Numerik
2. Root Finding Methods
   - Newton-Raphson
   - Secant Method
   - Bisection Method
3. Linear Systems
   - Gauss Elimination
4. Numerical Integration
   - Simpson's Rule
   - Trapezoid Rule
5. Ordinary Differential Equations
   - Runge-Kutta 4
```

### F. Study Cases

**Akses**: Dashboard → "📖 Study Cases" tab

**Konten**:
- Real-world applications dari setiap metode
- Engineering problems
- Physics simulations
- Economics models
- Biology applications

**Format**:
- Problem statement
- Method selection reasoning
- Step-by-step solution
- Result interpretation
- Visualization

---

## Panduan Dosen

### A. Membuat Assignment

1. **Switch ke "Instructor" tab** di dashboard
2. **Klik "New Assignment"**
3. **Isi Form**:
   - **Title**: "Assignment 1: Newton-Raphson"
   - **Description**: Problem description & requirements
   - **Method**: Pilih metode yang required
   - **Due Date**: Set deadline
   - **Requirements** (optional):
     - Min Accuracy: `1e-6`
     - Max Iterations: `50`
4. **Klik "Create Assignment"**

### B. Monitor Submissions

**Akses**: Instructor Panel → Assignment Detail

**Informasi**:
- Total submissions
- On-time vs Late
- Average score
- Completion rate

**Actions**:
- View individual submissions
- Grade submissions
- Provide feedback
- Download all results

### C. Grading System

**Manual Grading**:
1. Open submission detail
2. Review student's job results
3. Check accuracy & methodology
4. Assign score (0-100)
5. Add feedback
6. Save grade

**Auto-grading** (future feature):
- Based on solution accuracy
- Based on iteration efficiency
- Based on parameter choices

### D. Assignment Templates

**Pre-built Templates**:
- **Lab 1**: Basic Root Finding
- **Lab 2**: Linear Systems
- **Lab 3**: Numerical Integration
- **Lab 4**: ODE Solving
- **Midterm**: Mixed methods
- **Final Project**: Real-world problem

**Custom Templates**:
1. Create assignment once
2. Save as template
3. Reuse in future semesters

---

## Advanced Features

### A. LaTeX Editor

**Akses**: Dashboard → "✨ Advanced Learning Tools" → "LaTeX Editor"

**Features**:
- **24 Quick-Insert Symbols**: √, ∫, ∑, ∏, lim, α, β, θ, dll
- **6 Pre-built Templates**: Quadratic, Newton-Raphson, Taylor Series, dll
- **Live Preview**: Inline & block mode
- **Copy to Clipboard**: One-click copy
- **Dark Mode**: Auto-adapts to theme

**Usage**:
```latex
# Input
f(x) = \sqrt{x^2 + 1}

# Preview
f(x) = √(x² + 1)
```

**Use Cases**:
- Write mathematical expressions
- Document formulas
- Create presentations
- Assignment descriptions

### B. AI Method Recommender

**Akses**: 
- Job Creator → Type in Problem Description
- Advanced Tools → "AI Method Recommender"

**How It Works**:
1. **Describe Your Problem**: "Find root of polynomial x^3 - 2x + 1"
2. **AI Analyzes**: NLP processing
3. **Get Recommendations**: Ranked list with scores
4. **Select Method**: One-click to populate form

**Example Output**:
```
🏆 Newton-Raphson (Score: 95/100)
   Reason: Fast convergence, polynomial function, 
           derivative easily computable
   
🥈 Secant Method (Score: 85/100)
   Reason: Good alternative if derivative is complex
   
🥉 Bisection (Score: 70/100)
   Reason: Guaranteed convergence but slower
```

**Factors Considered**:
- Problem type (root finding, integration, etc)
- Function complexity
- Derivative availability
- Accuracy requirements
- Speed requirements

### C. Video Tutorials & Quizzes

**Akses**: Advanced Tools → "Video Tutorials"

**Features**:
- **12 High-Quality Videos**: MIT, YouTube experts
- **Filter by Category**: General, Methods
- **Filter by Difficulty**: Beginner, Intermediate, Advanced
- **Duration Badges**: See time before watching
- **Interactive Quizzes**: Test understanding
- **Progress Tracking**: Track completion

**Learning Flow**:
1. **Watch Video** → Learn concept (10-50 min)
2. **Take Quiz** → 3 multiple choice questions
3. **Get Feedback** → Instant answer check
4. **View Explanation** → Understand why
5. **Review Mistakes** → Learn from errors
6. **Retry** → Improve score
7. **Complete** → Mark as done (≥60% to pass)

**Quiz Scoring**:
- 🏆 **80-100%** = Excellent! (auto-complete)
- 🎖️ **60-79%** = Good Job! (auto-complete)
- 💪 **0-59%** = Try Again! (retry recommended)

### D. 3D Visualization

**Akses**: Job Detail → "3D View" tab

**Modes**:

1. **3D Mesh View**
   - Animated rotating spheres
   - Color-coded by iteration
   - Orbit controls

2. **Surface Plot**
   - 3D function visualization
   - f(x,y) = x² + y²
   - Interactive mesh

3. **Convergence Path**
   - Animated trajectory
   - Color gradient (start → end)
   - Show iteration points
   - Speed controls

**Controls**:
- **Animation Speed**: 0.5x to 2x
- **Show Grid**: Toggle grid lines
- **Reset View**: Reset camera
- **Auto-rotate**: Toggle auto-rotation

**Use Cases**:
- Visualize convergence behavior
- Understand method trajectory
- Present results in 3D
- Educational demonstrations

---

## Tips & Tricks

### 💡 Productivity Tips

1. **Use Quick Start Samples**
   - Fastest way to start learning
   - Pre-validated data
   - Learn from examples

2. **Bookmark Favorite Methods**
   - Filter dashboard by method
   - Quick access to specific jobs

3. **Export Early, Export Often**
   - Save results before closing browser
   - Multiple format options
   - Share with team/instructor

4. **Leverage Parameter Explorer**
   - Experiment without creating new jobs
   - Compare side-by-side
   - Understand parameter effects

5. **Complete Video Quizzes**
   - Solidify understanding
   - Track learning progress
   - Get certificates (future)

### 🎯 Learning Tips

1. **Start with General Videos**
   - Build foundation first
   - Understand concepts before methods

2. **Use Study Cases**
   - Real-world context
   - Practical applications
   - Better retention

3. **Experiment with Parameters**
   - See what happens with different tolerance
   - Test edge cases
   - Understand trade-offs

4. **Read Theory Materials**
   - Before solving problems
   - Refer during problem-solving
   - Review after completion

5. **Use AI Recommender**
   - Learn method selection criteria
   - Understand trade-offs
   - Build intuition

### ⚡ Performance Tips

1. **Limit Max Iterations**
   - Prevent infinite loops
   - Faster computation
   - Still accurate

2. **Use Appropriate Tolerance**
   - `1e-6` for most cases
   - `1e-3` for quick results
   - `1e-9` for high precision

3. **Clear Old Jobs**
   - Free up localStorage
   - Better performance
   - Organized workspace

4. **Use CSV for Large Matrices**
   - Faster than manual input
   - Less error-prone
   - Easy to prepare in Excel

---

## Troubleshooting

### ❌ Common Issues

#### 1. "Job Failed to Process"

**Possible Causes**:
- Invalid function syntax
- Derivative mismatch
- Matrix not square
- Division by zero

**Solutions**:
- Check function syntax: `x^2` not `x²`
- Verify derivative is correct
- Ensure matrix dimensions match
- Choose better initial guess

#### 2. "Method Not Converging"

**Possible Causes**:
- Poor initial guess
- Function not differentiable
- Tolerance too strict
- Max iterations too low

**Solutions**:
- Try different initial guess
- Switch to different method
- Increase tolerance to `1e-3`
- Increase max iterations to `100`

#### 3. "Data Upload Failed"

**Possible Causes**:
- Invalid file format
- Incorrect CSV structure
- File too large

**Solutions**:
- Use CSV or JSON format
- Check file structure (comma-separated)
- Reduce data size
- Try manual input

#### 4. "localStorage Full"

**Possible Causes**:
- Too many jobs saved
- Browser storage limit reached

**Solutions**:
- Click "Clear All" in dashboard
- Delete old jobs manually
- Export important jobs first
- Use browser with higher limits

#### 5. "3D Visualization Not Loading"

**Possible Causes**:
- Browser doesn't support WebGL
- GPU acceleration disabled
- Outdated browser

**Solutions**:
- Update browser to latest version
- Enable hardware acceleration
- Use Chrome/Firefox/Edge
- Try different device

### 🔧 Browser Compatibility

| Browser | Status | Notes |
|---------|--------|-------|
| Chrome 90+ | ✅ Fully Supported | Recommended |
| Firefox 88+ | ✅ Fully Supported | Recommended |
| Safari 14+ | ✅ Fully Supported | Some 3D features limited |
| Edge 90+ | ✅ Fully Supported | Recommended |
| IE 11 | ❌ Not Supported | Use modern browser |

### 📱 Mobile Support

| Device | Status | Notes |
|--------|--------|-------|
| Android (Chrome) | ✅ Supported | Full features |
| iOS (Safari) | ✅ Supported | Some 3D features limited |
| Tablet | ✅ Supported | Optimized layout |
| Mobile | ⚠️ Limited | Best on desktop |

---

## FAQ

### Umum

**Q: Apakah gratis?**  
A: Ya, sepenuhnya gratis untuk mahasiswa dan pengajar.

**Q: Perlu install software?**  
A: Tidak, 100% web-based. Cukup buka di browser.

**Q: Data tersimpan dimana?**  
A: Di localStorage browser Anda. Tidak ada server backend saat ini.

**Q: Bisa offline?**  
A: Tidak, butuh internet untuk akses platform. (PWA coming soon)

**Q: Bahasa apa yang didukung?**  
A: Saat ini hanya Bahasa Indonesia. English coming soon.

### Teknis

**Q: Method apa yang paling cepat?**  
A: Newton-Raphson untuk root finding, Gauss untuk linear systems.

**Q: Berapa max iterations yang recommended?**  
A: 50-100 untuk most cases. Increase jika tidak converge.

**Q: Format CSV seperti apa?**  
A: Comma-separated, contoh:
```
1,2,3,10
4,5,6,20
7,8,9,30
```

**Q: Bisa export ke Excel?**  
A: Ya, download CSV lalu open di Excel.

**Q: 3D visualization lag, kenapa?**  
A: Coba disable grid, reduce animation speed, atau gunakan device dengan GPU lebih baik.

### Akademis

**Q: Hasil akurat tidak?**  
A: Ya, menggunakan standard numerical algorithms. Tolerance default `1e-6`.

**Q: Bisa untuk tugas/skripsi?**  
A: Ya, silakan gunakan. Cite dengan proper attribution.

**Q: Dosen bisa track progress mahasiswa?**  
A: Fitur instructor panel masih limited. Full LMS integration coming soon.

**Q: Bisa custom method?**  
A: Belum. Request feature di GitHub Issues.

---

## Dukungan

### 📧 Kontak

- **Email**: support@rantaimetnumlab.com
- **Discord**: [Join server](https://discord.gg/metnumlab)
- **GitHub**: [Report issues](https://github.com/mrbrightsides/metnumlab/issues)

### 📚 Resources

- **Documentation**: [docs.rantaimetnumlab.com](https://metnumlab.elpeef.com)
- **Video Tutorials**: Di dalam platform

---

**Selamat belajar! 🎓**

**Happy computing! 🚀**

---

**Last Updated**: October 4, 2025  
**Version**: 1.0.0

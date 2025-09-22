# RANTAI MetNumLab 🧮

**Interactive Numerical Methods Lab for teaching — CSV & JSON input → plots, iterations, reports.**

---

## What is MetNumLab?
RANTAI MetNumLab is an educational web tool for *Metode Numerik* (Numerical Methods) that allows students to **upload CSV / JSON** inputs and run standard numerical algorithms (e.g., Gaussian elimination, Newton-Raphson, RK4, Simpson). The platform focuses on *concepts & interpretation* (table of iterations, plots, downloadable report) rather than coding syntax.

---

## Goals
- Make numerical experiments accessible to non-programmer students.
- Provide reproducible job runs with downloadable results (CSV/JSON/PNG/PDF).
- Provide instructor features: assignment creation, auto-grading (tolerance-based), and grade export.

---

## Key Features
- Upload CSV (matrices, samples) or JSON (functions & parameters).
- Pre-implemented algorithms: Gauss Elimination, LU, Newton-Raphson, Secant, Simpson, RK4.
- Interactive iteration tables & plots (convergence, solution vs iteration).
- Job queue + persistent results (job_id → downloadable artifacts).
- Instructor mode: create assignment, expected output (with tolerance), auto-grade.
- OpenAPI endpoints for integration with RANTAI Diva / LMS.

---

## Input Formats (examples)

### 1. Augmented matrix (CSV)
Single CSV file: each row `a1,a2,...,an,b` (n columns for A, last column is b).
3,2,-1,1
2,-2,4,-2
-1,0.5,-1,0


### 2. Root finding (JSON)
```json
{
  "method": "newton",
  "function": "x**3 - 2*x - 5",
  "derivative": "3*x**2 - 2",
  "initial_guess": 2.0,
  "tolerance": 1e-6,
  "max_iter": 50
}
```
## Output (example JSON)

```json
{
  "job_id": "uuid-123",
  "method": "newton",
  "converged": true,
  "final_x": 1.4142135624,
  "iterations": [
    {"k": 0, "x": 1.0, "f": -1.0, "error": 1.0},
    {"k": 1, "x": 1.4167, "f": 0.0069, "error": 0.4167}
  ],
  "downloads": {
    "csv": "/api/metnum/jobs/uuid-123/result.csv",
    "pdf": "/api/metnum/jobs/uuid-123/report.pdf"
  }
}
```

---

## Tech stack (suggested)

- Frontend: Next.js + Plotly / Chart.js

= Backend: FastAPI (Python)

- Numerics: NumPy, SciPy, SymPy (safe parsing)

- Queue: Celery / RQ or FastAPI BackgroundTasks for MVP

- Storage: PostgreSQL (metadata) + S3/MinIO (artifacts)

- Auth: SIWE / wallet-based (optional instructor API keys)

---

## Getting started (MVP)

1. Clone repo

2. python -m venv venv && source venv/bin/activate

3. pip install -r requirements.txt

4. Run FastAPI backend (see example server files)

5. Push sample CSV/JSON → test with POST /metnum/jobs

---

## Contributing & Roadmap

Week 0–1: core endpoints + Gauss & Newton

Week 2: plotting + downloads

Week 3: instructor assignment & autograde

Week 4: extra methods & polish

---

## License

MIT © 2025 RANTAI / ELPEEF

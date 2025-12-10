# ASE Mock Lab Exam 2024/2025

Advanced Software Engineering lab exam practice — Flask API, Docker, and Load Testing.

**Exam Date:** 3rd December 2024  
**Student Code:** 123456  
**Passing Score:** 6/11 points

## Quick Start

```bash
cd material
docker-compose up --build
```

- **Flask API (HTTPS):** `https://localhost:8089`
- **Locust UI:** `http://localhost:8090`

---

## Exercises & Solutions

### Ex 1 — Git & GitHub (2 pts)

Repository link: `https://github.com/Maxvolt15/ASE00-123456/tree/main/material`

### Ex 2 — HTTPS Certificates (2 pts)

Created `asekey.pem` (RSA 4096-bit) and `asecert.pem` (expires 100 days, CN=localhost, O=123456).

### Ex 3 — Flask Endpoint `/ex1` (2 pts)

Counts digits (D) and letters (C) in input string, returns `D // C`.

```
GET /ex1?a=1a0   →  {"s": 2}               200 OK
GET /ex1?a=123   →  {"s": "invalid Input"} 400 Bad Request
GET /ex1?a=ciao  →  {"s": "invalid Input"} 400 Bad Request
```

### Ex 4 — Dockerfile (3 pts)

Built image based on `python:3.12-slim`, workdir `/123456`, exposes port 5001.

### Ex 5 — Container Execution (4 pts)

```bash
docker build -t mockex .
docker run -p 5002:5001 --name mockexcont mockex
```

| Field | Value |
|-------|-------|
| PORTS | `0.0.0.0:5002->5001/tcp` |
| Volumes | `null` |

### Ex 6 — Locustfile (1 pt)

Added task for `/ex1?a=C1a0` with weight 1.

### Ex 7 — Dockerfile.locust (2 pts)

Locust container based on `python:3.12-slim`, exposes port 8089.

### Ex 8 — Docker Compose (3 pts)

Two services (`ex1`, `locust`) with secrets for TLS certificates.

### Ex 9 — Locust Load Testing (3 pts)

| Metric | Endpoint |
|--------|----------|
| Most requests | `mio` |
| Most failures | `yui` |
| Highest response time | `azusa` |

### Ex 10 — Postman (3 pts)

Collection `mockex.json` with tests for X = "1a0", "123", "ciao".

### Ex 11 — Bandit Security Scan (2 pts)

| Metric | Count |
|--------|-------|
| Total issues | 2 |
| High severity | 1 |

### Ex 12 — Extra (1 pt)

Header value: `exam: 0654321`

---

## Project Structure

```
material/
├── app/
│   ├── app.py
│   ├── Dockerfile
│   ├── requirements.txt
│   ├── asecert.pem
│   └── asekey.pem
├── docker-compose.yml
├── locustfile.py
├── Dockerfile.locust
└── solutions.txt
```

---

## API Reference

| Endpoint | Description |
|----------|-------------|
| `GET /add?a=X&b=Y` | Addition |
| `GET /sub?a=X&b=Y` | Subtraction |
| `GET /mul?a=X&b=Y` | Multiplication |
| `GET /div?a=X&b=Y` | Division |
| `GET /mod?a=X&b=Y` | Modulo |
| `GET /ex1?a=X` | Digit/Letter ratio |
| `GET /secret?X=N` | Generate headers |

---

**Repository:** [ASE-mockExam2425](https://github.com/Maxvolt15/ASE-mockExam2425/tree/main/material)

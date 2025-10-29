# 🔌 API Documentation - RANTAI MetNumLab

Dokumentasi lengkap untuk API endpoints yang tersedia di RANTAI MetNumLab.

---

## 📋 Table of Contents

1. [Overview](#overview)
2. [Base URL](#base-url)
3. [Endpoints](#endpoints)
   - [Health Check](#health-check)
   - [Logger](#logger)
   - [Numerical Methods Jobs](#numerical-methods-jobs)
   - [Proxy](#proxy)
4. [Types & Interfaces](#types--interfaces)
5. [Error Handling](#error-handling)

---

## Overview

RANTAI MetNumLab menggunakan Next.js App Router untuk API routes. Semua endpoints berada di `/api/*` dan menggunakan TypeScript untuk type safety.

---

## Base URL

**Development**: `http://localhost:3000`  
**Production**: `https://your-domain.com`

---

## Endpoints

### Health Check

#### `GET /api/health`

Endpoint untuk cek status aplikasi.

**Response:**
```json
{
  "status": "ok",
  "timestamp": "2025-06-04T10:30:00.000Z",
  "uptime": 12345,
  "memory": {
    "used": 123456789,
    "total": 987654321
  }
}
```

**Status Codes:**
- `200` - OK

---

### Logger

#### `POST /api/logger`

Endpoint untuk logging events dari client-side.

**Request Body:**
```json
{
  "level": "info" | "warn" | "error",
  "message": "Log message",
  "metadata": {
    "userId": "optional",
    "action": "optional",
    "additionalData": {}
  }
}
```

**Response:**
```json
{
  "success": true,
  "timestamp": "2025-06-04T10:30:00.000Z"
}
```

**Status Codes:**
- `200` - Successfully logged
- `400` - Invalid request body
- `500` - Server error

---

### Numerical Methods Jobs

#### `GET /api/metnum/jobs`

Mendapatkan daftar semua jobs (untuk future backend integration).

**Query Parameters:**
- `limit` (optional) - Number of jobs to return
- `offset` (optional) - Pagination offset

**Response:**
```json
{
  "jobs": [],
  "total": 0,
  "message": "Currently using client-side storage"
}
```

**Status Codes:**
- `200` - OK

---

#### `POST /api/metnum/jobs`

Membuat job baru (untuk future backend integration).

**Request Body:**
```json
{
  "method": "newton_raphson",
  "data": {
    "function": "x^2 - 4",
    "derivative": "2*x"
  },
  "parameters": {
    "initialGuess": 1.0,
    "tolerance": 1e-6,
    "maxIterations": 50
  }
}
```

**Response:**
```json
{
  "jobId": "job_123456",
  "status": "processing",
  "createdAt": "2025-06-04T10:30:00.000Z"
}
```

**Status Codes:**
- `201` - Job created
- `400` - Invalid request body
- `500` - Server error

---

#### `GET /api/metnum/jobs/[jobId]`

Mendapatkan detail job berdasarkan ID (untuk future backend integration).

**Path Parameters:**
- `jobId` - Job ID

**Response:**
```json
{
  "id": "job_123456",
  "method": "newton_raphson",
  "status": "completed",
  "output": {
    "solution": 2.0,
    "iterations": [...],
    "metadata": {
      "executionTime": 15,
      "iterationCount": 5
    }
  },
  "createdAt": "2025-06-04T10:30:00.000Z",
  "completedAt": "2025-06-04T10:30:15.000Z"
}
```

**Status Codes:**
- `200` - OK
- `404` - Job not found
- `500` - Server error

---

### Proxy

#### `POST /api/proxy`

Proxy endpoint untuk external API calls dari client-side.

**Request Body (JSON):**
```json
{
  "protocol": "https",
  "origin": "api.example.com",
  "path": "/data",
  "method": "GET" | "POST" | "PUT" | "DELETE",
  "headers": {
    "Authorization": "Bearer token",
    "Content-Type": "application/json"
  },
  "body": {
    "key": "value"
  }
}
```

**Request Body (multipart/form-data):**
```typescript
const formData = new FormData();
formData.append('protocol', 'https');
formData.append('origin', 'api.example.com');
formData.append('path', '/upload');
formData.append('method', 'POST');
formData.append('headers', JSON.stringify({}));
formData.append('file', fileBlob);
```

**Response:**
```json
{
  "data": "Response from external API",
  "status": 200
}
```

**Status Codes:**
- `200` - OK
- `400` - Invalid request
- `500` - Server error
- `502` - Bad Gateway (external API error)

**Usage Example:**
```typescript
// JSON request
const response = await fetch('/api/proxy', {
  method: 'POST',
  headers: { 'Content-Type': 'application/json' },
  body: JSON.stringify({
    protocol: 'https',
    origin: 'api.example.com',
    path: '/endpoint',
    method: 'GET',
    headers: {},
  }),
});

// FormData request
const formData = new FormData();
formData.append('protocol', 'https');
formData.append('origin', 'api.example.com');
formData.append('path', '/upload');
formData.append('method', 'POST');
formData.append('headers', JSON.stringify({}));
formData.append('file', fileBlob);

const response = await fetch('/api/proxy', {
  method: 'POST',
  body: formData, // No Content-Type header - browser sets it automatically
});
```

---

## Types & Interfaces

### Job

```typescript
interface Job {
  id: string;
  method: NumericalMethod;
  status: 'pending' | 'processing' | 'completed' | 'failed';
  input: {
    data: any;
    parameters: MethodParameters;
  };
  output?: JobOutput;
  createdAt: Date;
  completedAt?: Date;
  error?: string;
}
```

### NumericalMethod

```typescript
type NumericalMethod = 
  | 'newton_raphson'
  | 'gauss_elimination'
  | 'secant'
  | 'runge_kutta_4'
  | 'simpson'
  | 'trapezoid'
  | 'bisection';
```

### MethodParameters

```typescript
interface MethodParameters {
  // Root finding
  initialGuess?: number;
  secondGuess?: number;
  tolerance?: number;
  maxIterations?: number;
  
  // Linear systems
  pivoting?: boolean;
  
  // Integration
  lowerBound?: number;
  upperBound?: number;
  intervals?: number;
  
  // ODEs
  stepSize?: number;
  endTime?: number;
  initialValue?: number;
}
```

### JobOutput

```typescript
interface JobOutput {
  solution: number | number[];
  iterations: IterationStep[];
  converged?: boolean;
  metadata: {
    executionTime: number;
    iterationCount: number;
    finalError?: number;
  };
}
```

### IterationStep

```typescript
interface IterationStep {
  step: number;
  values: Record<string, any>;
  error?: number;
  operation?: string;
}
```

### Assignment

```typescript
interface Assignment {
  id: string;
  title: string;
  description: string;
  method: NumericalMethod;
  dueDate: Date;
  requirements: {
    minAccuracy?: number;
    maxIterations?: number;
  };
  submissions: Submission[];
}
```

### Submission

```typescript
interface Submission {
  id: string;
  studentId: string;
  studentName: string;
  jobId: string;
  submittedAt: Date;
  score?: number;
  feedback?: string;
}
```

---

## Error Handling

### Error Response Format

```json
{
  "error": true,
  "message": "Error description",
  "code": "ERROR_CODE",
  "details": {
    "field": "Additional error details"
  }
}
```

### Common Error Codes

| Code | Description |
|------|-------------|
| `INVALID_METHOD` | Unsupported numerical method |
| `INVALID_PARAMETERS` | Invalid method parameters |
| `COMPUTATION_FAILED` | Error during computation |
| `NOT_FOUND` | Resource not found |
| `VALIDATION_ERROR` | Request validation failed |
| `SERVER_ERROR` | Internal server error |

### HTTP Status Codes

| Status | Meaning |
|--------|---------|
| `200` | OK - Success |
| `201` | Created - Resource created successfully |
| `400` | Bad Request - Invalid input |
| `401` | Unauthorized - Authentication required |
| `403` | Forbidden - Insufficient permissions |
| `404` | Not Found - Resource not found |
| `422` | Unprocessable Entity - Validation error |
| `500` | Internal Server Error - Server error |
| `502` | Bad Gateway - External API error |
| `503` | Service Unavailable - Server overloaded |

---

## Rate Limiting

**Current Status**: No rate limiting implemented

**Future Implementation**:
- 100 requests per minute per IP
- 1000 requests per hour per user
- Burst allowance: 20 requests

---

## Authentication

**Current Status**: No authentication required (all client-side)

**Future Implementation**:
- JWT-based authentication
- OAuth2 integration (Google, GitHub)
- API key for external integrations

---

## Webhooks

**Current Status**: Not implemented

**Future Implementation**:
- Job completion notifications
- Assignment submission alerts
- System status updates

---

## SDK Examples

### JavaScript/TypeScript

```typescript
import { createClient } from '@rantai-metnumlab/sdk';

const client = createClient({
  baseUrl: 'https://api.rantaimetnumlab.com',
  apiKey: 'your_api_key'
});

// Create a job
const job = await client.jobs.create({
  method: 'newton_raphson',
  data: {
    function: 'x^2 - 4',
    derivative: '2*x'
  },
  parameters: {
    initialGuess: 1.0,
    tolerance: 1e-6
  }
});

// Get job status
const result = await client.jobs.get(job.id);

// List all jobs
const jobs = await client.jobs.list({ limit: 10 });
```

### Python

```python
from rantai_metnumlab import Client

client = Client(
    base_url='https://api.rantaimetnumlab.com',
    api_key='your_api_key'
)

# Create a job
job = client.jobs.create(
    method='newton_raphson',
    data={
        'function': 'x**2 - 4',
        'derivative': '2*x'
    },
    parameters={
        'initialGuess': 1.0,
        'tolerance': 1e-6
    }
)

# Get job status
result = client.jobs.get(job['id'])

# List all jobs
jobs = client.jobs.list(limit=10)
```

---

## Changelog

### v1.0.0 (Current)
- ✅ Health check endpoint
- ✅ Logger endpoint
- ✅ Proxy endpoint
- ✅ Client-side job management
- ✅ localStorage persistence

### v1.1.0 (Planned)
- 🔜 Backend job processing
- 🔜 Database integration
- 🔜 User authentication
- 🔜 Real-time updates (WebSockets)

---

## Support

For API support, please:
- 📧 Email: api-support@rantaimetnumlab.com
- 💬 Discord: [Join our server](https://discord.gg/rantaimetnumlab)
- 🐛 Issues: [GitHub Issues](https://github.com/yourusername/rantai-metnumlab/issues)

---

**Last Updated**: June 4, 2025  
**API Version**: v1.0.0

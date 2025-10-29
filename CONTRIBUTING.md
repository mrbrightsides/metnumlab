# 🤝 Contributing to RANTAI MetNumLab

Thank you for your interest in contributing to RANTAI MetNumLab! This document provides guidelines and instructions for contributing.

---

## 📖 Table of Contents

1. [Code of Conduct](#code-of-conduct)
2. [Getting Started](#getting-started)
3. [Development Workflow](#development-workflow)
4. [Coding Standards](#coding-standards)
5. [Commit Guidelines](#commit-guidelines)
6. [Pull Request Process](#pull-request-process)
7. [Bug Reports](#bug-reports)
8. [Feature Requests](#feature-requests)
9. [Documentation](#documentation)

---

## Code of Conduct

### Our Pledge

We are committed to providing a friendly, safe, and welcoming environment for all contributors.

### Expected Behavior

- ✅ Be respectful and inclusive
- ✅ Accept constructive criticism
- ✅ Focus on what's best for the community
- ✅ Show empathy towards others

### Unacceptable Behavior

- ❌ Harassment or discrimination
- ❌ Trolling or insulting comments
- ❌ Publishing others' private information
- ❌ Unethical or unprofessional conduct

---

## Getting Started

### Prerequisites

- **Node.js**: 18.x or higher
- **npm**: 9.x or higher
- **Git**: For version control
- **Code Editor**: VSCode recommended

### Fork & Clone

```bash
# Fork the repository on GitHub
# Then clone your fork
git clone https://github.com/mrbrightsides/metnumlab.git
cd rantai-metnumlab

# Add upstream remote
git remote add upstream https://github.com/mrbrightsides/metnumlab.git
```

### Install Dependencies

```bash
npm install
```

### Run Development Server

```bash
npm run dev
```

Open [http://localhost:3000](http://localhost:3000)

---

## Development Workflow

### 1. Create a Branch

```bash
# Update your main branch
git checkout main
git pull upstream main

# Create feature branch
git checkout -b feature/your-feature-name

# Or bug fix branch
git checkout -b fix/bug-description
```

### Branch Naming Convention

- `feature/` - New features
- `fix/` - Bug fixes
- `docs/` - Documentation changes
- `refactor/` - Code refactoring
- `test/` - Adding tests
- `chore/` - Maintenance tasks

**Examples**:
- `feature/add-lagrange-interpolation`
- `fix/convergence-chart-rendering`
- `docs/update-api-documentation`
- `refactor/numerical-methods-module`

### 2. Make Changes

- Write clean, readable code
- Follow existing code style
- Add comments for complex logic
- Update tests if applicable
- Update documentation if needed

### 3. Test Your Changes

```bash
# Type checking
npm run type-check

# Linting
npm run lint

# Build
npm run build
```

### 4. Commit Changes

```bash
git add .
git commit -m "feat: add Lagrange interpolation method"
```

### 5. Push & Create PR

```bash
git push origin feature/your-feature-name
```

Then create a Pull Request on GitHub.

---

## Coding Standards

### TypeScript

#### 1. Strict Typing

```typescript
// ✅ Good - Explicit types
function calculateError(x: number, xNew: number): number {
  return Math.abs(xNew - x);
}

// ❌ Bad - Implicit any
function calculateError(x, xNew) {
  return Math.abs(xNew - x);
}
```

#### 2. Interface Definitions

```typescript
// ✅ Good - Clear interface
interface MethodParameters {
  initialGuess?: number;
  tolerance?: number;
  maxIterations?: number;
}

// ❌ Bad - Generic object
const params: any = { ... };
```

#### 3. Type Imports

```typescript
// ✅ Good - Type-only import
import type { Job, Assignment } from '@/types/job';

// ❌ Bad - Runtime import for types
import { Job, Assignment } from '@/types/job';
```

### React Components

#### 1. Component Structure

```typescript
'use client';

import type { FC } from 'react';

interface ComponentProps {
  title: string;
  onSubmit: () => void;
}

export const Component: FC<ComponentProps> = ({ title, onSubmit }) => {
  // Hooks
  const [state, setState] = useState<string>('');
  
  // Handlers
  const handleClick = () => {
    // Logic
  };
  
  // Render
  return (
    <div>
      {/* JSX */}
    </div>
  );
};
```

#### 2. Props Naming

```typescript
// ✅ Good - Clear prop names
interface ButtonProps {
  label: string;
  onClick: () => void;
  isDisabled?: boolean;
  variant?: 'primary' | 'secondary';
}

// ❌ Bad - Vague names
interface ButtonProps {
  text: string;
  handler: () => void;
  disabled?: boolean;
  type?: string;
}
```

### File Organization

```
src/
├── app/              # Next.js app router
├── components/       # React components
│   ├── ui/          # Reusable UI components
│   └── ...          # Feature components
├── lib/             # Utility functions
├── types/           # TypeScript definitions
├── contexts/        # React contexts
└── hooks/           # Custom hooks
```

### Naming Conventions

- **Files**: kebab-case (`job-creator.tsx`)
- **Components**: PascalCase (`JobCreator`)
- **Functions**: camelCase (`calculateError`)
- **Constants**: UPPER_SNAKE_CASE (`MAX_ITERATIONS`)
- **Types/Interfaces**: PascalCase (`MethodParameters`)

### Comments & Documentation

```typescript
/**
 * Solves a system of linear equations using Gauss Elimination.
 * 
 * @param matrix - Augmented matrix [A|b]
 * @param parameters - Method parameters (pivoting, etc)
 * @returns JobOutput containing solution and iterations
 * 
 * @example
 * ```typescript
 * const result = gaussElimination(
 *   [[2, 1, -1, 8], [-3, -1, 2, -11], [-2, 1, 2, -3]],
 *   { pivoting: true }
 * );
 * ```
 */
export function gaussElimination(
  matrix: number[][], 
  parameters: MethodParameters = {}
): JobOutput {
  // Implementation
}
```

---

## Commit Guidelines

### Commit Message Format

```
<type>(<scope>): <subject>

<body>

<footer>
```

### Types

- `feat` - New feature
- `fix` - Bug fix
- `docs` - Documentation changes
- `style` - Code style changes (formatting, etc)
- `refactor` - Code refactoring
- `test` - Adding or updating tests
- `chore` - Maintenance tasks
- `perf` - Performance improvements

### Examples

```bash
# Feature
git commit -m "feat(methods): add Lagrange interpolation"

# Bug fix
git commit -m "fix(charts): resolve convergence plot rendering issue"

# Documentation
git commit -m "docs(readme): update installation instructions"

# Refactoring
git commit -m "refactor(numerical-methods): extract common logic"

# With body
git commit -m "feat(export): add PDF export functionality

- Implement PDF generation using browser print API
- Add formatting for professional reports
- Include charts and iteration tables
- Add unit tests for export functionality"

# Breaking change
git commit -m "feat(api): change job status field names

BREAKING CHANGE: Rename 'state' to 'status' in Job interface"
```

---

## Pull Request Process

### 1. Before Submitting

- ✅ Code compiles without errors
- ✅ All tests pass
- ✅ Code follows style guidelines
- ✅ Documentation is updated
- ✅ Commit messages are clear
- ✅ Branch is up to date with main

### 2. PR Title

Use commit message format:

```
feat(methods): Add Lagrange interpolation method
```

### 3. PR Description Template

```markdown
## Description
Brief description of changes

## Type of Change
- [ ] Bug fix
- [ ] New feature
- [ ] Breaking change
- [ ] Documentation update

## How Has This Been Tested?
Describe testing process

## Screenshots (if applicable)
Add screenshots

## Checklist
- [ ] Code follows style guidelines
- [ ] Self-reviewed code
- [ ] Commented complex code
- [ ] Updated documentation
- [ ] No new warnings
- [ ] Added tests
- [ ] All tests pass
- [ ] Dependent changes merged
```

### 4. Review Process

1. **Automated Checks**: CI/CD runs automatically
2. **Code Review**: Maintainers review code
3. **Feedback**: Address review comments
4. **Approval**: Get approval from maintainers
5. **Merge**: Maintainer merges PR

### 5. After Merge

- Delete your feature branch
- Update your main branch
- Close related issues

---

## Bug Reports

### Before Submitting

1. **Search Issues**: Check if already reported
2. **Update**: Try latest version
3. **Reproduce**: Ensure bug is reproducible

### Bug Report Template

```markdown
**Describe the bug**
Clear description of the bug

**To Reproduce**
Steps to reproduce:
1. Go to '...'
2. Click on '...'
3. Scroll to '...'
4. See error

**Expected behavior**
What you expected to happen

**Screenshots**
Add screenshots if applicable

**Environment**
- OS: [e.g., Windows 10]
- Browser: [e.g., Chrome 120]
- Version: [e.g., 1.0.0]

**Additional context**
Any other relevant information
```

### Labels

- `bug` - Something isn't working
- `critical` - Critical bug requiring immediate fix
- `needs-reproduction` - Needs steps to reproduce
- `confirmed` - Bug confirmed by maintainers

---

## Feature Requests

### Feature Request Template

```markdown
**Is your feature request related to a problem?**
Description of the problem

**Describe the solution you'd like**
Clear description of desired solution

**Describe alternatives you've considered**
Alternative solutions considered

**Additional context**
Mockups, examples, or other context

**Priority**
- [ ] Low - Nice to have
- [ ] Medium - Would improve UX
- [ ] High - Critical for workflow
```

### Labels

- `enhancement` - New feature
- `good-first-issue` - Good for beginners
- `help-wanted` - Needs community help
- `question` - Further information needed

---

## Documentation

### What to Document

1. **Code Comments**: Complex logic, algorithms
2. **JSDoc**: Function parameters, return values
3. **README**: Setup, usage, features
4. **API Docs**: Endpoints, parameters, responses
5. **User Guide**: Step-by-step instructions

### Documentation Style

- Use clear, concise language
- Include code examples
- Add screenshots for UI features
- Keep up-to-date with code changes
- Use Markdown formatting

### Example

```typescript
/**
 * Calculates numerical solution using Newton-Raphson method.
 * 
 * The Newton-Raphson method uses the derivative to find roots:
 * x_{n+1} = x_n - f(x_n) / f'(x_n)
 * 
 * @param functionStr - Function as string (e.g., "x^2 - 4")
 * @param derivativeStr - Derivative as string (e.g., "2*x")
 * @param parameters - Method parameters
 * @param parameters.initialGuess - Starting point for iteration
 * @param parameters.tolerance - Convergence tolerance (default: 1e-6)
 * @param parameters.maxIterations - Maximum iterations (default: 50)
 * 
 * @returns JobOutput with solution, iterations, and metadata
 * 
 * @throws {Error} If derivative is zero (division by zero)
 * 
 * @example
 * ```typescript
 * const result = newtonRaphson(
 *   "x^2 - 4",
 *   "2*x",
 *   { initialGuess: 1.0, tolerance: 1e-6 }
 * );
 * console.log(result.solution); // 2.0
 * ```
 */
export function newtonRaphson(
  functionStr: string,
  derivativeStr: string,
  parameters: MethodParameters
): JobOutput {
  // Implementation
}
```

---

## Testing

### Running Tests

```bash
# Run all tests
npm test

# Run with coverage
npm run test:coverage

# Run specific test
npm test -- job-creator
```

### Writing Tests

```typescript
import { describe, it, expect } from 'vitest';
import { gaussElimination } from '@/lib/numerical-methods';

describe('gaussElimination', () => {
  it('should solve 2x2 system correctly', () => {
    const matrix = [
      [2, 1, 5],
      [1, -1, 1]
    ];
    
    const result = gaussElimination(matrix);
    
    expect(result.solution).toEqual([2, 1]);
    expect(result.converged).toBe(true);
  });
  
  it('should handle singular matrix', () => {
    const matrix = [
      [1, 2, 3],
      [2, 4, 6]
    ];
    
    expect(() => gaussElimination(matrix)).toThrow();
  });
});
```

---

## Community

### Communication Channels

- **GitHub Issues**: Bug reports, feature requests
- **GitHub Discussions**: Questions, ideas, general discussion
- **Discord**: Real-time chat (link in README)
- **Email**: support@rantaimetnumlab.com

### Getting Help

1. **Documentation**: Check README, User Guide, API Docs
2. **Search Issues**: Look for similar problems
3. **Ask in Discussions**: For questions
4. **Discord**: For real-time help

---

## Recognition

### Contributors

All contributors will be:
- Listed in CONTRIBUTORS.md
- Mentioned in release notes
- Featured on website (with permission)

### Types of Contributions

We value all contributions:
- 💻 Code
- 📖 Documentation
- 🐛 Bug reports
- 💡 Feature ideas
- 🎨 Design
- 🌍 Translations
- 📢 Community support

---

## License

By contributing, you agree that your contributions will be licensed under the MIT License.

---

## Questions?

Feel free to reach out:
- **Email**: dev@rantaimetnumlab.com
- **Discord**: [Join server](https://discord.gg/metnumlab)
- **GitHub**: Open an issue with `question` label

---

**Thank you for contributing! 🎉**

**Together we make RANTAI MetNumLab better! 🚀**

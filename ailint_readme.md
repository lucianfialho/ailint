# AILint 🤖⚡

**Stop your AI from generating shit code.**

AI assistants like Claude, GPT, and Copilot are amazing, but they have one problem: **they don't know your project**. They generate outdated patterns, ignore your conventions, and create inconsistent code.

AILint fixes this with **deterministic state machine rules** that teach your AI about your project's constraints.

## 🔥 The Problem

```javascript
// Your AI generates this garbage:
class UserService extends BaseService {
  constructor() {
    super();
    this.db = new Database(); // tightly coupled
    this.cache = new Redis();  // hardcoded dependencies
  }
}
```

```javascript
// AILint forces this instead:
function createUserService(db, cache) {
  return {
    async getUser(id) {
      // dependency injection
      // proper composition
    }
  }
}
```

## ⚡ The Solution

AILint uses **state machines** to detect AI limitations and apply constraints:

```yaml
# rules/universal/composition-over-inheritance.mdc
---
name: "composition-over-inheritance"
description: "AI defaults to inheritance when composition is better"

states: [idle, detection, analysis, constraint, validation, complete]

triggers:
  ai_requests: ["class", "extends", "inheritance"]
  
limitation:
  problem: "AI creates deep inheritance hierarchies"
  constraint: "Force composition patterns instead"
---
```

## 🚀 Quick Start

1. **Clone the rules:**
```bash
git clone https://github.com/yourusername/ailint
cd ailint
```

2. **Copy to your IDE:**
```bash
# Cursor
cp rules/universal/* .cursor/rules/

# Windsurf  
cp rules/universal/* .windsurf/rules/

# VS Code + Claude Dev
cp rules/universal/* .vscode/claude-rules/
```

3. **Watch your AI generate better code!**

## 📋 Available Rules

### Universal (Language-Agnostic)
- ✅ `composition-over-inheritance.mdc` - Prefer composition
- ✅ `dependency-injection.mdc` - Avoid tight coupling  
- ✅ `avoid-god-classes.mdc` - Single responsibility
- 🚧 `prefer-immutability.mdc` - Coming soon
- 🚧 `fail-fast-validation.mdc` - Coming soon

### Language-Specific
- 🚧 JavaScript modern patterns
- 🚧 Python type hints
- 🚧 Java streams & Optional

### Framework-Specific  
- 🚧 React hooks over classes
- 🚧 Django ORM best practices
- 🚧 Spring dependency injection

## 🎯 Why State Machines?

Traditional linting checks **static code**. AILint constrains **AI behavior** using deterministic state machines:

- **Debuggable**: See exactly which state triggered
- **Testable**: Verify state transitions  
- **Predictable**: Same input = same constraint
- **Extensible**: Community can contribute rules

## 🏗️ Architecture

```
AI Request → Detection → Analysis → Constraint → Validation → Better Code
     ↓           ↓          ↓           ↓            ↓
   Triggers   Context   Limitations  Patterns    Quality
```

## 🤝 Contributing

We need rules for every AI limitation! 

1. **Fork the repo**
2. **Create a rule** using our template
3. **Add examples** (before/after)  
4. **Submit PR** with test cases

See `docs/CONTRIBUTING.md` for the rule template.

## 📊 Stats

- 🎯 **Rules**: 3 universal, 15 coming soon
- 🔧 **IDEs**: Cursor, Windsurf, Claude Dev, VS Code
- 🌍 **Languages**: JavaScript, Python, Java, C#, Go
- 👥 **Contributors**: Looking for you!

## ⭐ Star if this saves you from AI-generated spaghetti code!

---

*"ESLint for the AI era"*
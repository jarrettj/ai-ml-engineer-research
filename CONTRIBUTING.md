# Contributing to AI/ML Engineer Research

Thank you for considering contributing to this learning resource! This is a **personal research repository**, but we welcome community contributions.

## 🌟 Ways to Contribute

### 1. Share Resources
- Found a useful tutorial? Add to [resources/](resources/)
- Great tool you discovered? Add to [guides/tools.md](guides/tools.md)
- Helpful code snippet? Create an exercise with it

### 2. Fix Issues
- Found a typo in the learning path? Submit a PR with corrections
- Notice a broken link? Fix it in the relevant file
- Improve documentation? Update the markdown files

### 3. Add Solutions (Optional)
- Completed an exercise? Add your solution in a separate file
- Created a better approach? Document it as an alternative method

### 4. Report Bugs
- Something's not working as expected?
- Exercise has incorrect instructions?
- Code doesn't run?

Open an **issue** with details:
- What you expected vs what happened
- Steps to reproduce
- Error messages

## 📝 How to Submit

### Using GitHub Pull Requests

1. **Fork** the repository
2. **Clone** your fork:
   ```bash
   git clone https://github.com/YOUR_USERNAME/ai-ml-engineer-research.git
   cd ai-ml-engineer-research
   ```
3. **Create a branch**:
   ```bash
   git checkout -b fix/typo-in-research-path
   ```
4. **Make your changes** and test thoroughly
5. **Commit** with clear messages:
   ```bash
   git commit -m "Fix: Correct typo in Phase 1.1.3"
   ```
6. **Push** to your fork:
   ```bash
   git push origin fix/typo-in-research-path
   ```
7. **Create a PR** on GitHub

## ✍️ Style Guidelines

### Documentation
- Use clear, concise language
- Active voice: "Run this command" not "This command should be run"
- Consistent formatting (headings, lists, code blocks)
- Add explanations for technical concepts

### Code
```python
# Follow Python PEP 8 style
import numpy as np
from sklearn.model_selection import train_test_split

def train_model(X, y):
    """Train a model on the given data."""
    # Inline comments for complex logic
    X_train, X_test, y_train, y_test = train_test_split(
        X, y, test_size=0.2, random_state=42
    )
    # ...
```

### Documentation Files
- Use Markdown for structure
- Include examples where helpful
- Add TODO sections for incomplete parts
- Keep markdown files up-to-date with actual content

## 🚫 What Not to Do

- ❌ Don't make major changes without discussion
- ❌ Don't add full solutions to exercises (provide hints only)
- ❌ Don't commit to `.gitignore` or `.env`
- ❌ Don't remove or modify existing content without discussion

## 🔍 Before Submitting

1. **Search existing issues** - Is your issue already reported?
2. **Check if it's broken** - Is the content outdated?
3. **Test your changes** - Does everything work?
4. **Update documentation** - Do other docs need updating?
5. **Run the exercises** - Do they still work?

## 🤝 Being a Good Contributor

- **Be respectful** - Everyone is learning!
- **Explain your reasoning** - Why is your approach better?
- **Offer alternatives** - There's rarely one "right" way
- **Help others** - Answer questions when you can
- **Stay updated** - Read the learning path as you contribute

## 📚 Resources for Contributors

- [Markdown guide](guides/writing-docs.md)
- [Python style guide](https://peps.python.org/pep-0008/)
- [GitHub Flow](https://guides.github.com/introduction/flow/)

## 🎉 Thank You!

Whether you contribute to fix a typo, add a new resource, or just follow the path - you're making this journey better for everyone.

**Happy contributing!** 🚀

# 🚀 Quick Start Guide

Welcome to your **AI/ML Engineer Research Journey**! This guide will help you get set up quickly and start learning.

---

## ✅ Pre-Requisites

### Minimum Requirements
- [ ] Python 3.10+
- [ ] Basic Python knowledge
- [ ] Git installed
- [ ] GitHub account

### Recommended (but optional)
- [ ] Linux/MacOS (Windows works but requires WSL)
- [ ] Jupyter Lab or VS Code
- [ ] Docker (for later phases)
- [ ] 8GB+ RAM

---

## 🚀 Step-by-Step Setup

### 1. Clone the Repository

```bash
git clone https://github.com/jarrettj/ai-ml-engineer-research.git
cd ai-ml-engineer-research
```

### 2. Create Virtual Environment

```bash
# Create venv
python -m venv venv

# Activate it
# Mac/Linux:
source venv/bin/activate

# Windows:
venv\Scripts\activate
```

### 3. Install Core Dependencies

```bash
pip install -r requirements.txt
```

### 4. Install Development Tools (Optional)

```bash
pip install -r requirements-dev.txt
```

### 5. Set Up Your Environment

```bash
# Copy .env.example to .env (if needed)
cp .env.example .env  # Don't commit .env!

# Run setup script (if exists)
bash setup.sh
```

### 6. Verify Installation

```bash
# Test Python version
python --version

# Test dependencies
python -c "import torch; print(f'PyTorch: {torch.__version__}')"

# Test notebook servers
jupyter lab --no-browser  # Should start successfully
```

---

## 📁 Understanding the Structure

```
ai-ml-engineer-research/
├── docs/                 # Learning path, guides, resources
│   ├── RESEARCH-PATH.md  # Main learning curriculum
│   ├── QUICKSTART.md     # This file!
│   └── ...
├── notebooks/            # Jupyter notebooks
│   └── jupyter/          # Phase 1 notebooks here
├── projects/            # Your completed projects
├── exercises/           # Practice exercises
└── resources/           # Curated tutorials, courses, tools
```

### Where to Start?

1. **Read [RESEARCH-PATH.md](docs/RESEARCH-PATH.md)** - Get the big picture
2. **Start with Phase 1** - Foundations first
3. **Do exercises** - Hands-on practice
4. **Build projects** - Apply what you learn
5. **Iterate** - Keep building, keep learning

---

## 🐍 Getting Started with Phase 1

### Week 1: Python Review

Create a simple Python script:

```python
# practice-python.py
import numpy as np
from sklearn.datasets import make_regression

# Generate simple data
X, y = make_regression(n_samples=100, n_features=5, noise=0.1, random_state=42)

# Print dimensions
print(f"Features shape: {X.shape}")
print(f"Target shape: {y.shape}")

# Simple linear regression from scratch
# (You'll build this in tutorials)
```

Run it:
```bash
python practice-python.py
```

### Week 2: Your First ML Model

```python
# from sklearn import linear_model
# from sklearn.model_selection import train_test_split
# from sklearn.metrics import mean_squared_error

# Split data
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2)

# Create model
model = linear_model.LinearRegression()

# Train
model.fit(X_train, y_train)

# Evaluate
y_pred = model.predict(X_test)
mse = mean_squared_error(y_test, y_pred)
print(f"RMSE: {np.sqrt(mse)}")
```

---

## 📚 Learning Resources

### Must-Follow
- [RESEARCH-PATH.md](docs/RESEARCH-PATH.md) - Your roadmap
- Weekly **reading assignments** (linked in docs)
- Hands-on **exercises** (do these!)

### Optional (pick 1-2)
- **Course**: Andrew Ng's ML Specialization (Coursera)
- **Book**: Hands-On ML by Géron
- **Blog**: [Distill.pub](https://distill.pub/) for ML intuition
- **YouTube**: Two Minute Papers for staying updated

### Avoid (for now)
- Too many courses (finish one first!)
- Math-heavy books without practice
- "10 courses to become..." lists (do the path, not the courses)

---

## 🛠️ Helpful Commands

### Python Quick Reference

```python
# Import your main modules
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LinearRegression

# Start a numpy array
arr = np.array([[1, 2, 3], [4, 5, 6]])

# Matrix operations
result = arr @ arr.T  # Matrix multiplication

# Basic stats
print(f"Mean: {arr.mean(axis=0)}")
print(f"Std: {arr.std(axis=0)}")
```

### Git Quick Reference

```bash
# Track changes
git add docs/ projects/ notebooks/

# Create commit
git commit -m "Add project 01: Linear regression with analysis"

# Push to GitHub
git push origin main

# Create new branch for work
git checkout -b project-02
```

---

## 📈 Tracking Progress

### Daily Log
Keep a simple log in `progress-daily.md`:

```markdown
## 2024-XX-XX
- **Focus**: Python numpy basics
- **Completed**: Matrix multiplication, array indexing
- **Struggled**: Understanding broadcasting
- **Next**: Linear algebra review
```

### Weekly Check-in
Update your [RESEARCH-PATH.md](docs/RESEARCH-PATH.md) with progress:

```markdown
| Milestone | Status | Notes |
|-----------|--------|-------|
| **Phase 1.1.1** | ✅ Done | Covered in notebook |
| **Phase 1.1.2** | ⬜ Planned | Starting next week |
```

---

## 🆘 Getting Help

### Common Issues

#### Issue: "ModuleNotFoundError: No module named 'sklearn'"
```bash
pip install scikit-learn
```

#### Issue: Jupyter notebook not displaying plots
```bash
# Set IPython display hooks
%matplotlib inline
```

#### Issue: CUDA errors on GPU
```bash
# Check GPU
python -c "import torch; print(torch.cuda.is_available())"
# If False, install CPU version first
pip uninstall torch torchvision torchaudio
pip install torch --index-url https://download.pytorch.org/whl/cpu
```

### Where to Ask

1. **Check docs first** - Read [guides/](guides/) thoroughly
2. **Search Google/StackOverflow** - 90% of questions are answered
3. **GitHub Issues** - Search existing issues first
4. **Discord** - Join ML/AI communities

---

## 🎯 First Week Goals

1. [ ] Clone repo and set up environment
2. [ ] Read [RESEARCH-PATH.md](docs/RESEARCH-PATH.md) (skim at least)
3. [ ] Complete "Python Review" exercise
4. [ ] Build your first linear regression model
5. [ ] Log your progress in daily.md
6. [ ] Commit your work to GitHub

---

## 🏆 Milestone Checkpoints

### Month 1 Goal
- Complete Phase 1.1 (Python + Math basics)
- Build 1 small ML project
- Commit 5+ meaningful commits to GitHub

### Month 3 Goal
- Finish Phase 1 (Foundations)
- Start Phase 2 (Deep Learning)
- Have 2-3 completed projects

### Month 6 Goal
- Complete Phases 1-3
- Deploy 1 production-ready model
- Contribute to open-source ML project

---

## 💡 Pro Tips

1. **Code every single day** - Even 30 minutes
2. **Don't just read** - Type everything out
3. **Break things** - Learn from errors
4. **Teach what you learn** - Write notes, explain to others
5. **Build in public** - Share on Twitter, LinkedIn
6. **Join communities** - Find people on the same path

---

## 🎉 Congratulations!

You're on your AI/ML engineering journey now. This path is challenging but incredibly rewarding. Every error you encounter, every concept you master, every model you deploy - these are your wins.

**Stay curious, stay humble, keep building!** 🚀

---

**Questions?** Open an issue or check the [RESEARCH-PATH.md](docs/RESEARCH-PATH.md) for detailed breakdowns of each topic!

# Contributing to Adaptive Demand Forecasting Platform

Thank you for considering contributing! This is a research-grade, production-level project,
and we maintain high standards for code quality, documentation, and testing.

---

## Development Setup

```bash
git clone https://github.com/yourname/adaptive-demand-forecasting.git
cd adaptive-demand-forecasting
python -m venv venv && source venv/bin/activate
pip install -r requirements.txt
pip install -r requirements-dev.txt   # linting/test extras
cp .env.example .env
```

**Requirements-dev.txt extras:**
```
ruff black isort bandit pytest pytest-cov pytest-asyncio httpx
```

---

## Code Standards

| Tool | Purpose | Config |
|---|---|---|
| `ruff` | Linting | `pyproject.toml` |
| `black` | Formatting (line-length 100) | `pyproject.toml` |
| `isort` | Import ordering | `pyproject.toml` |

Run all checks before committing:
```bash
ruff check src/ api/ dashboard/ tests/
black --check src/ api/ dashboard/ tests/
isort --check-only src/ api/ dashboard/ tests/
```

Auto-fix:
```bash
ruff check --fix src/ api/ dashboard/
black src/ api/ dashboard/ tests/
isort src/ api/ dashboard/ tests/
```

---

## Testing Requirements

- New ML model contributions must include:
  - A unit test verifying `fit()` and `predict()` run without error on synthetic data
  - A benchmark result in `docs/RESEARCH.md`
- New API endpoints must include:
  - An API test in `tests/api/test_api.py`
- Minimum 90% test coverage on new code

Run tests:
```bash
pytest tests/unit -v
pytest tests/api -v
pytest tests/integration -v
```

---

## Pull Request Process

1. Fork the repository and create a feature branch: `git checkout -b feat/your-feature`
2. Follow the code standards above
3. Write or update tests
4. Update documentation (`docs/`, docstrings) as needed
5. Ensure all CI checks pass
6. Open a PR with a clear description of:
   - What problem this solves
   - How it was tested
   - Any benchmark results

---

## Commit Message Convention

We follow [Conventional Commits](https://www.conventionalcommits.org/):

```
feat(models): add Temporal Fusion Transformer model
fix(features): resolve days_to_holiday dtype error on pandas 2.x
docs(api): add authentication example to API_REFERENCE.md
test(unit): add quantile forecasting tests for LightGBM
refactor(pipeline): extract time-based split to utility function
```

---

## Areas Open for Contribution

- 🧠 Temporal Fusion Transformer (TFT) implementation
- 🌤 Real weather API integration (OpenWeather)
- 📊 Additional benchmark datasets (e.g., M4, Tourism)
- 🌍 Multi-language holiday support
- 🤖 LLM-based natural language forecast explanations
- 📱 Mobile companion app
- 🔄 Reinforcement learning dynamic pricing module

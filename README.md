<div align="center">

<img src="docs/assets/logo.svg" alt="AquaScope logo" width="160"/>

# AquaScope

**Open-source Python toolkit for water data, hydrology, and agricultural water management.**

[![CI](https://github.com/Rekin226/aquascope/actions/workflows/ci.yml/badge.svg)](https://github.com/Rekin226/aquascope/actions/workflows/ci.yml)
[![PyPI version](https://img.shields.io/pypi/v/aquascope.svg?color=blue)](https://pypi.org/project/aquascope/)
[![PyPI downloads](https://img.shields.io/pypi/dm/aquascope.svg?color=blue)](https://pypi.org/project/aquascope/)
[![Python](https://img.shields.io/pypi/pyversions/aquascope.svg?color=informational)](https://www.python.org/downloads/)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Code style: ruff](https://img.shields.io/badge/code%20style-ruff-261230.svg)](https://github.com/astral-sh/ruff)
[![Tests](https://img.shields.io/badge/tests-534%20passing-brightgreen.svg)](#)

[![GitHub stars](https://img.shields.io/github/stars/Rekin226/aquascope?style=social)](https://github.com/Rekin226/aquascope/stargazers)
[![GitHub forks](https://img.shields.io/github/forks/Rekin226/aquascope?style=social)](https://github.com/Rekin226/aquascope/network/members)

[**Install**](#install) ·
[**Try it**](#try-it) ·
[**Features**](docs/features.md) ·
[**Docs**](#documentation) ·
[**Roadmap**](ROADMAP.md) ·
[**Discussions**](https://github.com/Rekin226/aquascope/discussions)

</div>

---

AquaScope unifies 12 global water-data APIs (USGS, FAO AQUASTAT, FAO WaPOR, GEMStat, EU WFD, Copernicus, Taiwan, Japan MLIT, Korea WAMIS, OpenMeteo, UN SDG 6) behind one Python schema, then layers a full scientific stack on top — Bulletin 17C flood frequency, baseflow separation, FAO-56 ET₀, copulas, Bayesian UQ — wrapped in an AI engine that scores 26 research methodologies against your dataset.

---

## ✨ What you can do

- 🌊 **Pull data** from 12 agencies with one unified API.
- 📈 **Run flood-frequency analysis** (GEV / LP3 / Gumbel / non-stationary GEV, Bulletin 17C compliant).
- 🌾 **Compute FAO-56 crop water requirements** for 20 crops with full Kc tables and soil water balance.
- 💧 **Separate baseflow**, fit rating curves, compute 22 hydrological signatures.
- 🤖 **Ask the AI engine** which methodology fits your dataset — and auto-execute it.

## 📊 Why AquaScope

| | AquaScope | HEC-SSP | R `lmom` | Standalone collectors |
| :--- | :---: | :---: | :---: | :---: |
| Bulletin 17C FFA + EMA | ✅ | ✅ | partial | — |
| Non-stationary GEV | ✅ | — | partial | — |
| Baseflow separation | ✅ | — | — | — |
| FAO-56 ET₀ + crop water | ✅ | — | — | — |
| 12 unified data collectors | ✅ | — | — | per-source |
| AI methodology recommender | ✅ | — | — | — |
| Free, MIT, Python-native | ✅ | partial | ✅ | varies |

---

## ⚡ Install

```bash
pip install aquascope            # core
pip install "aquascope[all]"     # everything — ML, viz, spatial, dashboard
```

Need a subset? `pip install "aquascope[ml]"`, `[viz]`, `[scientific]`, `[spatial]`, `[dashboard]`. See [pyproject.toml](pyproject.toml) for all extras.

## 🚀 Try it

```python
from aquascope.api import flood_analysis

result = flood_analysis(daily_discharge, method="gev", return_periods=[10, 50, 100])
print(result.return_levels)
#   return_period  return_level  lower_ci  upper_ci
# 0           10        1840.2     1690.4    2010.6
# 1           50        2530.7     2280.1    2820.9
# 2          100        2870.4     2540.6    3260.5
```

That's a Bulletin 17C-compliant flood frequency analysis with bootstrap confidence intervals in three lines. Equivalent workflows exist for baseflow separation, FAO-56 ET₀, copula dependence, change-point detection, and 20+ more methods — see [docs/features.md](docs/features.md).

---

## 📚 Documentation

| Resource | What it covers |
| :--- | :--- |
| [Features](docs/features.md) | Full capability list — hydrology, agriculture, ML, spatial, I/O |
| [Data sources](docs/data_sources.md) | All 12 sources, endpoints, API-key requirements |
| [Theory guide](docs/theory.md) | Equations, DOI citations, decision trees for every method |
| [Methodology matrix](docs/methodology_matrix.md) | When to use which method |
| [Architecture](docs/guides/architecture.md) | How AquaScope is structured internally |
| [FAQ](docs/faq.md) · [Troubleshooting](docs/troubleshooting.md) | Common questions and fixes |
| [Use cases](docs/use_cases.md) | Real-world applications |
| [Integration guides](docs/integration_guides/) | xarray, QGIS, R interoperability |
| [Contributing](CONTRIBUTING.md) | How to add a data source, methodology, or test |

---

## 🤝 Contributing

We welcome contributions from the global water and agriculture research community. The highest-impact contributions right now:

- New **data source collectors** (your country / region)
- New **research methodologies** for the AI recommender
- **Jupyter tutorials** and validation studies

See [CONTRIBUTING.md](CONTRIBUTING.md) and the [adding a data source](docs/guides/adding_data_source.md) guide.

## 📜 Citation

If you use AquaScope in your research, please cite:

```bibtex
@software{aquascope2026,
  title   = {AquaScope: Open-Source Water Data Aggregation, Hydrological Analysis, and Agricultural Water Management Toolkit},
  author  = {AquaScope Contributors},
  year    = {2026},
  url     = {https://github.com/Rekin226/aquascope},
  version = {0.4.0},
  license = {MIT}
}
```

## 📄 License

MIT — see [LICENSE](LICENSE).

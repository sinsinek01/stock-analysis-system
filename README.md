# 📊 Stock Market Analysis System

> Automated desktop application that scrapes live stock market data, runs multi-indicator technical analysis, and generates next-day **BUY / SELL** recommendations — all inside a modern dark-mode GUI.

![Python](https://img.shields.io/badge/Python-3.10%2B-blue?style=flat-square&logo=python)
![Selenium](https://img.shields.io/badge/Selenium-4.x-green?style=flat-square&logo=selenium)
![Pandas](https://img.shields.io/badge/Pandas-2.x-150458?style=flat-square&logo=pandas)
![License](https://img.shields.io/badge/License-MIT-yellow?style=flat-square)

---

## 🖥️ Preview

![Dashboard Preview](preview.png)

---

## ✨ Features

- **Live data scraping** via Selenium (headless Chrome) from Yahoo Finance
- **HTML parsing** with BeautifulSoup — extracts Finviz fundamental data (P/E, EPS) for US stocks
- **Technical indicators** calculated from scratch with Pandas:
  - RSI (14), MACD, Bollinger Bands, MA20 / MA50, ATR, Volume MA
- **Composite 0–100 scoring engine** → `STRONG BUY` / `BUY` / `HOLD` / `CAUTIOUS SELL` / `SELL`
- **Modern dark-mode GUI** built with customtkinter + embedded Matplotlib charts
- **Non-blocking threading** — UI stays responsive while analysis runs in the background
- **Live log feed** — every step printed in real time inside the app
- **CSV export** with timestamped results
- Supports **BIST (Turkish)** and **US markets** simultaneously

---

## 🔧 Tech Stack

| Layer | Library |
|---|---|
| Web Scraping (dynamic) | `selenium` + `webdriver-manager` |
| Web Scraping (static) | `requests` + `beautifulsoup4` |
| Data & Indicators | `pandas` + `yfinance` |
| GUI Framework | `customtkinter` |
| Charts | `matplotlib` (embedded via TkAgg) |
| Concurrency | `threading` + `queue` |

---

## 🚀 Installation

```bash
# 1. Clone the repository
git clone https://github.com/YOUR_USERNAME/stock-analysis-system.git
cd stock-analysis-system

# 2. Install dependencies
pip install customtkinter matplotlib selenium beautifulsoup4 pandas requests yfinance webdriver-manager

# 3. Run
python stock_analyzer_gui.py
```

> **Requirements:** Python 3.10+, Google Chrome installed (ChromeDriver auto-downloaded)

---

## 📁 File Structure

```
stock-analysis-system/
├── stock_analyzer_gui.py   # Main GUI application
├── stock_analyzer_en.py    # CLI version (terminal output)
├── README.md
└── preview.png             # Dashboard screenshot
```

---

## 🧠 How the Scoring Works

Each stock is evaluated across 7 signals:

| Signal | Points |
|---|---|
| RSI < 30 (Oversold) | +20 |
| MACD Positive Crossover | +20 |
| Price above MA20 > MA50 | +15 |
| Strong 5-day Momentum (>3%) | +15 |
| Price at Bollinger Lower Band | +10 |
| Volume spike (>1.5x average) | +10 |
| Low P/E Ratio (<20) | +10 |

| Score Range | Signal |
|---|---|
| 75 – 100 | 🚀 STRONG BUY |
| 60 – 74 | 📈 BUY |
| 40 – 59 | ⏳ HOLD |
| 25 – 39 | 📉 CAUTIOUS SELL |
| 0 – 24 | 🔴 SELL |

---

## ⚠️ Disclaimer

This tool is for **educational and portfolio demonstration purposes only**.  
It is **not financial advice**. Always do your own research before making investment decisions.

---

## 👤 Author

**Hacer B.** — Python Automation & Data Extraction Specialist  
[Upwork Profile](https://www.upwork.com/freelancers/~YOUR_PROFILE_ID)

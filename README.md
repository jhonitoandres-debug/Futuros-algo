# Futuros Algo — EMA + RSI + ATR

Estrategia algorítmica para futuros en TradingView (Pine Script v6): entradas por cruce de EMAs con filtro de RSI, salidas con Stop Loss y Take Profit basados en ATR.

Algorithmic futures strategy for TradingView (Pine Script v6): EMA-crossover entries with RSI filter, ATR-based Stop Loss and Take Profit exits.

---

## 🇪🇸 Español

### Qué hace

Este script detecta oportunidades de trading en futuros siguiendo la tendencia:

- **Entradas LONG/SHORT** cuando la EMA rápida (9) cruza la EMA lenta (21), confirmadas por el RSI.
- **Filtro RSI:** solo LONG si RSI ≥ 50, solo SHORT si RSI ≤ 50 (evita operar contra el momentum).
- **Salidas automáticas:** Stop Loss a 1.5 × ATR y Take Profit a 3.0 × ATR desde la entrada (relación riesgo/beneficio 1:2).
- **Filtro de sesión:** opera solo en el horario configurado (por defecto 9:30–16:00, horario de Nueva York).
- **Panel en pantalla** con RSI, ATR, tendencia y posición actual.
- **Alertas** configurables para LONG y SHORT (integrables con webhooks o bots).

### Parámetros principales

| Parámetro | Valor por defecto | Descripción |
|---|---|---|
| EMA rápida / lenta | 9 / 21 | Cruce que genera la señal |
| Filtro RSI | activado, 14, umbral 50 | Confirma momentum |
| Stop Loss | 1.5 × ATR (14) | Riesgo por operación |
| Take Profit | 3.0 × ATR | Objetivo por operación |
| Trailing stop | desactivado | Opcional, 2.0 × ATR |
| Sesión | 09:30–16:00 | Solo opera en ese horario |
| Contratos | 1 | Tamaño de posición |

Todos los parámetros son ajustables desde la configuración del script en TradingView.

### Instalación

1. Abre [TradingView](https://www.tradingview.com) y entra al gráfico del futuro que quieras (ej: `NQ1!`).
2. Abajo, abre el **Editor de Pine** → **Abrir** → **Nuevo script en blanco**.
3. Pega el contenido de `futures_algo_tradingview.pine`.
4. Clic en **Agregar al gráfico**.
5. Usa el **Probador de estrategias** para ver el backtest.

### Uso

- **Backtest:** cambia de timeframe (1m, 5m, 15m, 30m) y ajusta los parámetros para tu activo.
- **Alertas en vivo:** clic derecho sobre el gráfico → **Agregar alerta** → elige "🟢 Señal LONG" o "🔴 Señal SHORT".
- **Sin martingala:** 1 contrato por operación, sin piramidación (`pyramiding=0`).

### Estructura del repo

```
├── futures_algo_tradingview.pine  # Estrategia (Pine Script v6)
├── README.md                      # Esta documentación
├── .gitignore                     # Protección: nunca subir API keys
└── LICENSE                        # MIT
```

### Seguridad

Este proyecto no usa API keys (Pine Script corre dentro de TradingView). Para futuros proyectos en Python: las claves van en un archivo `.env` que **nunca** se sube a GitHub — el `.gitignore` de este repo ya lo protege.

### Descargo de responsabilidad

Proyecto educativo. No es asesoría financiera. Opera futuros bajo tu propio riesgo y valida cualquier estrategia en cuenta demo antes de usar dinero real.

---

## 🇬🇧 English

### What it does

This script spots futures trading opportunities by following the trend:

- **LONG/SHORT entries** when the fast EMA (9) crosses the slow EMA (21), confirmed by RSI.
- **RSI filter:** LONG only if RSI ≥ 50, SHORT only if RSI ≤ 50 (avoids trading against momentum).
- **Automatic exits:** Stop Loss at 1.5 × ATR and Take Profit at 3.0 × ATR from entry (1:2 risk/reward).
- **Session filter:** trades only during the configured hours (default 09:30–16:00 New York time).
- **On-screen dashboard** with RSI, ATR, trend and current position.
- **Configurable alerts** for LONG and SHORT (webhook/bot compatible).

### Key parameters

| Parameter | Default | Description |
|---|---|---|
| Fast / slow EMA | 9 / 21 | Crossover that triggers the signal |
| RSI filter | on, 14, threshold 50 | Momentum confirmation |
| Stop Loss | 1.5 × ATR (14) | Risk per trade |
| Take Profit | 3.0 × ATR | Target per trade |
| Trailing stop | off | Optional, 2.0 × ATR |
| Session | 09:30–16:00 | Trades only in this window |
| Contracts | 1 | Position size |

All parameters are adjustable from the script settings in TradingView.

### Installation

1. Open [TradingView](https://www.tradingview.com) and load your futures chart (e.g. `NQ1!`).
2. At the bottom, open the **Pine Editor** → **Open** → **New blank script**.
3. Paste the contents of `futures_algo_tradingview.pine`.
4. Click **Add to chart**.
5. Use the **Strategy Tester** to see the backtest.

### Usage

- **Backtest:** switch timeframes (1m, 5m, 15m, 30m) and tune the parameters for your asset.
- **Live alerts:** right-click the chart → **Add alert** → pick "🟢 Señal LONG" or "🔴 Señal SHORT".
- **No martingale:** 1 contract per trade, no pyramiding (`pyramiding=0`).

### Security

This project uses no API keys (Pine Script runs inside TradingView). For future Python projects: keys go in a `.env` file that is **never** pushed to GitHub — this repo's `.gitignore` already protects it.

### Disclaimer

Educational project. Not financial advice. Trade futures at your own risk and validate any strategy on a demo account before using real money.

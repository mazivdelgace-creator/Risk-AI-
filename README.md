# Risk-AI-
Optimizador cuantitativo de cartera que compara Random Forest y KNN sobre precios reales en vivo de la API pública de Binance. Incluye escudo de volatilidad que ajusta la exposición y reserva en USDT, validación temporal fuera de muestra con test Diebold-Mariano y auditoría con Gemini. Proyecto educativo, no es asesoría financiera.
RiskSignal AI

Optimizador cuantitativo de cartera que compara Random Forest y KNN sobre precios reales en vivo de la API pública de Binance, con escudo de volatilidad y auditoría estadística con Gemini.

Proyecto de análisis y aprendizaje. No es una recomendación de inversión.

Qué hace
Cartera óptima RF vs. KNN: calcula asignaciones multiactivo con matriz de covarianza y pronóstico a 7 días, y las compara contra Markowitz (media-varianza) y una cartera equiponderada 1/N.
Escudo de volatilidad en vivo: clasifica el régimen de volatilidad (Baja, Media, Alta) y ajusta la exposición. En régimen ALTA expande automáticamente la reserva en USDT.
Auditoría cuantitativa con Gemini: interpreta los resultados de la validación en lenguaje claro.
Mercado BTC 15m: velas de 15 minutos con RSI, MACD, ATR y Bollinger, régimen de volatilidad, señal técnica del modelo y niveles de stop loss y take profit basados en ATR.
Controles
Capital total (mínimo $100) y perfil de riesgo: Conservador, Balanceado o Crecimiento.
Vista del modelo: RF vs. KNN, solo Random Forest o solo KNN.
Tres pestañas: Cartera Óptima, Métricas de Validación y Mercado BTC 15m.
Metodología de validación
Validación cruzada temporal con TimeSeriesSplit (4 folds expansivos), con entrenamiento estrictamente causal y sin fuga al futuro.
Evaluación fuera de muestra sobre retornos diarios reales de Binance.
Métricas: RMSE del retorno, acierto direccional, F1-macro del régimen, matriz de confusión, VaR 95% a 1 día, drawdown máximo y ratio Sharpe.
Test de Diebold-Mariano para saber si la diferencia de error entre RF y KNN es estadísticamente significativa.
Validación por activo (BTC, ETH, SOL, BNB, XRP, ADA, AVAX, entre otros) en Binance Spot.
Resultados de ejemplo

Corrida del 18 de noviembre de 2026, con 35 días fuera de muestra y $10,000 en perfil Balanceado:

Métrica	Random Forest	KNN
RMSE del retorno	0.2017	0.2470
Diebold-Mariano	−6.64 (p = 0.0001)	n/a
Acierto direccional	20.1%	12.5%
F1-macro (en vivo)	0.366	0.355

En esa ventana, que fue bajista, las cuatro estrategias (RF, KNN, Markowitz y 1/N) tuvieron retorno negativo.

Limitaciones
La ventana fuera de muestra es corta (35 días) y corresponde a un solo régimen de mercado.
Un menor RMSE que KNN no equivale a superar al mercado: el R² fuera de muestra fue negativo y el acierto direccional es bajo.
Los resultados cambian con cada corrida porque usan precios en vivo.
Stack

[Por completar: lenguajes, frameworks y librerías de ML que usa el proyecto]

Cómo ejecutarlo

[Por completar: instalación y comandos]

Aviso

Este proyecto es solo informativo y educativo. No constituye asesoría financiera ni una recomendación de compra o venta de ningún activo.

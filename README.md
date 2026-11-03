# Radar Chuva IA

Previsão de chuva em um único arquivo HTML, feita para o celular e para quem é daltônico.

**Abrir:** https://drill23.github.io/radar-chuva-ia/

## O que faz

- **Medidor de 0 a 100%** com a chance de chover nas próximas 3, 6, 12, 24, 48 ou 72 horas.
- **Quatro intensidades:** baixa, moderada, severa e temporal perigoso. Cada uma tem cor, textura e nome, então nada depende só da cor.
- **Mapa** de chuva acumulada com os números em milímetros, radar ao vivo e toque em qualquer ponto para ver a previsão dele.
- **Semana** com a chance e a intensidade de cada dia.
- **Modelos** com o voto de cada um e o consenso final, e um resumo opcional escrito pelo Gemini.

## Como a chance é calculada

Cada modelo roda dezenas de cenários diferentes. A chance de um modelo é a fração desses cenários em que chove pelo menos 0,2 mm na janela escolhida. O resultado final é a média ponderada dos modelos:

| Modelo | Tipo | Cenários | Peso |
|---|---|---|---|
| Google WeatherNext 2 | IA | 64 | 30% |
| ECMWF AIFS | IA | 51 | 22% |
| ECMWF IFS | Física | 51 | 18% |
| DWD ICON | Física | 40 | 12% |
| NOAA AIGEFS | IA | 31 | 10% |
| NOAA GEFS | Física | 31 | 8% |

A intensidade usa limiares de chuva acumulada (1, 10, 30 e 60 mm em 24 h), ajustados ao tamanho da janela. Energia para tempestade (CAPE), rajadas de vento e sinal de trovoada podem elevar a classe.

## Fontes (todas gratuitas, sem chave)

- Previsões: [Open-Meteo](https://open-meteo.com) (uso não comercial)
- Radar: [RainViewer](https://www.rainviewer.com)
- Mapa: OpenStreetMap e CARTO
- Resumo por IA (opcional): Gemini, com chave grátis do Google AI Studio, guardada só no aparelho

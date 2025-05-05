# Análise de Benford em Imagens

[![Python](https://img.shields.io/badge/python-3.6+-blue.svg)](https://www.python.org/downloads/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![GitHub Stars](https://img.shields.io/github/stars/deldotore-r/benford_01?style=social)](https://github.com/deldotore-r/benford_01)
[![GitHub Forks](https://img.shields.io/github/forks/deldotore-r/benford_01?style=social)](https://github.com/deldotore-r/benford_01)

Apresento neste repositório uma ferramenta Python para analisar imagens digitais e verificar sua conformidade com a Lei de Benford, utilizando a Transformada Discreta de Coseno (DCT) ou a Transformada Wavelet Discreta (DWT) para decompor a imagem em componentes de frequência. Esta análise pode ser utilizada para detectar manipulações, identificar características de imagens geradas por inteligência artificial ou para caracterizar propriedades intrínsecas de diferentes tipos de imagens.

## Sobre a Lei de Benford

<p align="center">
  <img src="assets/Benford_graph.png" alt="Gráfico de Benford" width="400">
</p>

A Lei de Benford, também conhecida como Lei do Primeiro Dígito, é um fenômeno estatístico onde em muitos conjuntos de dados numéricos do mundo real, o primeiro dígito significativo segue uma distribuição logarítmica específica:

- O dígito 1 aparece como primeiro dígito em cerca de 30.1% das vezes
- O dígito 2 aparece como primeiro dígito em cerca de 17.6% das vezes
- O dígito 3 aparece como primeiro dígito em cerca de 12.5% das vezes
- ...e assim por diante, com frequências menores para dígitos maiores

Esta lei tem aplicações em auditoria financeira, detecção de fraudes, análise científica e, como explorado neste projeto, na análise de propriedades estatísticas de imagens digitais através da análise dos coeficientes de frequência obtidos por DCT ou DWT.

## Como a Lei de Benford se Aplica a Imagens (via Transformações de Frequência)

Neste projeto, a análise da Lei de Benford é aplicada aos **coeficientes de frequência** obtidos através da **Transformada Discreta de Coseno (DCT)** ou da **Transformada Wavelet Discreta (DWT)** da imagem. A ideia é que a distribuição dos primeiros dígitos desses coeficientes possa revelar padrões característicos de imagens naturais versus manipuladas ou geradas artificialmente.

O projeto implementa um algoritmo para:

1. **Decompor a imagem:** Aplicar DCT ou DWT para obter os coeficientes de frequência.
2. **Extrair os primeiros dígitos:** Obter o primeiro dígito significativo dos coeficientes de cada subband (no caso da DWT).
3. **Calcular a distribuição observada:** Determinar a frequência de cada primeiro dígito nos coeficientes.
4. **Comparar com a distribuição teórica:** Utilizar métricas como Divergência de Kullback-Leibler, Distância de Bhattacharyya e Coeficiente de Correlação de Pearson para quantificar a similaridade entre a distribuição observada e a distribuição de Benford.
5. **Visualizar os resultados (opcional):** Plotar as distribuições para comparação visual.

## Instalação

```bash
# Clonar o repositório
git clone [https://github.com/deldotore-r/benford_01.git](https://github.com/deldotore-r/benford_01.git)
cd benford_01

# Criar e ativar um ambiente virtual (recomendado)
python -m venv venv
source venv/bin/activate  # No Linux/macOS
venv\Scripts\activate  # No Windows

# Instalar dependências
pip install -r requirements.txt

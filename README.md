# Análise de Benford em Imagens


Apresento neste repositório uma ferramenta Python para analisar imagens digitais e verificar sua conformidade com a Lei de Benford, que pode ser utilizada para detectar manipulações ou para caracterizar propriedades intrínsecas das imagens.

## Sobre a Lei de Benford

<p align="center">
  <img src="assets/Benford_graph.png" alt="Gráfico de Benford" width="400">
</p>

A Lei de Benford, também conhecida como Lei do Primeiro Dígito, é um fenômeno estatístico onde em muitos conjuntos de dados numéricos do mundo real, o primeiro dígito significativo segue uma distribuição logarítmica específica:

- O dígito 1 aparece como primeiro dígito em cerca de 30.1% das vezes
- O dígito 2 aparece como primeiro dígito em cerca de 17.6% das vezes
- O dígito 3 aparece como primeiro dígito em cerca de 12.5% das vezes
- ...e assim por diante, com frequências menores para dígitos maiores

Esta lei tem aplicações em auditoria financeira, detecção de fraudes, análise científica e, como explorado neste projeto, na análise de propriedades estatísticas de imagens digitais.

## Como a Lei de Benford se Aplica a Imagens

Em imagens digitais, podemos analisar os valores dos pixels, coeficientes de transformadas (como DCT ou wavelets), gradientes, ou outros atributos extraídos da imagem. Curiosamente, imagens naturais não manipuladas tendem a seguir a Lei de Benford para certos parâmetros, enquanto imagens manipuladas ou geradas artificialmente podem apresentar desvios significativos.

Este projeto implementa um algoritmo para:

1. Extrair características relevantes da imagem;
2. Analisar a distribuição do primeiro dígito;
3. Comparar com a distribuição esperada pela Lei de Benford;
4. Visualizar e quantificar os resultados.

## Instalação

```bash
# Clonar o repositório
git clone https://github.com/deldotore-r/benford_01.git
cd benford_01 

# Instalar dependências
pip install -r requirements.txt
```

## Exemplos de Resultados

Abaixo estão alguns exemplos de análises conduzidas com esta ferramenta:

### Imagem Natural Não Manipulada

<p align="left">
  <img src="assets/benford_natural.png" alt="Imagem natural" width="550">
</p>

*Observe como a distribuição (barras azuis) segue de perto a Lei de Benford esperada (linha vermelha).

### Imagem criada por IA

<p align="left">
  <img src="assets/benford_manipulada.png" alt="Imagem criada por IA" width="550">
</p>

*Note o desvio significativo da Lei de Benford, particularmente nos dígitos 1 e 2.

## Implementação

O código-fonte principal implementa os seguintes componentes:

1. Extração do primeiro dígito;
2. Análise do Primeiro Dígito;
3. Métricas de Conformidade;
4. Visualização.

Trecho inicial do código principal:

```python
import cv2
import numpy as np
import matplotlib.pyplot as plt
from collections import Counter
import math

# Função para extrair o primeiro dígito
def first_digit(n):
    while n >= 10:
        n //= 10
    return n

# Função para calcular a distribuição de Benford
def benford_distribution():
    return [math.log10(1 + 1/d) for d in range(1, 10)]

# Carregar imagem em tons de cinza
image = cv2.imread('C:/Benford_S.png', cv2.IMREAD_GRAYSCALE)

# Flatten (transforma matriz em vetor)
pixels = image.flatten()

# Remove zeros (não são úteis para Benford)
pixels = pixels[pixels > 0]

# Extrair primeiros dígitos
first_digits = [first_digit(val) for val in pixels]
        
    # ... (código continua)
```

O código completo está disponível [neste Gist](https://gist.github.com/deldotore-r/aed560d2e228194200161b042ef37bdb).

## Aplicações

Este projeto pode ser útil para:

- Identificação de imagens manipuladas digitalmente;
- Estudo de propriedades estatísticas de diferentes tipos de imagens;
- Aprendizado sobre processamento de imagens e estatística aplicada;
- Detecção de imagens geradas por IA versus fotografias reais;
- Análise forense de imagens digitais.

## Licença

Este projeto está licenciado sob a licença MIT - veja o arquivo [LICENSE](LICENSE) para detalhes.



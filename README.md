# Detecção de Elementos Arquitetônicos em Plantas Baixas

Este repositório contém a solução desenvolvida para a disciplina de Processamento de Imagens. O objetivo é identificar e segmentar elementos estruturais (paredes, portas e janelas) em imagens de plantas baixas digitalizadas.

## 📺 Apresentação em Vídeo

[Insira aqui o Link para o seu vídeo no YouTube]
> Clique no link acima para ver a explicação detalhada da solução e dos resultados (Máx 15min).

## 🛠️ Tecnologias Utilizadas

O projeto foi desenvolvido em Python utilizando **Jupyter Notebooks**. As principais bibliotecas empregadas foram:
* **Numpy:** Manipulação matricial.
* **Matplotlib:** Visualização dos dados.
* **Scikit-Image (skimage):** Processamento de imagens e transformadas.
* **Scipy:** Operações de convolução e filtros.

## 🚀 Metodologia

A solução foi dividida nas seguintes etapas:

1.  **Pré-processamento:** Binarização e inversão da imagem original para destacar os traços.
2.  **Morfologia Matemática:**
    * Aplicação de **Abertura e Fechamento** para remover ruídos e conectar falhas nas paredes.
3.  **Segmentação de Paredes:** Uso do **Filtro de Sobel** para detectar as bordas e gradientes das estruturas principais.
4.  **Detecção de Portas (Curvas):** Implementação de uma **Transformada de Hough Circular Restrita**, onde a busca por centros de arcos é limitada às coordenadas das paredes, reduzindo falsos positivos.
5.  **Detecção de Portas (Reta):** Uso de **Transformada de Hough Linear** para identificar a parte reta contida nas portas.
6.  **Limpeza:** Remoção de textos e cotas baseada em propriedades geométricas (área, solidez e excentricidade).

## 📂 Estrutura do Repositório

* `notebooks/`: Contém os códigos fontes documentados (`.ipynb`).
* `data/`: Imagens originais utilizadas nos testes.
* `results/`: Resultados visuais gerados pelo algoritmo.

## Resultados Obtidos

### Detecção de Portas (Hough Circular + Hough Linear)
![Portas Detectadas](./results/portas_hough.png)
*(Sugestão: Salve a imagem final do seu código com os arcos verdes e coloque na pasta results)*

### Detecção de Paredes (Sobel)
![Paredes Sobel](./results/sobel_final.png)

## Autores

* **[Bernardo Silva Luz]** - *Desenvolvimento e Documentação*
* **[Madson Silva]** - *Desenvolvimento e Documentação*

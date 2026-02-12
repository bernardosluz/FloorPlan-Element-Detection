# FloorPlan-CV-Analysis: Detecção de Elementos Arquitetônicos em Plantas Baixas

Este repositório contém a solução desenvolvida para a disciplina de Processamento de Imagens. O objetivo é identificar e segmentar elementos estruturais (paredes, portas e janelas) em imagens de plantas baixas digitalizadas.

## 📺 Apresentação em Vídeo

[Insira aqui o Link para o seu vídeo no YouTube]
> Clique no link acima para ver a explicação detalhada da solução e dos resultados (Máx 15min).

## 👥 Autores

* **Bernardo Silva Luz** (Matrícula: 202200092389)
* **Madson Silva**
* **Professor:** Leonardo N.

## 📄 Descrição dos Arquivos

O projeto está dividido em dois notebooks principais:

### 1. `Deteccao_Planta_Baixa_Detalhado.ipynb` (Relatório Técnico)
Este é o notebook de desenvolvimento e exploração. Ele contém:
* **Passo-a-passo explicado:** Desde o carregamento da imagem até à visualização final.
* **Visualizações Intermediárias:** Plots que mostram o resultado de cada filtro (Sobel, Morfologia, Hough).
* **Implementações Manuais:** Código detalhado das transformadas e filtros.
* *Ideal para:* Entender a lógica, a matemática e o funcionamento do algoritmo.

### 2. `Deteccao_Planta_Baixa.ipynb` (Script de Processamento em Lote)
Este notebook foi otimizado para produção. Ele contém:
* **Automação:** Percorre automaticamente uma pasta de imagens.
* **Sem Interface Gráfica:** Configurado com backend `Agg` do Matplotlib para salvar os resultados diretamente em disco.
* *Ideal para:* Processar múltiplas plantas de uma só vez.

## 🛠️ Tecnologias e Bibliotecas

O projeto foi desenvolvido em **Python 3**. As principais dependências são:

* **Numpy:** Manipulação matricial e operações vetoriais.
* **Matplotlib:** Visualização de dados.
* **Scikit-Image (skimage):** Leitura e pré-processamento.
* **Scipy:** Operações de convolução (para o Sobel) e morfologia.

## 🚀 Metodologia

A solução aborda o problema em etapas sequenciais, com destaque para a validação cruzada geométrica na detecção de portas:

1.  **Pré-processamento:**
    * Binarização e inversão da imagem.
    * Aplicação de **Morfologia Matemática** (Abertura/Fechamento) para redução de ruído e esqueletização para obter traços finos.

2.  **Detecção de Paredes (Walls):**
    * Utilização do **Filtro de Sobel** para calcular a magnitude do gradiente.
    * Segmentação baseada em limiares de intensidade para isolar as estruturas retangulares rígidas.

3.  **Detecção de Portas (Doors) - A Inovação do Projeto:**
    A detecção de portas utiliza uma abordagem híbrida de **Fusão de Evidências**:
    
    * **A. Transformada de Hough Circular Restrita:** Identifica o "movimento" da porta (o arco). A busca pelos centros é restrita às coordenadas das paredes (dobradiças), reduzindo drasticamente o espaço de busca e falsos positivos.
        
    * **B. Transformada de Hough Linear (Implementação Personalizada):**
        Diferente da implementação padrão (que detecta retas infinitas), desenvolvemos um algoritmo que detecta **segmentos finitos** (a folha da porta). Ele percorre a reta pixel a pixel e verifica a continuidade, quebrando a linha caso encontre "buracos" (gaps) maiores que a tolerância definida.
        
    * **C. Validação Cruzada (Arco + Reta):**
        Uma porta só é confirmada se houver a intersecção geométrica das duas evidências: um arco detectado próximo a um segmento de reta. Isso elimina falsos positivos como mobílias curvas (tem arco, mas não tem reta) ou janelas (tem reta, mas não tem arco).

4.  **Pós-processamento:**
    * Limpeza de ruídos, textos e cotas utilizando análise de propriedades de regiões (`regionprops` baseada em área e excentricidade).
---
*Projeto desenvolvido para a disciplina de Processamento de Imagens - 2025.2
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

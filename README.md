# Reconhecimento de Gênero Musical

## I. Introdução (W11 - 07/11/2024)

Este trabalho aborda a classificação automática de músicas em gêneros como jazz, rock e clássico, utilizando técnicas de processamento digital de sinais e aprendizado de máquina. Com o aumento da quantidade de músicas disponíveis em plataformas de streaming, a categorização automática em gêneros facilita a organização de bibliotecas, a personalização de recomendações e a busca em arquivos de áudio [1]. Nosso objetivo é identificar características dos sinais de áudio, como frequência, ritmo, timbre e melodia, que possam ser utilizadas para distinguir padrões de cada gênero, desenvolvendo modelos de classificação de alta precisão e aplicabilidade prática.

Para isso, usaremos o **GTZAN Music Genre Dataset** [2], amplamente reconhecido em pesquisas de classificação de gêneros musicais, e faremos uma revisão da literatura sobre extração de características e algoritmos de classificação de áudio. Nossa metodologia inclui análise de espectrogramas e técnicas de detecção de timbre e ritmo, além de modelos de aprendizado como **SVM**, **KNN** e **Redes Neurais Convolucionais (CNNs)**. Avaliaremos o desempenho dos modelos com métricas como acurácia, matriz de confusão, F-score e benchmarks da literatura, buscando identificar as abordagens mais eficazes para a classificação de gêneros musicais.

## Referências

[1] X. Cai e H. Zhang, “Music genre classification based on auditory image, spectral and acoustic features”, *Multimedia Syst.*, janeiro de 2022. Acesso em 05/11/2024. Disponível: [https://doi.org/10.1007/s00530-021-00886-3](https://doi.org/10.1007/s00530-021-00886-3)  
[2] “GTZAN Dataset - Music Genre Classification”. *Kaggle: Your Machine Learning and Data Science Community*. Acesso em 05/11/2024. Disponível: [https://www.kaggle.com/datasets/andradaolteanu/gtzan-dataset-music-genre-classification/data](https://www.kaggle.com/datasets/andradaolteanu/gtzan-dataset-music-genre-classification/data)

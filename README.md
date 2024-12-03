# INF0413 - Processamento Digital de Sinais e Imagens

Equipe: 1

GEOVANA TEIXEIRA CAMARGO - 202303338

JAIR MARTINS SANTIAGO NETO - 202300619

LIDIA RAKEL ALCANTARA DO VALE - 202305743

MIRMILA SOCRATES DO NASCIMENTO - 202306723

NATÃ MILHOMEM LEMOS - 202305744


# Reconhecimento de Gênero Musical

## I. Introdução (W11 - 07/11/2024)

Este trabalho aborda a classificação automática de músicas em gêneros como jazz, rock e clássico, utilizando técnicas de processamento digital de sinais e aprendizado de máquina. Com o aumento da quantidade de músicas disponíveis em plataformas de streaming, a categorização automática em gêneros facilita a organização de bibliotecas, a personalização de recomendações e a busca em arquivos de áudio [1]. Nosso objetivo é identificar características dos sinais de áudio, como frequência, ritmo, timbre e melodia, que possam ser utilizadas para distinguir padrões de cada gênero, desenvolvendo modelos de classificação de alta precisão e aplicabilidade prática.

Para isso, usaremos o **GTZAN Music Genre Dataset** [2], amplamente reconhecido em pesquisas de classificação de gêneros musicais, e faremos uma revisão da literatura sobre extração de características e algoritmos de classificação de áudio. Nossa metodologia inclui análise de espectrogramas e técnicas de detecção de timbre e ritmo, além de modelos de aprendizado como **SVM**, **KNN** e **Redes Neurais Convolucionais (CNNs)**. Avaliaremos o desempenho dos modelos com métricas como acurácia, matriz de confusão, F-score e benchmarks da literatura, buscando identificar as abordagens mais eficazes para a classificação de gêneros musicais.

## II. Fundamentos Teóricos (W14 - 28/11/2024)

O reconhecimento de gênero musical é uma tarefa complexa que combina processamento avançado de sinais de áudio e aprendizado de máquina, sendo amplamente aplicado em sistemas de recomendação e organização de bibliotecas musicais digitais. Abordamos conceitos fundamentais que sustentam as técnicas empregadas, detalhando mecanismos, algoritmos e estratégias de avaliação.

A biblioteca Librosa desempenha um papel central na análise e visualização dos sinais de áudio, permitindo a extração de características relevantes, como coeficientes Mel-Frequency Cepstral Coefficients (MFCCs), energia, ritmo e espectrogramas, que servem como base para a classificação de gêneros musicais (Athulya, 2021). É necessária a extração e exploração de características acústicas utilizando técnicas como:

Coeficientes Mel-Frequency Cepstral Coefficients (MFCCs): Representam a envoltória espectral de um sinal, capturando o timbre e a tonalidade. Essa técnica é amplamente reconhecida por seu alinhamento com a percepção humana de sons (Logan, 2000). A análise demonstra que a Transformada Discreta do Cosseno é adequada para correlacionar espectros tanto de fala quanto de música.

 ![image](https://github.com/user-attachments/assets/6c025228-b119-45ab-8a2c-ddd0778f4428)

A Figura ilustra o processo de extração das características MFCC. O sinal de áudio é segmentado em quadros, aplicando-se uma função de janela em intervalos regulares. Esse procedimento visa modelar pequenas partes do sinal (geralmente com duração de 20 ms), que são consideradas estatisticamente estacionárias. Como resultado, é gerado um vetor de características cepstrais (Estruturas periódicas em espectros de frequência) para cada quadro processado.
Espectrogramas: Um sistema, baseado em uma Rede Neural Convolucional (CNN), processa espectrogramas de trechos de músicas para extrair características relevantes. Utilizando o dataset GTZAN é possível obter alta acurácia (94%) na classificação de gêneros (Athulya, 2021). 

O sistema utiliza redes neurais convolucionais (CNNs) para processar espectrogramas, que são representações visuais da energia do áudio em diferentes frequências ao longo do tempo. As CNNs são eficazes nessa tarefa porque podem capturar padrões espaciais e temporais nos espectrogramas, associando características específicas a gêneros musicais. O uso de espectrogramas permite que o modelo aproveite informações detalhadas sobre o timbre, ritmo e frequência, fundamentais para diferenciar gêneros musicais (Tzanetakis, 2019). Essa abordagem melhora a precisão na classificação quando comparada a métodos baseados apenas em características numéricas.

Diversos modelos foram utilizados para comparar abordagens e identificar a melhor solução para o problema:

KNN e Logistic Regression são classificadores de aprendizado de máquina tradicionais usados para classificação de gênero musical (SINGH, 2022). K-Nearest Neighbors baseia-se na similaridade entre as amostras, medindo distâncias como a euclidiana para classificar os gêneros. Logistic Regression é um modelo estatístico que estima a probabilidade de uma música pertencer a um gênero.

Decision Tree que é uma estrutura hierárquica baseada em decisões sobre atributos musicais. Isso permite identificar critérios relevantes para a classificação. A partir disso a Random Forest constrói múltiplas árvores de decisão e combina os resultados. A vantagem é que o modelo generaliza bem, é robusto contra ruído e evita sobreajuste.

CatBoost que é um algoritmo de aprendizado de máquina que tem ganhado popularidade nos últimos anos, especialmente na área de classificação de gêneros musicais. O nome "CatBoost" é uma abreviação de "Category Boosting", o que destaca sua capacidade de lidar eficientemente com variáveis categóricas, um tipo de dado comum nesse tipo de classificação (Salihu, 2023). Pode ser usado para construir modelos que classificam músicas em diferentes gêneros com base em suas letras. As letras são processadas e transformadas em características numéricas que servem de entrada para o algoritmo.  Após o treinamento, o modelo pode prever o gênero de novas músicas com base em suas letras.

Avaliação

A avaliação de modelos em tarefas de classificação, como a de gêneros musicais, é uma etapa essencial para medir sua eficácia e identificar áreas de melhoria. Em problemas de aprendizado de máquina, a avaliação permite verificar se o modelo treinado é capaz de generalizar adequadamente para dados desconhecidos, que representam casos reais.

Dentre as métricas comumente utilizadas, a acurácia é uma das mais populares e mede a proporção de previsões corretas em relação ao total de amostras testadas. Formalmente, é expressa como a razão entre o número de acertos e o número total de testes.

Embora simples e intuitiva, a acurácia pode ser enganosa em conjuntos de dados desbalanceados. Por exemplo, se um gênero musical domina o conjunto de dados, o modelo pode obter uma alta acurácia apenas por prever consistentemente a classe majoritária, mesmo sem aprender padrões significativos das outras classes (Ndou, 2021). Por isso, métricas adicionais são frequentemente utilizadas para complementar a análise, como visualizações de Desempenho que pode ser essencial. Gráficos que mostram a evolução da acurácia e do erro para os conjuntos de treinamento e validação são amplamente utilizados. Esses gráficos ajudam a diagnosticar problemas como overfitting (quando o modelo se ajusta excessivamente aos dados de treinamento e perde capacidade de generalização) e underfitting (quando o modelo é incapaz de capturar padrões significativos nos dados).

Por exemplo, uma grande diferença entre a acurácia no treinamento e na validação pode indicar overfitting, enquanto baixos valores de acurácia em ambos os conjuntos sugerem underfitting. Esses insights podem orientar ajustes nos hiperparâmetros, como o número de árvores em algoritmos de boosting, a taxa de aprendizado ou mesmo os métodos de pré-processamento e seleção de características.


## III. Metodologia (W12 - 14/11/2024)

Primeiramente, a base de dados foi composta por trechos de áudio de 30 segundos, categorizados em diferentes gêneros musicais. Cada amostra possuía características extraídas previamente, como coeficientes mel-freq (MFCCs), energia, espectro de frequência e tempo entre batidas, que foram fundamentais para representar as propriedades acústicas dos gêneros. A manipulação dos dados e a realização das análises exploratórias foram possibilitadas por bibliotecas como pandas e numpy para organização e cálculos, além de matplotlib e seaborn para visualizações detalhadas.

Na etapa de análise exploratória, foi verificada a distribuição das amostras para cada gênero musical utilizando funções como value_counts() do pandas. Foi confirmado o balanceamento da base, ou seja, cada gênero possuía a mesma quantidade de amostras (100 amostras por gênero). Em seguida, para compreender melhor as características dos áudios, formas de onda e espectrogramas foram gerados com a biblioteca librosa. As formas de onda destacaram a amplitude das amostras ao longo do tempo, enquanto os espectrogramas forneceram uma representação visual da energia em diferentes frequências ao longo do tempo, permitindo identificar padrões distintos entre os gêneros.

Em seguida foi realizado o pré-processamento dos dados. Inicialmente, as etiquetas de gênero foram convertidas em valores numéricos utilizando o LabelEncoder da biblioteca scikit-learn, possibilitando o uso das classes como saída nos algoritmos. Além disso, as características numéricas foram escaladas com o MinMaxScaler para normalizá-las em um intervalo comum, evitando que variáveis com amplitudes maiores dominassem o aprendizado. Colunas irrelevantes, como o nome dos arquivos, foram removidas para eliminar dados redundantes. Os dados foram então divididos em conjuntos de treino (70%) e teste (30%) usando a função train_test_split, garantindo a validação cruzada durante a etapa de treinamento.

Para o treinamento dos modelos, foram escolhidos algoritmos representativos com diferentes abordagens de aprendizado. O K-Neighbors Classifier foi configurado para classificar os gêneros com base na proximidade das amostras, utilizando a métrica de distância euclidiana. O Decision Tree foi projetado para dividir os dados recursivamente de acordo com critérios que maximizassem a separação entre os gêneros. O Random Forest, uma combinação de múltiplas Árvores de Decisão, foi implementado para melhorar a robustez e reduzir a variação dos resultados. O Logistic Regression foi aplicado como um modelo probabilístico, adequado para prever a probabilidade de uma amostra pertencer a cada gênero. Além disso, os algoritmos CatBoost e Gradient Boosting foram empregados, com o objetivo de explorar métodos baseados em árvores de decisão com otimizações sequenciais para alcançar maior precisão.

Ao longo do processo de treinamento, os modelos foram ajustados iterativamente com base nas características dos dados de entrada. Cada modelo foi testado quanto à sua capacidade de aprendizado e generalização.

A metodologia também incluiu a implementação de uma rede neural utilizando a biblioteca TensorFlow, com uma arquitetura simples, porém eficiente. A rede foi definida através do modelo sequencial, contendo as seguintes camadas: uma camada de entrada Flatten, que transforma os dados de entrada em uma única dimensão, seguida por uma camada densa (Dense) com 256 neurônios e ativação ReLU. Para melhorar o desempenho e a estabilidade do treinamento, foi adicionada uma camada de normalização em lote (BatchNormalization). Em seguida, outra camada densa com 128 neurônios e ativação ReLU foi incorporada, acompanhada por uma camada de dropout (Dropout) com taxa de 0,3 para evitar o overfitting. Por fim, a camada de saída, com 10 neurônios e ativação softmax, foi configurada para realizar a classificação dos gêneros musicais em categorias exclusivas.

## IV. Resultados (W13 - 21/11/2024)

Os resultados obtidos no trabalho demonstraram a eficácia dos diferentes algoritmos de aprendizado de máquina na classificação de gêneros musicais. Durante os testes, foi possível observar que os modelos apresentaram desempenhos variados, refletindo suas características específicas e adaptações aos dados fornecidos.

O algoritmo Random Forest mostrou um bom desempenho geral, alcançando uma acurácia de aproximadamente 78%. Isso é esperado devido à sua abordagem de combinar múltiplas Árvores de Decisão, reduzindo o risco de overfitting e aumentando a robustez do modelo. O CatBoost, por sua vez, destacou-se como o mais preciso, com uma acurácia em torno de 83%, o que evidencia sua eficiência em lidar com dados categóricos e complexidades inerentes ao conjunto de características acústicas. O Gradient Boosting também obteve um desempenho sólido, atingindo cerca de 79%, beneficiando-se de sua abordagem sequencial de otimização.

Os modelos baseados em métodos tradicionais, como o K-Neighbors Classifier e a Logistic Regression, apresentaram resultados ligeiramente inferiores aos métodos baseados em árvores de decisão e ensemble learning. Isso pode ser explicado pela natureza dos dados, que possivelmente favorecem algoritmos mais avançados na detecção de padrões não lineares. Ainda assim, esses modelos demonstraram sua relevância como pontos de comparação no estudo.

Além disso, foi implementada uma rede neural utilizando a biblioteca TensorFlow, com uma arquitetura composta por camadas densas, funções de ativação ReLU e uma camada de saída com softmax. Após o treinamento em 100 épocas, a rede neural alcançou uma acurácia de teste de aproximadamente 75%. Embora inferior ao CatBoost, a rede demonstrou ser promissora para tarefas futuras, considerando sua capacidade de se adaptar a dados maiores ou mais complexos.

## Referências

[1] X. Cai e H. Zhang, “Music genre classification based on auditory image, spectral and acoustic features”, *Multimedia Syst.*, janeiro de 2022. Acesso em 05/11/2024. Disponível: [https://doi.org/10.1007/s00530-021-00886-3](https://doi.org/10.1007/s00530-021-00886-3)  

[2] “GTZAN Dataset - Music Genre Classification”. *Kaggle: Your Machine Learning and Data Science Community*. Acesso em 05/11/2024. Disponível: [https://www.kaggle.com/datasets/andradaolteanu/gtzan-dataset-music-genre-classification/data](https://www.kaggle.com/datasets/andradaolteanu/gtzan-dataset-music-genre-classification/data)

[3] Logan, B. (2000). Mel frequency cepstral coefficients for music modeling. International Symposium on Music Information Retrieval, DOI:https://www.researchgate.net/publication/2552483_Mel_Frequency_Cepstral_Coefficients_for_Music_Modeling

[4] Athulya K., M. & Sindhu, S. "Deep Learning Based Music Genre Classification Using Spectrogram" in Proceedings of the 2nd International Conference on IoT Based Control Networks and Intelligent Systems (ICICNIS 2021), Kerala, India, 2021. DOI: https://papers.ssrn.com/sol3/papers.cfm?abstract_id=3883911

[5] G. Tzanetakis, A. Phan, and P. Cook, "A machine learning approach to music genre classification," Electronics Letters, vol. 56, no. 10, pp. 1234-1236, 2019. DOI: 10.1049/el.2019.4202.

[6] N. Ndou, R. Ajoodha, e A. Jadhav, "Music Genre Classification: A Review of Deep-Learning and Traditional Machine-Learning Approaches," em 2021 IEEE International IOT, Electronics and Mechatronics Conference (IEMTRONICS), Toronto, Canadá, 21-24 de abril de 2021. DOI: https://doi.org/10.1109/IEMTRONICS52119.2021.9422487

[7] SINGH, Y.; BISWAS, A. Robustness of musical features on deep learning models for music genre classification. Expert Systems With Applications, v. 199, p. 116879, 2022. DOI: https://doi.org/10.1016/j.eswa.2022.116879

[8] Salihu, S. A., Lawal, I. O., Abikoye, O. C., Balogun, A. O., Mojeed, H. A., Usman-Hamza, F. E., & Akintola, A. G. (2023). Classification of Music Genres Using Catboost Algorithm. Sule Lamido University Journal of Science and Technology (SLUJST), 7(2), 17–26. https://doi.org/10.56471/slujst.v7i.472.


---

Relatório (em construção): https://docs.google.com/document/d/1iHz3pI4FvJky0d7LNGppfr_xLw6Ff6sDIy70SVVTCck/edit?tab=t.0

Apresentação (em construção): https://www.canva.com/design/DAGVu7yBs3Q/MkV82Y4X_6bRiATIVSwbVQ/edit

# SVM para classificação de dificuldade financeira

## O Dataset

O dataset utilizado para treinar o modelo está disponível na plataforma Kaggle pelo link "https://www.kaggle.com/datasets/shebrahimi/financial-distress". 

O dataset possui um conjunto de dados de empresas de diversos períodos diferentes, sendo a primeira coluna o nome da empresa, a segunda o período e a terceira a dificuldade financeira. Da quarta coluna até a ultima, o conjunto de dados possuí 86 colunas, todas são referentes às características financeiras e não financeiras das empresas no período posterior ao da dificuldade financeira, sendo essas características não especificadas por metadados, nomeadas em sequência de x1 a x83. A coluna x80 é a única referente a uma varíavel categórica.

O conjunto de dados é desbalanceado e assimétrico, possuindo 136 empresas com dificuldades financeiras e 286 empresas saudáveis. Por conta dessas características o dataset nos orienta a utilizar f1-score como métrica de avaliação e de treinar com 70% dos dados, enquanto testamos com 30%.

## Treino do Modelo

O modelo foi treinado com 70% dos dados e testado com 30%, com a divisão realizada por empresa através de GroupShuffleSplit para evitar que registros da mesma empresa aparecessem simultaneamente em treino e teste. Devido ao desbalanceamento entre as classes, o SVM foi treinado com pesos balanceados por classe. Através do GridSearchCV foram testados os kerneis 'linear', 'poly', 'rbf', os parametros C 0.1, 1, 10, 100, os parametros gamma 0.01, 0.1, 1. Os hiperparametros utilizados, seguindo o resultado do GridSearchCV, foram 'C': 1, 'gamma': 0.01, 'kernel': 'poly'.

## Resultados

F1-score: 0.41025641025641024

              precision    recall  f1-score   support

           0       0.99      0.97      0.98      1124
           1       0.33      0.53      0.41        30

    accuracy                            0.96      1154
    macro avg       0.66      0.75      0.69      1154
    weighted avg    0.97      0.96      0.96      1154

Matriz de Confusão:

<img width="390" height="336" alt="image" src="https://github.com/user-attachments/assets/e4d89039-6643-41fb-8295-438cb506008e" />


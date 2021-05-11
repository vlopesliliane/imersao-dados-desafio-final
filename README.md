<a href="https://ibb.co/x2HNNwK"><img src="https://i.ibb.co/BfN99vH/1-Banner-Desafio-Git-Hub.png" alt="1-Banner-Desafio-Git-Hub" border="0"></a>

# Comparação de modelos de Machine Learning na previsão dos Mecanismos de Ação (MoA) e descoberta de novas drogas

##### Base de Dados: Esse projeto foi baseado no desafio do Laboratory Innovation Science at Harvard disponibilizado  inicialmente em uma competição no [Kaggle](https://www.kaggle.com/c/lish-moa/data) e agora no evento de Imersão Dados promovido pela Alura.

## Sumário 

1. Compreensão do conjunto de dados;
2. Análise exploratória e estatística do Conjunto de dados;
4. Pesquisa de modelos de *Machine Learning* aplicáveis;
5. Modelagem aplicação e teste de modelos de *Machine Learning*;
7. Comparação dos resultados de cada modelo;
8. Considerações finais acerca das limitações e melhorias futuras;
9. Referências bibliográficas.


## Escopo do projeto 

O Termo **MoA** é uma abreviação para **Mecanismo de Ação** e se refere a **atividade biológica** observada em uma **molécula** quando acionada por algum composto químico **(fármacos/drogas)**. Assim, nos testes de novos medicamentos são realizados experimentos nos quais células humanas são tratadas com a droga e as **respostas celulares** são analisadas para cada **par fármaco-MoA** são registrados valores numéricos médios que representam a perda logarítmica.

### Problema de Negócio 

Sabendo-se que **cada composto químico** é considerado uma **classe** diferente, tem-se um **problema de classificação** multiclasse, no qual busca-se avaliar se  **Dado um composto e uma assinatura celular, houve algum MoA ativado?**

### Objetivos do projeto

Encontrar um modelo de *Machine Learning* capaz de prever se **Dado um composto e uma assinatura celular algum MoA será ativado**

## Desenvolvimento

### Compreensão do conjunto de dados

Para análise, foram disponibilizados dois conjuntos de dados: **dados_experimentos** e **dados_resultados**. Para fins de estudo, os dados de interesse para teste e análise foram **combinados** em um único conjunto de dados: **dados_combinados**.
Assim, o DataFrame é composto por **23814 linhas/registros** e **879 colunas/atributos**. Cada registro representa um experimento e as colunas definem os atributos de cada um desses experimentos, conforme abaixo: 

| Nome do atributo                 | Tipo    | Descrição                                                                                                            |
|----------------------------------|---------|----------------------------------------------------------------------------------------------------------------------|
| id                               | object  | número único de cada experimento                                                                                     |
| tratamento                       | object  | tipo de tratamento: com droga ou com controle                                                                        |
| tempo                            | int64   | 24, 48 ou 72 horas                                                                                                   |
| dose                             | object  | tipo de dose aplicada: D1 ou D2                                                                                      |
| expressão gênica (g-0 à g-771)   | float64 | processo pelo qual a informação contida nos genes é convertida em moléculas que determinam as propriedades da célula |
| viabilidade celular (c-0 à c-99) | float64 | analisa se uma célula está metabolicamente ativa (sobrevivência celular)                                             |
| n_moa                            | int64   | quantidade de mecanismos de ação (MoA) ativados no experimento                                                       |
| ativo_moa                        | bool    | indica de 1 ou mais mecanismos (Moa) foram ativados  


### Análise exploratória e estatística
### Pesquisa de modelos de *Machine Learning* aplicáveis
### Modelagem aplicação e teste de modelos de *Machine Learning*
### Comparação dos resultados de cada modelo

## Considerações finais acerca das limitações e melhorias futuras

## Referências bibliográficas



**Mergulhe fundo, é apenas o primeiro passo!**

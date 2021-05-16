<a href="https://ibb.co/x2HNNwK"><img src="https://i.ibb.co/BfN99vH/1-Banner-Desafio-Git-Hub.png" alt="1-Banner-Desafio-Git-Hub" border="0"></a>

# Comparação de modelos de *Machine Learning* na previsão dos Mecanismos de Ação (MoA) e descoberta de novas drogas

##### Base de Dados: Esse projeto foi inspirado no desafio do [Laboratory Innovation Science at Harvard](https://lish.harvard.edu/) disponibilizado  inicialmente em uma competição no [Kaggle](https://www.kaggle.com/c/lish-moa/data) e agora no evento de Imersão Dados promovido pela Alura.

## Sumário 

1. [O Paciente](O-Paciente)
2. [A Dor](A-Dor)
3. [O Diagnóstico](O-Diagnostico)
4. [O Remédio](O-Remedio)
5. [A Consulta Médica](A-Consulta-Medica)
    * [A anamnese: Compreensão do conjunto de dados](Compreensao-do-conjunto-de-dados)
    * [Os Exames Laboratoriais: Análise exploratória e estatística do Conjunto de dados](Analise-exploratoria-e-estatistica-do-Conjunto-de-dados)  
6. [O Tratamento: Modelagem aplicação e teste de modelos de *Machine Learning*](Modelagem-aplicacao-e-teste-de-modelos-de-Machine-Learning)
7. [A Receita Médica: Comparação dos resultados de cada modelo](Comparacao-dos-resultados-de-cada-modelo)
8. [O *check-up* médico: Considerações finais acerca das limitações e melhorias futuras](Consideracoes-finais-acerca-das-limitacoes-e-melhorias-futuras)
9. [O Catálogo de Medicamentos: Referências Bibliográficas](Referencias-bibliograficas)

## <a name=“O-Paciente”><a/> :boy: O Paciente

No processo de desenvolvimento de novos medicamentos, os cientistas realizam experimentos nos quais células humanas são previamente tratadas com um medicamento. Nesse processo, as **respostas celulares**, representadas por valores numéricos médios de perda logarítmica, são registradas e analisadas para cada **par fármaco-MoA**. O Termo **MoA** é uma abreviação para **Mecanismo de Ação** e se refere a **atividade biológica** observada em uma **molécula** quando acionada por algum composto químico **(medicamentos/fármacos/drogas)**. 

Os cientistas buscam então identificar um **alvo proteico** associado a uma doença e desenvolver uma molécula que possa modular essa proteína alvo, tratando a doença.

### <a name=“A-Dor”><a/> :boom: A Dor 

O alto custo humano envolvido na análise e busca de semelhanças as respostas celulares com padrões conhecidos em grandes bancos de dados genômicos, como bibliotecas de expressão gênica ou padrões de viabilidade celular de drogas, com MoAs conhecidos.

### <a name=“O-Diagnostico”><a/> :mag: O Diagnóstico

Sabendo-se que **cada composto químico** pode ser considerado uma **classe** diferente tem-se, no presente estudo de caso, um **problema de classificação** multiclasse.

### <a name=“O-remedio”><a/> :pill: O Remédio

Encontrar um modelo de *Machine Learning* capaz de prever se **Dado um composto e uma assinatura celular algum MoA será ativado**.

## <a name=“A-Consulta-Medica”><a/> :hospital: A Consulta Médica

### <a name=“Compreensao-do-conjunto-de-dados”><a/> :bookmark_tabs: A Anamnese: Compreensão do conjunto de dados

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

Observa-se pelo *dashboard* abaixo que os **dados encontram-se balanceados**, com **exceção da coluna *tratamento***. 
Para esse atributo, observa-se que foi realizado um número expressivo de **experientos *com_droga* a mais do que *com_controle***. Essa característica é **específica** dessa a área de **negócio**, que exige que uma porcentagem dos experimentos seja ralizada com placebo, na **técnica duplo-cego**, para fins de comparação e controle.

<a href="https://ibb.co/12QThJW"><img src="https://i.ibb.co/ry0HTfr/2-Balanceamento-dos-dados.png" alt="2-Balanceamento-dos-dados" border="0"></a>

#### Limpeza do conjunto de dados
Concluímos que as drogas utilizadas nos tratamento do tipo ***com_controle***, por se tratarem de **placebo**, **jamais serão capazes de ativar algum mecanismo de ação (MoA)**. Assim, **deletamos** todas as linhas cuja **droga** é igual a **"cacb2b860"**.
(21948, 878)

Após a limpeza, o DataFrame ficou com **21948 linhas/registros** e **878 colunas/atributos**

### <a name=“Analise-exploratoria-e-estatistica-do-Conjunto-de-dados”><a/> :chart_with_downwards_trend: Os Exames Laboratoriais: Análise exploratória e estatística do Conjunto de dados
   
<a href="https://ibb.co/vcpXRvD"><img src="https://i.ibb.co/hgbYw1C/3-Media-expressao-genica-Xviabilidade-celular.png" alt="3-Media-expressao-genica-Xviabilidade-celular" border="0"></a>

<a href="https://ibb.co/c6WKCQh"><img src="https://i.ibb.co/x1nKf6q/4-variancia-express-o-genica-Xviabilidade-celular.png" alt="4-variancia-express-o-genica-Xviabilidade-celular" border="0"></a>

<a href="https://ibb.co/m6MctCB"><img src="https://i.ibb.co/18wmKfn/5-media-vari-ncia-expressao-genica-conjunto-Eviabilidade-celular.png" alt="5-media-vari-ncia-expressao-genica-conjunto-Eviabilidade-celular" border="0"></a>
  

### <a name=“Modelagem-aplicacao-e-teste-de-modelos-de-Machine-Learning”><a/> :syringe: O Tratamento: Modelagem, aplicação e teste de modelos de *Machine Learning*
   
#### **Validação Cruzada com Scikit-learn**

Para evitar o **overfitting** e demais erros metodológicos na construção do modelo e ainda assim mover-se na busca pelos melhores parâmetros **(Tuning)** aplicáveis ao problema de negócio, uma boa prática é a realização da **validação cruzada ** , uma técnica que particiona o conjuento de dads em vários subconjuntos, mutualmente exclusivos. Nessa técnica, utiliza-se parte dos subconjuntos para estimar os melhores valores para os parâmetros e a outra parte dos subconjuntos para validação do aprendizado do modelo. 

Esta técnica é amplamente empregada em problemas onde o objetivo da modelagem é a descoberta de conhecimento em conjuntos de dados novos e desconhecidos com as mesmas características do modelo, como é o caso do nosso projeto de **Drug Discovery**.[[Fonte 3]](https://pt.wikipedia.org/wiki/Valida%C3%A7%C3%A3o_cruzada)

Assim, buscou-se utilizar a **validação cruzada** para comparar os **melhores modelos de Machine Learning** aplicáveis ao problema de **Drug Discovery**. 

Os modelos a serem testados foram escolhidos com base no artigo **Machine Learning Methods in Drug Discovery** [[Fonte 4]](https://pubs.acs.org/doi/full/10.1021/acs.jcim.9b00136)

Existem três tipos principais de **métodos** para realização do **particionamento do conjunto de dados** na validação cruzada, sendo eles: **o método holdout, o k-fold e o leave-one-out.** [[Fonte 3]](https://pt.wikipedia.org/wiki/Valida%C3%A7%C3%A3o_cruzada)

No modelo  de Drug Discovery em estudo foi utlilizada a **validação cruzada pelo método k-fold** que consiste em: 

> **Dividir** o conjunto total de dados em **k subconjuntos mutuamente exclusivos do mesmo tamanho** e, a partir daí, **um subconjunto** é utilizado para **teste** e os **k-1 restantes** são utilizados para **estimação dos parâmetros**, fazendo-se o cálculo da acurácia do modelo. Este processo é **realizado k vezes** alternando de forma circular o subconjunto de teste. **Ao final das k iterações calcula-se a acurácia** sobre os erros encontrados, através da equação descrita anteriormente, obtendo assim uma **medida mais confiável** sobre a capacidade do modelo de representar o processo gerador dos dados. [[Fonte 3]](https://pt.wikipedia.org/wiki/Valida%C3%A7%C3%A3o_cruzada)

Para estabelecer um **bom valor de acurácia**, precisamos de uma **base comparativa**, quer dizer, preciso dos resultados de um outro modelo para entender se estamos acertando mais ou menos casos.

Para isso, o *Scikit-Learn*, já tem implementado alguns algoritmos que testam modelos **menos complexos** e que podem ser usados como **base comparativa**. Neste caso, vamos usar o **DummyClassifier.**

### <a name=“Comparacao-dos-resultados-de-cada-modelo”><a/> :pencil: A Receita Médica: Comparação dos resultados de cada modelo
   
#### Resultado do teste simultâneo de seis modelos de *Machine Learning*, em comparação com os resultados do  do modelo *DummyClassifier.*

Pelo teste simultâneo, temos que o algoritmo que apresentou a melhor acurácia foi o SVC

<a href="https://ibb.co/5jz6k38"><img src="https://i.ibb.co/jwxTzYM/6-Comparacao-modelos.png" alt="6-Comparacao-modelos" border="0"></a>
  
#### Ajustando a dose 

O ***GridSearchCV*** é uma ferramenta usada para **automatizar** o processo de **ajuste dos parâmetros** de um algoritmo, pois ele fará de maneira sistemática **diversas combinações** dos parâmetros e depois de avaliá-los os armazenará num **único objeto**.

Após aplicação do método para **ajuste dos parâmetros** do algoritmo **SVC()**, obtivemos os seguintes resusltados:

| Nome do Parâmetro | Tipo                                                  | Descrição                                                                                                                                                                   | Melhor valor  |
|-------------------|-------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------|
| C                 | float                                                 | Parâmetro de regularização. A intensidade da regularização é inversamente proporcional a C. Deve ser estritamente positiva.                                                 | 10            |
| gamma             | {‘scale’, ‘auto’} or float                            | Coeficiente de kernel para 'rbf', 'poly' e 'sigmóide'.                                                                                                                      | 0.0001        |
| Kernel            | {'linear', 'poli', 'rbf', 'sigmoid', 'pré-computado'} | Especifica o tipo de kernel a ser usado no algoritmo. Deve ser 'linear', 'poli', 'rbf', 'sigmóide', 'pré-computado' ou chamável. Se nenhum for fornecido, 'rbf' será usado. | 'rbf'         |

#### Grau de acerto 

Como podemos ver pela **Matriz de Confusão**  (Grupo de Teste e Treino), o **modelo baseado em SVC** conseguiu **prever** 
com muito bem a **ativação** dos mecanismos **MoA** para ambos os **estados (False, True)**.

<a href="https://imgbb.com/"><img src="https://i.ibb.co/jzHBFdR/7-Confusion-matrix-teste.png" alt="7-Confusion-matrix-teste" border="0"></a>

<a href="https://imgbb.com/"><img src="https://i.ibb.co/zf23zDk/8-Confusion-matrix-treino.png" alt="8-Confusion-matrix-treino" border="0"></a>

## <a name=“Consideracoes-finais-acerca-das-limitacoes-e-melhorias-futuras”><a/> :repeat: O *check-up* médico: Considerações finais acerca das limitações e melhorias futuras

## <a name=“Referencias-bibliograficas”><a/> :books: O Catálogo de Medicamentos: Referências Bibliográficas
   
1. [Validação Cruzada com Scikit-learn](https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.cross_val_score.html)
2. [Validação cruzada: avaliando o desempenho do estimador com Scikit-learn](https://scikit-learn.org/stable/modules/cross_validation.html)
3. [Validação cruzada](https://pt.wikipedia.org/wiki/Valida%C3%A7%C3%A3o_cruzada)
4. [Machine Learning in Drug Discovery](https://pubs.acs.org/doi/full/10.1021/acs.jcim.9b00136)
5. [sklearn.naive_bayes.GaussianNB ](https://scikit-learn.org/stable/modules/generated/sklearn.naive_bayes.GaussianNB.html?highlight=naive#sklearn.naive_bayes.GaussianNB/)
6. [A Gentle Introduction to Bayes Theorem for Machine Learning](https://machinelearningmastery.com/bayes-theorem-for-machine-learning/)
7. [Validação Cruzada Aninhada com Scikit-learn](https://dataml.com.br/validacao-cruzada-aninhada-com-scikit-learn/)

# ***-Mergulhe fundo, é apenas o primeiro passo!-***

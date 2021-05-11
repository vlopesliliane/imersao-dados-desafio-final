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


### <a name=“Analise-exploratoria-e-estatistica-do-Conjunto-de-dados”><a/> :chart_with_downwards_trend: Os Exames Laboratoriais: Análise exploratória e estatística do Conjunto de dados
  

### <a name=“Modelagem-aplicacao-e-teste-de-modelos-de-Machine-Learning”><a/> :syringe: O Tratamento: Modelagem, aplicação e teste de modelos de *Machine Learning*
  
### <a name=“Comparacao-dos-resultados-de-cada-modelo”><a/> :sunglasses: :pencil: A Receita Médica: Comparação dos resultados de cada modelo
  
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

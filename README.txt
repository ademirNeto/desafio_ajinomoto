==============================================================================
DESAFIO DE CIENCIA DE DADOS - SUPPLY CHAIN GLOBAL
Material de aula (turma) - dataset DataCo Supply Chain
==============================================================================

Contexto: voces foram contratados como Cientistas de Dados por uma empresa de
Supply Chain global. A diretoria esta preocupada com atrasos nas entregas e
margens de lucro inconsistentes. Ao longo dos encontros vamos do entendimento
dos dados ate modelos de Machine Learning.

Cada encontro tem dois notebooks:
  - ALUNO    : codigo base + celulas marcadas com "# TODO" para completar
  - GABARITO : resolucao completa (uso do instrutor)


ARQUIVOS DO REPOSITORIO
-----------------------
  Dataset
    data.csv                          Amostra de 1/3 do dataset (~60.173 linhas,
                                      53 colunas). Seed fixa (random_state=42),
                                      salvo em UTF-8.
                                      (originalmente DataCoSupplyChain_reduzido.csv)

  Encontro 1 - EDA e Estatistica
    Desafio_SupplyChain_ALUNO.ipynb
    desafio_I.ipynb                   (gabarito do Encontro 1)

  Encontro 2 - Regressao, Classificacao e ML
    Encontro2_ML_ALUNO.ipynb
    Encontro2_ML_GABARITO.ipynb

  README.txt                          Este arquivo.

IMPORTANTE - nome do CSV:
  Os notebooks do Encontro 1 leem 'data.csv' / 'DataCoSupplyChain_reduzido.csv'
  e os do Encontro 2 leem 'supplychain.csv'. Use o MESMO nome em todos ou ajuste
  a linha pd.read_csv(...) no inicio de cada notebook para o nome do seu arquivo.


COMO RODAR
----------
  Jupyter / Anaconda:
    pip install pandas numpy matplotlib scipy scikit-learn jupyter
    jupyter notebook

  JupyterLite / Pyodide (no navegador):
    - pandas, numpy, matplotlib e scipy ja vem no ambiente.
    - Para o Encontro 2, instale o scikit-learn numa celula:
        import piplite
        await piplite.install("scikit-learn")
    - NAO use seaborn: os notebooks ja foram escritos so com matplotlib.


==============================================================================
ENCONTRO 1 - CONHECENDO OS DADOS (EDA + ESTATISTICA)
==============================================================================
Parte 1 - Dicionario de dados (25 variaveis criticas; Grupo A: 1-12, Grupo B: 13-25).
Parte 2 - Feature Engineering: exemplos prontos (Atraso_em_Dias,
          Margem_Lucro_Percentual) + 2 novas features propostas pela equipe.
Parte 3 - Estatistica descritiva e outliers (Order Item Discount Rate,
          Order Profit Per Order); o que acontece com o lucro no desconto maximo.
Parte 4 - Matriz de correlacao; top 3 correlacoes positivas e negativas;
          discussao de data leakage.
Parte 5 - Teste de hipoteses e p-valor (template: Teste T Standard x First Class;
          desafio: nova hipotese de negocio com o teste adequado).


==============================================================================
ENCONTRO 2 - REGRESSAO, CLASSIFICACAO E MACHINE LEARNING
==============================================================================
O Diretor de Supply Chain quer previsibilidade. Construimos modelos iniciais.

Parte 1 - CLASSIFICACAO (vai atrasar?)
          Alvo: Late_delivery_risk (0 = no prazo, 1 = atrasado).
          Preditores: Shipping Mode, Customer Segment, Category Name.
          Avaliacao: acuracia + matriz de confusao.
          Discussao: o que e pior para a empresa, um Falso Positivo ou um
          Falso Negativo de atraso? (resposta no gabarito: minimizar FN).

Parte 2 - REGRESSAO (previsao de receita)
          Alvo: Sales. Preditores: quantidade, preco, desconto + categoricas.
          Avaliacao: R2, MAE, RMSE + grafico real x previsto.
          Cuidado com leakage (Order Item Total, Sales per customer).

Parte 3 - FEATURE IMPORTANCE
          Random Forest / Gradient Boosting para Late_delivery_risk;
          extrair e plotar as variaveis mais importantes. E a regiao? o
          departamento? o modal? (tendem a dominar desconto, prazo agendado e
          shipping mode).

Parte 4 - CLUSTERING (geolocalizacao)
          K-Means em Latitude/Longitude cruzado com Delivery Status e
          Order Status = SUSPECTED_FRAUD, gerando um mapa de risco logistico
          (clusters com maior taxa de atraso/fraude).


==============================================================================
PROXIMOS PASSOS (ideias)
==============================================================================
- Permutation importance para confirmar as variaveis-chave.
- Balanceamento de classes / ajuste de threshold para reduzir Falsos Negativos.
- Previsao de demanda temporal usando order date (DateOrders).

Bom trabalho!

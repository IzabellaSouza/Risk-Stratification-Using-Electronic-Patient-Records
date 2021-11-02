![alt text](https://github.com/IzabellaSouza/Risk-Stratification-Using-Electronic-Patient-Records/blob/1e0c396d0a58fc7663052d5c68c0a91359730c3a/imagens/imagem01.png)

<br>

## Índice

- [Definicao do Problema](#problema)
- [Dados](#dados)
- [Etapas](#etapas)
- [Progresso](#progresso)
- [Criador](#criador)

<br>
# DEFINIÇÃO DO PROBLEMA

As readmissões hospitalares são caras e refletem as inadequações no sistema de saúde. Nos Estados Unidos sozinho, o tratamento de pacientes diabéticos readmitidos excede 300 milhões de dólares por ano. Identificação precoce de pacientes que enfrentam um alto risco de readmissão pode permitir que os profissionais de saúde conduzam investigações adicionais e possivelmente impeçam futuras readmissões. Isso não apenas melhora a qualidade do atendimento, mas também reduz as despesas médicas em readmissão.

Diabetes é a sétima principal causa de morte (dados de 2016) no mundo e afeta cerca de 23,6 milhões de pessoas só nos EUA e milhões de pessoas são diagnosticados com diabetes a cada ano em todo mundo.

Segundo a Associação Americana de Diabetes, o custo do atendimento a pacientes diabéticos e pré-diabéticos nos Estados Unidos é o maiior do mundo. Essa epidemia global afeta mais de 350 milhões de pessoas, com 3 milhões de pessoas morrendo a cada ano devido a complicações relacionadas ao diabetes, predominantemente cardiovasculares ou nefropáticas.

A readmissão hospitalar é uma das principais preocupações no tratamento do diabetes, com milhões de dólares sendo gastos no tratamento de pacientes diabéticos que precisam ser readmitidos em um hospital após receberem alta.

A necessidade de readmissão indica que cuidados inadequados foram fornecidos ao paciente no momento da primeira admissão. A taxa de readmissão se tornou uma métrica importante para medir a qualidade geral de um hospital.

**Neste projeto usaremos registros eletrônicos de dados médicos, como resultados dos exames, nível de insulina, diagnóstico de outras doenças, etc...
Mas não vamos "apenas" prever se um paciente pode ou não ser readmitido. Vamos estratificar o risco em 3 categorias e realizar uma análise completa das métricas fornecidas pelos modelos.**

**Vamos treinar e comparar o desempenho de alguns algoritmos de aprendizado de máquina e decidir qual deles usar para prever o risco de readmissão para o paciente.**

Usaremos o melhor modelo treinado para estratificar a população em três grupos de risco:
- Alto Risco (probabilidade de readmissão > 0,7)
- Risco Médio (0,3 < Probabilidade de readmissão < 0,7)
- Baixo Risco (probabilidade de readmissão < 0,3)

Observe que maior sensibilidade (recall) é mais desejável para os hospitais porque é mais importante identificar corretamente pacientes de "alto risco" que provavelmente serão readmitidos do que identificar pacientes de "baixo risco".

Todas as escolhas serão justificadas durante o desenvolvimento do projeto.

Os EUA mantém um programa constante de redução de readmissão de pacientes: **Hospital Readmissions Reduction Program (HRRP)**
<br>

# DADOS

O conjunto de dados, **"Diabetes 130-US hospitals for years 1999-2008"**, foi baixado do UCI Machine Learning Repository.

Os dados representam 10 anos (1999-2008) de atendimento clínico em 130 hospitais dos EUA e redes de distribuição integradas com 100.000 observações e 50 recursos (variáveis) que representam os registros eletrônicos com resultados de exames dos pacientes e dados sobre cada hospital.

*Diabetes 130-US hospitals for years 1999-2008 Data Set*

A coleta dos dados foi descrita pelos autores neste trabalho:

- O controle da hiperglicemia em pacientes hospitalizados tem uma influência significativa no resultado, tanto em termos de morbidade quanto de mortalidade. No entanto, existem poucas avaliações nacionais sobre o tratamento do diabetes durante a hospitalização que podem servir de base para a mudança.

- Essa análise de um grande banco de dados clínicos (74 milhões de encontros únicos correspondentes a 17 milhões de pacientes únicos) foi realizada para fornecer essa avaliação e encontrar orientações futuras que possam levar a melhorias na segurança do paciente. Quase 70.000 encontros de pacientes internados com diabetes foram identificados com detalhes suficientes para análise. A regressão logística multivariável foi usada para ajustar a relação entre a medida da HbA1c e a readmissão precoce, enquanto o controle de covariáveis, como dados demográficos, gravidade e tipo da doença, e tipo de admissão.

- Os resultados mostram que a medição da HbA1c foi realizada com pouca frequência (18,4%) no ambiente hospitalar. O modelo estatístico sugere que a relação entre a probabilidade de readmissão e a medição da HbA1c depende do diagnóstico primário. Os dados sugerem ainda que a maior atenção ao diabetes refletida na determinação da HbA1c pode melhorar os resultados dos pacientes e reduzir o custo dos cuidados hospitalares.

HbA1c é uma medida de quão bem o seu açúcar no sangue está controlado durante um período de cerca de 3 meses. Essencialmente, dá uma boa ideia de quão altos ou baixos, em média, foram os níveis de glicose no sangue.

Descrição completa do trabalho:

Impact of HbA1c Measurement on Hospital Readmission Rates: Analysis of 70,000 Clinical Database Patient Records

## Dicionário de Dados:
- 0 **encounter_id** - identificador único de um encontro do pesquisador com o paciente.
- 1 **patient_nbr** - identificador exclusivo de um paciente.
- 2 **race** - valores: Caucasian, Asian, African American, Hispanic e other.
- 3 **gender** - valores: male, female, and unknown/invalid.
- 4 **age** - agrupados em intervalos de 10 anos: (0, 10), (10, 20), ..., (90, 100).
- 5 **weight** - peso em libras.
- 6 **admission_type_id** - identificador inteiro correspondente a 9 valores distintos, por exemplo, "emergência, urgência, eletiva, recém-nascido e não disponível".
- 7 **discharge_disposition_id** - identificador inteiro correspondente a 29 valores distintos, por exemplo, "enviado para casa, expirou e não está disponível".
- 8 **admission_source_id** - identificador inteiro correspondente a 21 valores distintos, por exemplo, "encaminhamento médico, e transferência de um hospital".
- 9 **time_in_hospital** - número inteiro de dias entre a admissão e a alta,
- 10 **payer_code** - identificador inteiro correspondente a 23 valores distintos, por exemplo, Blue Cross / Blue Shield, Medicare e auto-pagamento".
- 11 **medical_specialty** - identificador inteiro de uma especialidade do médico admitidor, correspondente a 84 valores distintos, por exemplo, cardiologia, medicina interna, família / clínica geral e cirurgião".
- 12 **num_lab_procedures** - número de testes de laboratório realizados durante a consulta.
- 13 **num_procedures** - número de procedimentos (exceto testes de laboratório) realizados durante a consulta.
- 14 **num_medications** - número de medicamentos genéricos distintos administrados durante a consulta.
- 15 **number_outpatient** - número de consultas ambulatoriais do paciente no ano anterior a consulta.
- 16 **number_emergency** - número de visitas de emergência do paciente no ano anterior a consulta.
- 17 **number_inpatient** - número de visitas hospitalares do paciente no ano anterior a consulta.
- 18 **diag_1** - diagnóstico primário (codificado como três primeiros dígitos da CID9); 848 valores distintos.
- 19 **diag_2** - diagnóstico secundário (codificado como três primeiros dígitos da CID9); 923 valores distintos.
- 20 **diag_3** - diagnóstico secundário adicional (codificado como três primeiros dígitos da CID9); 954 valores distintos.
- 21 **number_diagnoses** - número de diagnósticos inseridos no sistema.
- 22 **max_glu_serum** - teste sérico de glicose que indica a faixa do resultado ou se o teste não foi realizado. Valores: > 200, > 300, normal e nenhum, se não for medido.
- 23 **A1Cresult** - teste A1c que indica o intervalo do resultado ou se o teste não foi realizado. Valores: > 8 (se o resultado for maior que 8%), > 7 (se o resultado for maior que 7%, porém menor que 8%), normal (se o resultado for inferior a 7%) e nenhum, se não for medido.

Na sequência temos os recursos de 24 a 46 para os nomes dos medicamentos genéricos:

*metformina, repaglinida, nateglinida, clorpropamida, glimepirida, acetohexamida, glipizida, gliburida, tolbutamida, pioglitazona, rosiglitazona, acarbose, miglitol, troglitazona, insulazforamida, examide, sitaglagliptida, sitazagliptida , glipizida-metformina, glimepirida-pioglitazona, metformina-rosiglitazona e metformina-pioglitazona.*

Cada um desses recursos indica se o medicamento foi prescrito ou se houve uma alteração na dosagem. Valores: "up" se a dose foi aumentada durante a consulta.

- 47 **change** - indica se houve alteração nos medicamentos para diabéticos (dosagem ou nome genérico). Valores: "change" e "no change".
- 48 **diabetesMed** - indica se houve algum medicamento diabético prescrito. Valores: "sim" e "não".
- 49 **readmitted** - readmitido, "Dias para readmissão hospitalar. Valores: <30 (se o paciente foi readmitido em menos de 30 dias), > 30 (se o paciente foi readmitido em mais de 30 dias) e No, para nenhum registro de readmissão.

**Nota: Códigos ICD-9 ou CID-9 (International Classification of Diseases ou Código Internacional de Doenças).**
<br>

# ETAPAS
- [x] Carregando os Dados e Compreendendo as Variáveis
- [x] Limpeza e Transformação dos Dados
- [x] Análise Exploratória
- [x] Modelagem Preditiva
- [x] Comparação Entre os Modelos
- [x] Estratificação de Risco
- [x] Previção do Risco de Readmissão com Novos Dados
- [x] Conclusão
- [x] Ferramentas Utilizadas
<br>

# PROCESSO 

### Carregando os Dados e Compreendendo as Variáveis

### Limpeza e Transformação dos Dados
- Engenharia de Atributos
- Recategorização de Variável
- Recoding variáveis categóricas

### Análise Exploratória
- Análise Univariada
- Pré-Processamento de Dados

### Modelagem Preditiva
- Criação de cinco modelos
- Treinamento dos modelos
- Avaliação dos modelos
- Cálculo e interpretação das métricas
- Extração da importância das variáveis

### Comparação Entre os Modelos

### Estratificação de Risco
- Usaremos o modelo que apresentou as melhores métricas globais, Acurácia e Score AUC

### Previção do Risco de Readmissão com Novos Dados

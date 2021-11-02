![alt text](https://github.com/IzabellaSouza/Risk-Stratification-Using-Electronic-Patient-Records/blob/1e0c396d0a58fc7663052d5c68c0a91359730c3a/imagens/imagem01.png)
 
# Definição do Problema

As readmissões hospitalares são caras e refletem as inadequações no sistema de saúde. Nos Estados Unidos sozinho, o tratamento de pacientes diabéticos readmitidos excede 300 milhões de dólares por ano. Identificação precoce de pacientes que enfrentam um alto risco de readmissão pode permitir que os profissionais de saúde conduzam investigações adicionais e possivelmente impeçam futuras readmissões. Isso não apenas melhora a qualidade do atendimento, mas também reduz as despesas médicas em readmissão.

Diabetes é a sétima principal causa de morte (dados de 2016) no mundo e afeta cerca de 23,6 milhões de pessoas só nos EUA e milhões de pessoas são diagnosticados com diabetes a cada ano em todo mundo.

Segundo a Associação Americana de Diabetes, o custo do atendimento a pacientes diabéticos e pré-diabéticos nos Estados Unidos é o maiior do mundo. Essa epidemia global afeta mais de 350 milhões de pessoas, com 3 milhões de pessoas morrendo a cada ano devido a complicações relacionadas ao diabetes, predominantemente cardiovasculares ou nefropáticas.

A readmissão hospitalar é uma das principais preocupações no tratamento do diabetes, com milhões de dólares sendo gastos no tratamento de pacientes diabéticos que precisam ser readmitidos em um hospital após receberem alta.

A necessidade de readmissão indica que cuidados inadequados foram fornecidos ao paciente no momento da primeira admissão. A taxa de readmissão se tornou uma métrica importante para medir a qualidade geral de um hospital.

Neste projeto usaremos registros eletrônicos de dados médicos, como resultados dos exames, nível de insulina, diagnóstico de outras doenças, etc...

Mas não vamos "apenas" prever se um paciente pode ou não ser readmitido. Vamos estratificar o risco em 3 categorias e realizar uma análise completa das métricas fornecidas pelos modelos.

Vamos treinar e comparar o desempenho de alguns algoritmos de aprendizado de máquina e decidir qual deles usar para prever o risco de readmissão para o paciente.

Usaremos o melhor modelo treinado para estratificar a população em três grupos de risco:
- Alto Risco (probabilidade de readmissão > 0,7)
- Risco Médio (0,3 < Probabilidade de readmissão < 0,7)
- Baixo Risco (probabilidade de readmissão < 0,3)

Observe que maior sensibilidade (recall) é mais desejável para os hospitais porque é mais importante identificar corretamente pacientes de "alto risco" que provavelmente serão readmitidos do que identificar pacientes de "baixo risco".

Todas as escolhas serão justificadas durante o desenvolvimento do projeto.

Os EUA mantém um programa constante de redução de readmissão de pacientes:
- Hospital Readmissions Reduction Program (HRRP)
 
 

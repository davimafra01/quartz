---
draft: true
---
# 1. Introdução à Fase 1
O **RTO (*Real-Time Optimization*)** não é um “controlador” no sentido clássico. Ele é uma **camada de inteligência operacional e econômica**, construída acima da automação existente da planta (geralmente PIDs e APCs), cujo papel é **decidir continuamente quais são as melhores condições globais de operação da usina**, neste caso, considerando simultaneamente (i) moagem, (ii) destilação e (iii) cogeração de energia.

A planta já possui automação, PLCs, sensores, historiadores (PIMS, LIMS), operadores humanos e malhas regulatórias. Tudo isso já funciona. O RTO não substitui nada disso. Ele entra como uma **camada superior de raciocínio**, que observa a planta como um sistema integrado de produção, energia e matéria-prima, e responde a uma pergunta muito específica:

> “Dadas as condições atuais da planta, qual é a melhor forma de operar agora para maximizar os indicadores **ESTRATÉGICOS** da empresa?”

Neste caso, quando falamos de "indicadores estratégicos", estamos falando daqueles descritos no Plano de Produção.

---
# 2. AS-IS: Dados, KPIs e Ativos disponíveis

### 2.1 Moagem
Dados operacionais:
- Dados de processo da moagem;
- Variáveis manipuladas e controladas da moagem;
- Setpoints da moagem (pressão, vazão, temperatura, etc.);
- Dados via PIMS;
- Dados via CLP / PLC.

Dados laboratoriais:
- Pureza do caldo;
- Pol do caldo.

KPIs:
- Rendimento de extração;
- Consumo energético;
- Disponibilidade operacional;
- Eficiência de extração;
- Tonelagem moída;
- Perdas na torta ou bagaço.

Ativos:
- Desfibradores;
- Moendas;
- Esteiras;
- Tanques de embebição;
- Sensores de qualidade de caldo.

### 2.2 Destilação
Dados operacionais:
- Dados de processo da destilação;
- Variáveis manipuladas e controladas da destilação;
- Setpoints da destilação;
- Dados via PIMS;
- Dados via CLP / PLC.

Dados laboratoriais:
- Concentração do etanol;
- Pureza do etanol.

KPIs:
- Pureza do etanol;
- Eficiência térmica;
- Perdas alcoólicas;
- Consumo energético.

Ativos:
- Coluna de destilação;
- Trocadores de calor;
- Bombas;
- Tanques intermediários;
- Torre de resfriamento.

### 2.3 Cogeração
Dados operacionais:
- Dados de processo da cogeração;
- Variáveis manipuladas e controladas da cogeração;
- Setpoints da cogeração;
- Dados via PIMS;
- Dados via CLP/PLC.

Dados inferidos (soft sensors):
- Umidade do bagaço.

KPIs:
- Eficiência térmica;
- Consumo específico de bagaço;
- Exportação de energia;
- Estabilidade de pressão do vapor;
- Estabilidade de temperatura do vapor;
- Energia gerada por tonelada de bagaço.

Ativos:
- Caldeiras.
- Turbogeradores;
- Sistemas de alimentação de bagaço;
- Exaustores;
- Sistemas de lavagem de gases.

### 2.4 Elementos Globais
Dados globais:
- Plano de Produção (metas estratégicas).

KPIs globais:
- Rendimento industrial;
- Consumo energético;
- Perdas alcoólicas;
- Eficiência térmica.

---
# 3. TO-BE: Dados, KPIs e Ativos que serão gerados

### 3.1 Ativos digitais
O principal ativo entregue pelo projeto é a **(i) camada de RTO**, que passa a existir como um sistema digital sobreposto à automação existente. Esse RTO não é um controlador no sentido clássico, mas sim um sistema de otimização matemática e econômica que opera continuamente sobre modelos do processo e sobre dados históricos e em tempo real.

Além do próprio RTO, o projeto entrega um conjunto de ativos digitais estruturantes, que compõem a arquitetura de inteligência operacional da planta. Entre eles estão os **(ii) modelos matemáticos do processo**, que representam formalmente a relação entre variáveis operacionais, restrições físicas e desempenho produtivo e energético. Esses modelos são utilizados tanto para simulação quanto para otimização.

Outro ativo central é o **(iii) CAR (identificador de gargalos)**, que é um módulo analítico responsável por identificar restrições ativas do sistema produtivo, isto é, quais equipamentos, variáveis ou limites estão efetivamente impedindo ganhos adicionais de produção, eficiência ou redução de perdas.

O projeto também entrega **(iv) *dashboards* interativos**, que constituem a camada de visualização e interação homem-sistema. Esses *dashboards* consolidam indicadores, metas, recomendações e resultados do RTO, permitindo que operadores, engenheiros e gestores visualizem o estado ótimo da planta e os desvios em relação ao ótimo.

Em síntese, os ativos digitais novos são:
- Sistema de RTO (otimizador em tempo real);
- Modelos matemáticos do processo;
- Módulo CAR (identificador de gargalos);
- Função de custo;
- Dashboards interativos de visualização e acompanhamento.

Entraremos em mais detalhes sobre cada um desses ativos da "seção 4" em diante. Por agora, vamos apenas falar um pouco de cada um desses ativos.

É importante entender o seguinte:

O **RTO** não otimiza temperatura, pressão ou vazão.
> Ele otimiza - lançando mão da função de custo - **resultados de negócio** usando variáveis físicas.
> 
> Em termos formais, os resultados de negócio são grandezas econômicas mensuráveis, tais como: Lucro operacional; Margem de contribuição; Receita; Custo energético total; Custo de insumos; Perdas monetárias; Valor econômico da produção; Exportação de energia (R$); Custo de oportunidade; EBITDA operacional (em alguns projetos).

Os **MODELOS MATEMÁTICOS DO PROCESSO** respondem à pergunta:
> "Se eu mexer nisso, o que acontece fisicamente?"

O **IDENTIFICADOR DE GARGALOS (MÓDULO CAR)** responde à pergunta:
> "O que está limitando o desempenho agora?"

A **FUNÇÃO DE CUSTO** é outra coisa. Ela não quer saber “como funciona”. Ela quer saber o que é bom e o que é ruim. Ela recebe:

Do plano produtivo:
- preços de venda;
- custos de energia;
- custos de insumos;
- penalidades contratuais;
- metas estratégicas.

Do modelo:
- quanto cada decisão afeta produção;
- quanto consome energia;
- quanto gera perdas.

Do CAR:
- quais restrições estão ativas;
- quais decisões são inviáveis;
- quais penalidades aplicar.

A função de custo não recebe dados operacionais e laboratoriais diretamente. Ela recebe as funções dos modelos (que, por sua vez, estão em função dos dados operacionais e laboratoriais). Vide exemplo da coluna de destilação de petróleo.

> A função de custo não consome dados brutos. Ela consome _variáveis modeladas_ derivadas dos dados.

A função de custo não “vê” coisas como:
- temperatura medida no sensor T-101;
- vazão instantânea da FT-203;
- composição medida no laboratório.

Ela vê coisas como:
- taxa de produção estimada;
- consumo energético previsto;
- rendimento calculado;
- perdas modeladas;
- eficiência global do sistema.

### 3.2 Dados digitais (gerados pelo RTO)
O projeto não cria novos sensores físicos, mas cria uma **nova classe de dados digitais**, que não existiam antes: dados calculados, inferidos e otimizados.

A primeira grande categoria são os **soft sensors**, isto é, variáveis que não são medidas diretamente, mas estimadas por modelos matemáticos a partir de dados existentes. Esses soft sensors passam a fornecer estimativas contínuas de grandezas relevantes para a otimização, como estados internos do processo, eficiências implícitas, perdas não diretamente mensuráveis, entre outros.

A segunda categoria são as **variáveis calculadas pelos modelos**, como balanços de massa e energia, rendimentos instantâneos, indicadores de eficiência e funções auxiliares utilizadas no problema de otimização.

A terceira categoria são os **outputs do otimizador**, que são, de fato, os dados mais característicos do RTO. Esses outputs incluem valores ótimos das variáveis de decisão, custos ótimos, valores da função objetivo, marginais econômicos, indicadores de sensibilidade e informações sobre quais restrições estão ativas no ponto ótimo.

Ou seja, o RTO transforma dados operacionais brutos em **dados de alto nível cognitivo**, que não existiam no AS-IS.

### 3.3 Novos KPIs
O projeto não define formalmente um novo conjunto fechado de KPIs com nomes específicos além dos já existentes, mas ele muda qualitativamente a natureza dos KPIs ao introduzir **KPIs econômicos e de otimização**. Tenha em mente que nem todos os KPIs serão transformados pelo RTO.

O projeto não cria novos KPIs operacionais, mas passa a fornecer **versões ótimas, preditivas e econômicas** dos KPIs já existentes, como:
- Rendimento industrial ótimo;
- Consumo energético global ótimo;
- Perdas alcoólicas globais mínimas;
- Eficiência térmica global ótima.

Além de KPIs nativamente novos do RTO:
- Valor da função de custo global;
- Ganho econômico estimado;
- Desvio em relação ao ponto ótimo;
- Utilização de gargalos;
- Potencial econômico não explorado;
- Entre outros KPIs a serem definidos em tempo de execução ou na fase de detalhamento.

Esses KPIs não são simplesmente indicadores de desempenho operacional, como no AS-IS, mas sim **indicadores de qualidade da decisão**, isto é, medem quão distante a planta está do ótimo matemático-econômico calculado pelo RTO.

Mesmo quando os KPIs têm o mesmo nome dos anteriores (eficiência, rendimento, consumo), eles passam a existir também em uma versão **“ótima”**, fornecida pelo modelo, e não apenas na versão “real”, medida na planta.

O RTO transforma KPI de **métrica descritiva** $\rightarrow$ **métrica normativa e econômica**.

### 3.4 Novas capacidades de controle e decisão
Essa é, conceitualmente, a entrega mais importante do projeto. Sem o RTO, a planta apenas:
- mede;
- controla localmente (PID/APC);
- observa indicadores.

Depois do RTO, a planta passa a ter **capacidade formal de decidir matematicamente**.

O sistema passa a gerar:
- **setpoints ótimos globais**, calculados a partir de uma função de custo econômica;
- **recomendações operacionais**, indicando como ajustar variáveis para maximizar desempenho;
- **priorização de gargalos**, mostrando onde atuar primeiro;
- **simulações de cenários**, permitindo testar virtualmente estratégias operacionais;
- **análises de sensibilidade**, mostrando impacto econômico de cada variável.

Ou seja, o RTO não apenas diz “como a planta está”, mas passa a dizer:

> **“Como a planta deveria estar, do ponto de vista matemático e econômico.”**

Isso representa uma mudança de paradigma:
- do controle reativo;
- para a **operação ótima orientada por modelo**.

---
# 4. Sistema de RTO
### 4.1 O que o RTO “enxerga” da planta
No modelo dessa proposta, o RTO enxerga a planta através de três grandes blocos de dados:
1. **Dados operacionais** vindos da automação (sensores, PLC, PIMS);
2. **Dados laboratoriais** (LIMS), como pureza, pol, brix, teor alcoólico;
3. **Plano produtivo**, vindo da gestão (metas, prioridades, restrições).

Esses dados alimentam um conjunto de **modelos matemáticos e analíticos**, que representam como a planta se comporta. Esses modelos não são apenas físicos; eles são **modelos híbridos**, que misturam:
- correlações estatísticas;
- regras de negócio;
- conhecimento de especialistas;
- restrições operacionais reais.

O RTO não está tentando resolver equações termodinâmicas perfeitas. Ele está tentando responder, de forma prática:

> “Se eu mudar esses parâmetros globais, o que acontece com meus KPIs?”

### 4.2 O papel central do RTO: otimização global
O ponto mais importante: o RTO é a **primeira camada que enxerga a planta como um todo**.

Na automação tradicional, cada área é um mundo:
- moagem tenta extrair o máximo possível;
- destilação tenta purificar o máximo possível;
- cogeração tenta gerar energia da forma mais eficiente.

Mas essas três áreas **competem entre si**:
- moagem consome energia;
- destilação consome vapor;
- cogeração depende do bagaço;
- bagaço depende da moagem;
- vapor limita destilação;
- qualidade do vinho impacta destilação.

O RTO existe exatamente para resolver esse tipo de conflito sistêmico. Ele faz algo que nenhum operador humano consegue fazer bem em tempo real:

> Coordenar automaticamente decisões locais de processos diferentes, com base em um objetivo global.

É por isso que o documento fala explicitamente em **“otimização global em tempo real”**.

### 4.3 Como o RTO funciona na prática (dinâmica real)

Na Fase 1 do projeto, o RTO funciona como **suporte à decisão**. Ele:
- coleta dados da planta;
- analisa correlações;
- constrói modelos;
- identifica gargalos;
- calcula cenários;
- sugere ajustes operacionais.

Essas sugestões aparecem em **dashboards interativos**, onde o operador e o gestor conseguem ver coisas do tipo:
- “Se eu priorizar eficiência energética, o rendimento industrial cai X%”;
- “Se eu priorizar produtividade, o consumo de bagaço sobe Y%”;
- “Este equipamento está atuando como gargalo agora”.

Nesse estágio, o RTO **não atua automaticamente**. Ele é um **sistema de recomendação inteligente**. Ele funciona como um **cérebro analítico da operação**, que transforma dados brutos em decisões estratégicas.

### 4.4 A função de custo: o coração matemático do RTO
Mesmo que o documento não escreva isso em fórmula, conceitualmente o RTO resolve algo do tipo:

$$
\max_{x,u} \; J(x,u) = 
w_1 \cdot P(x,u)
+ w_2 \cdot E(x,u)
- w_3 \cdot L(x,u)
- w_4 \cdot R(x,u)
$$
onde:
- $P$ = produtividade;
- $E$ = eficiência energética;
- $L$ = perdas;
- $R$ = consumo de recursos;
- $w_i$ = pesos econômicos.

Sujeito a:
- limites físicos dos equipamentos;
- limites de segurança;
- gargalos detectados;
- metas estratégicas da empresa.

Esses pesos $w_i$ são definidos pela gestão, via interface:
- hoje quero priorizar produção;
- amanhã quero priorizar economia;
- em outro turno quero priorizar estabilidade.

Isso é extremamente importante: **o RTO é um otimizador com função de custo ajustável pelo negócio.**

Não é engenharia pura. É engenharia + gestão + economia.

### 4.5 O que esse RTO é, em essência profunda
Se formos reduzir tudo à essência: esse RTO é um **sistema cibernético de tomada de decisão econômica em tempo real**, aplicado a um sistema industrial físico complexo.

Ele faz cinco coisas ao mesmo tempo:
1. Observa a planta real;
2. Constrói um modelo operacional;
3. Detecta gargalos e restrições;
4. Resolve um problema de otimização global;
5. Traduz isso em metas operacionais.

Isso não é controle clássico. Isso é **engenharia de sistemas + ciência de dados + otimização + economia operacional**.

### 4.6 A frase mais precisa possível para esse caso
Se pudéssemos definir o RTO dessa proposta em uma frase técnica perfeita, seria:

> **O RTO é a camada que transforma dados industriais em decisões econômicas ótimas, coordenando automaticamente múltiplos processos interdependentes em tempo real.**

E essa frase não é retórica. Ela descreve exatamente o que esse sistema faz na prática, na planta real descrita na proposta.

---
# 5. Modelos Matemáticos do Processo
DRAFT

---
# 6. Módulo CAR
Um elemento central desse RTO é o **CAR – Identificador de Gargalos**.

O sistema monitora continuamente:
- correntes de motores;
- pressões;
- entupimentos;
- quedas de desempenho;
- saturações de atuadores.

Quando detecta um gargalo real, o RTO:
- penaliza esse ponto na otimização;
- muda suas recomendações;
- evita empurrar a planta para instabilidade.

Ou seja: o RTO **não otimiza um modelo ideal**, ele otimiza **a planta real, com defeitos, limitações e degradações**.

Isso é uma diferença brutal entre RTO acadêmico e RTO industrial.

---
# 7. Dashboards Interativos
DRAFT

---
# 8. Introdução à Fase 2
Na Fase 2 acontece a virada ontológica do sistema. O RTO deixa de ser apenas “consultivo” e passa a ser **executivo**.

Ele se integra ao APC, e passa a:
- escrever setpoints automaticamente;
- coordenar moagem, destilação e cogeração;
- fechar a malha de otimização global.    

A arquitetura vira:
RTO → APC → PLC → Planta

Agora o RTO não só pensa, ele **manda**. Mas observe a hierarquia:
- RTO decide **o que é ótimo**;
- APC decide **como chegar lá dinamicamente**;
- PLC/PID executa **fisicamente**.

O RTO nunca atua diretamente em válvula. Ele atua em **objetivos globais**.
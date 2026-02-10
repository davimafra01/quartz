# 1. Introdução

A Otimização em Tempo Real, conhecida pela sigla RTO, é uma metodologia avançada dentro do controle e automação industrial, cujo objetivo principal é **determinar continuamente os melhores parâmetros de operação para um processo**, de forma a maximizar eficiência, qualidade ou retorno econômico. Diferentemente do controle clássico, que apenas mantém variáveis em níveis desejados, o RTO atua estrategicamente, analisando o estado atual do processo, prevendo como ele reagirá a diferentes ajustes e sugerindo as condições ideais de operação.

O funcionamento do RTO depende de três elementos integrados:
- Coleta de dados $\rightarrow$ Dados reais;
- Modelo do processo $\rightarrow$ Modelagem;
- Algoritmo de otimização $\rightarrow$ Otimização.

Inicialmente, sensores e instrumentos medem variáveis críticas do processo, como temperaturas, pressões, vazões e composições químicas, fornecendo uma fotografia em tempo real da operação. Em seguida, essas informações alimentam um modelo matemático do processo, que pode ser baseado em balanços de massa e energia, em equações de reação química ou até em modelos empíricos que relacionam entradas e saídas do sistema. Esse modelo permite ao RTO simular diferentes cenários antes de qualquer intervenção, prevendo o efeito de ajustes em variáveis controláveis.

Com base nesse modelo, o RTO aplica algoritmos de otimização que consideram restrições físicas e operacionais, como limites de segurança, capacidade de equipamentos e qualidade desejada do produto. O resultado desse cálculo são os *setpoints* ideais para cada variável controlável, que são então enviados para os sistemas de controle de nível inferior, como o controle PID ou o *Advanced Process Control* (APC), para que as mudanças sejam implementadas de forma suave e segura. Dessa maneira, o RTO não substitui os controles existentes; ele define estrategicamente o ponto de operação ótimo, enquanto o controle garante estabilidade e precisão.

A principal vantagem do RTO é sua capacidade de responder às mudanças do ambiente industrial de forma dinâmica. Mudanças no preço de matérias-primas, variações na demanda ou pequenas flutuações no processo podem ser rapidamente integradas à otimização, ajustando os *setpoints* em tempo real para maximizar eficiência e reduzir desperdício. Contudo, o sucesso do RTO depende diretamente da precisão do modelo e da confiabilidade dos dados. Modelos imprecisos ou sensores com atraso podem levar a decisões subótimas ou até prejudicar a operação.

O RTO é amplamente utilizado em setores como refinarias de petróleo, indústrias químicas, plantas de energia e produção de alimentos. Nessas aplicações, decisões estratégicas, como a proporção ideal de matérias-primas, a temperatura de reação ou a distribuição de fluxos, impactam diretamente no lucro e na eficiência operacional. Ao integrar (i) dados reais, (ii) modelagem e (iii) otimização, o RTO permite que as plantas industriais operem de forma próxima do ponto ótimo, mesmo em condições variáveis e complexas.

Em resumo, o RTO é a ferramenta que transforma dados em decisões estratégicas, conectando a operação diária do processo com objetivos de eficiência e lucro. Ele se diferencia do controle clássico por sua visão antecipatória e holística do processo, definindo o melhor caminho de operação enquanto PID e APC garantem que esse caminho seja seguido com estabilidade. Em essência, o RTO é o elo entre a operação operacional e a otimização econômica, fornecendo inteligência estratégica para processos industriais complexos.

---
# 2. RTO na Coluna de Destilação de Petróleo

No contexto de uma coluna de destilação de petróleo, o RTO atua como um sistema estratégico de decisão, cuja função é encontrar continuamente os melhores pontos de operação que maximizem a produção de gasolina de qualidade, minimizem o consumo de energia e mantenham a operação dentro dos limites de segurança. Diferente do PID ou do APC, que reagem a desvios e coordenam múltiplas variáveis respectivamente, o RTO trabalha a partir de modelos matemáticos do processo, levando em consideração tanto restrições físicas quanto variáveis econômicas, e calcula os *setpoints* ideais que serão aplicados pelos níveis de controle inferiores.

**Coleta de Dados:**
ORTO começa com a coleta de dados em tempo real. Sensores ao longo da coluna medem temperaturas em bandejas chave, pressão na coluna, vazão de alimentação, refluxo e saída de produtos. Além disso, analisadores on-line fornecem composição química das frações, como teor de octanas da gasolina ou densidade do diesel. Esses dados formam o estado atual do processo e são essenciais para alimentar o modelo do RTO.

**Modelagem:**
O modelo do processo usado pelo RTO é uma representação matemática detalhada da coluna. Ele inclui balanços de massa e energia para cada bandeja, equações de equilíbrio líquido-vapor para os componentes químicos, coeficientes de transferência de calor e massa e restrições operacionais, como pressões máximas e mínimas, limites de temperatura para evitar degradação do produto e capacidade máxima de bombeamento. Esse modelo permite que o RTO simule virtualmente como diferentes combinações de entradas — vazão de petróleo, aquecimento na base, vazão de refluxo, pressão de operação — afetarão a produção e a qualidade das frações, bem como o consumo energético.

**Otimização:**
Com base nesse modelo e nos dados atuais, o RTO aplica algoritmos de otimização, que podem ser lineares ou não lineares, dependendo da complexidade do processo. A função objetivo normalmente combina lucro líquido, consumo de energia e qualidade do produto. Por exemplo, se o preço da gasolina estiver alto e o do diesel baixo, o RTO priorizará a produção de gasolina, ajustando o refluxo e a temperatura da coluna para extrair mais frações leves, sem comprometer a estabilidade do processo. Ao mesmo tempo, ele minimiza o custo do vapor de aquecimento e evita ultrapassar limites de pressão que poderiam danificar a coluna. O algoritmo calcula os *setpoints* ótimos para cada variável controlável, determinando valores precisos de temperatura no topo e fundo da coluna, vazão de refluxo, pressão e proporção de extração de produtos.

O RTO não atua isoladamente; ele envia esses *setpoints* estratégicos para o APC ou diretamente para sistemas de controle que implementam os ajustes. Por exemplo, se o RTO determinar que o refluxo deve aumentar 5% para melhorar a qualidade da gasolina, o APC fará uma série de ajustes coordenados na coluna, distribuindo o refluxo, ajustando aquecimento e modificando pequenas vazões de alimentação, garantindo que as mudanças ocorram suavemente, sem provocar instabilidade. O PID, por sua vez, manterá cada variável próxima ao novo *setpoint* definido pelo RTO, reagindo a pequenas flutuações momentâneas.

Outro detalhe importante é que o RTO opera em ciclos periódicos, que podem variar de minutos a horas, dependendo da dinâmica do processo. Cada ciclo envolve a leitura dos dados atuais, a atualização do modelo do processo com as novas condições, a execução do algoritmo de otimização e a aplicação dos novos setpoints. Em processos mais dinâmicos ou com preços de insumos e produtos variando rapidamente, os ciclos podem ser consideravelmente mais curtos.

Além disso, o RTO permite simulações preditivas e cenários “*what-if*”, que são essenciais em plantas de destilação. Ele pode prever como uma variação no preço do petróleo ou uma alteração na qualidade da alimentação impactará a produção, o consumo de energia e a rentabilidade. Com essas previsões, o RTO pode recomendar ajustes antes mesmo que a condição real se manifeste, tornando a operação proativa e não apenas reativa. Ele também pode identificar restrições críticas que limitam o desempenho, como limites de pressão ou capacidade de aquecimento, e sugerir estratégias para otimizar o processo dentro desses limites.

A eficácia do RTO depende da precisão do modelo do processo e da confiabilidade dos dados. Sensores defeituosos ou atrasos nas medições podem levar a *setpoints* subótimos, enquanto modelos simplificados podem não capturar interações complexas entre variáveis. Por isso, em plantas industriais, o RTO é frequentemente atualizado e calibrado com dados históricos e experiências de operação, garantindo que as recomendações continuem precisas ao longo do tempo.

Em resumo, o RTO em uma coluna de destilação de petróleo funciona como um gerente estratégico da planta, conectando variáveis operacionais, restrições físicas e objetivos econômicos. Ele decide onde o processo deve operar, considerando custos, receitas, limites de operação e qualidade do produto, e envia *setpoints* precisos para os níveis de controle que efetivamente ajustam a operação. Com isso, a refinaria consegue operar de maneira próxima do ponto ótimo, adaptando-se continuamente a mudanças no mercado e no processo, maximizando lucro e eficiência energética sem comprometer a segurança ou a qualidade do produto.

---
# 3. Análise Numérica Coluna de Destilação de Petróleo
### 3.1 Dados iniciais do processo
Considere uma coluna de destilação com 30 bandejas, operando com petróleo cru a 350°C, com as seguintes variáveis de entrada e limites:
- **Vazão de alimentação (F)**: 1000 m³/h (variação ±10%);
- **Temperatura no topo (T_top)**: 100°C (limite 95–105°C);
- **Temperatura no fundo (T_base)**: 350°C (limite 340–360°C);
- **Pressão da coluna (P_col)**: 1,5 bar (limite 1,0–2,0 bar);
- **Vazão de refluxo (R)**: 200 m³/h (limite 150–250 m³/h);
- **Produção de gasolina (G)**: 600 m³/h inicial, com teor de octanas 90;
- **Produção de diesel (D)**: 300 m³/h inicial, densidade 0,85 g/cm³;
- **Custo do vapor de aquecimento (C_vapor)**: R$ 0,10/kWh;
- **Preços de mercado**: gasolina R$ 5,50/L, diesel R$ 4,00/L.

### 3.2 Modelo simplificado da coluna
O RTO precisa de um modelo que relacione entradas e saídas. Um modelo clássico simplificado envolve **balanceamento de massa e energia** e **curvas de eficiência**:

'1. **Produção de gasolina (G) em função de refluxo e temperatura do topo**: 

$G=600+10⋅(Ttop−100)−5⋅(R−200)G = 600 + 10 \cdot (T_{\text{top}} - 100) - 5 \cdot (R - 200)G=600+10⋅(Ttop​−100)−5⋅(R−200)$

- Aumentar T_top aumenta volatilidade → mais gasolina
    
- Aumentar R aumenta recuperação da gasolina, mas reduz vazão do topo
    

2. **Produção de diesel (D) em função de T_base e refluxo**:
    

D=300−5⋅(Ttop−100)+3⋅(R−200)D = 300 - 5 \cdot (T_{\text{top}} - 100) + 3 \cdot (R - 200)D=300−5⋅(Ttop​−100)+3⋅(R−200)

3. **Consumo de vapor (E)**:
    

E=500+2⋅(Tbase−350)+0,5⋅(R−200)E = 500 + 2 \cdot (T_{\text{base}} - 350) + 0,5 \cdot (R - 200)E=500+2⋅(Tbase​−350)+0,5⋅(R−200)

- kWh/h de vapor consumido, usado para custo econômico.
    

4. **Lucro por hora (L)**:
    

L=5,50⋅G+4,00⋅D−0,10⋅EL = 5,50 \cdot G + 4,00 \cdot D - 0,10 \cdot EL=5,50⋅G+4,00⋅D−0,10⋅E

> Observação: todas as unidades foram simplificadas para facilitar o cálculo.

---

### 3.3 Situação inicial

- T_top = 100°C, T_base = 350°C, R = 200 m³/h
    
- Produção: G = 600 m³/h, D = 300 m³/h
    
- Consumo de vapor: E = 500 kWh
    
- Lucro: L = 5,50_600 + 4_300 - 0,10*500 = 3300 + 1200 - 50 = R$ 4.450/h
    

---

### 3.4 Otimização do RTO

O RTO busca **maximizar L** variando T_top, T_base e R, respeitando limites:

- 95°C ≤ T_top ≤ 105°C
    
- 340°C ≤ T_base ≤ 360°C
    
- 150 ≤ R ≤ 250
    

O RTO aplica otimização simples (gradiente ou busca discreta):

1. **Variação T_top +2°C → T_top = 102°C**
    
    - G = 600 + 10*(102-100) - 5*(200-200) = 620 m³/h
        
    - D = 300 - 5*(102-100) + 3*(200-200) = 290 m³/h
        
    - E = 500 + 2*(350-350) + 0,5*(200-200) = 500 kWh
        
    - L = 5,50_620 + 4_290 - 0,10*500 = 3410 + 1160 - 50 = 4520/h
        
2. **Aumento do refluxo +10 → R = 210 m³/h**
    
    - G = 600 + 10*(102-100) - 5*(210-200) = 620 - 50 = 570 m³/h?
        

Vamos calcular com cuidado:  
G = 600 + 10*(102-100) - 5*(210-200) = 600 + 20 - 50 = 570 m³/h  
D = 300 - 5*(102-100) + 3*(210-200) = 300 - 10 + 30 = 320 m³/h  
E = 500 + 2*(350-350) + 0,5*(210-200) = 500 + 0 + 5 = 505 kWh  
L = 5,50_570 + 4_320 - 0,10*505 = 3135 + 1280 - 50,5 ≈ 4364,5 R$/h

> Observação: neste caso, aumentar refluxo aumentou diesel, mas diminuiu gasolina, o que reduziu o lucro.

3. **Ajuste T_base +5°C → T_base = 355°C**
    
    - G = 600 + 10*(102-100) - 5*(210-200) = 570 m³/h (mesmo)
        
    - D = 300 - 5*(102-100) + 3*(210-200) = 320 m³/h
        
    - E = 500 + 2*(355-350) + 0,5*(210-200) = 500 + 10 + 5 = 515 kWh
        
    - L = 5,50_570 + 4_320 - 0,10*515 = 3135 + 1280 - 51,5 ≈ 4363,5 R$/h
        

O RTO conclui que o **ponto ótimo é T_top = 102°C, T_base = 350°C, R = 200 m³/h**, com lucro L ≈ 4.520 R$/h, dentro das restrições e com consumo de energia mínimo.

---

### 3.5 Interpretação

O RTO avaliou **cenários simultâneos**, considerando restrições de temperatura, pressão e vazão, bem como impacto econômico de gasolina, diesel e energia. Ele determinou que aumentar o refluxo ou a temperatura do fundo além de certos limites não traria lucro adicional, e poderia prejudicar a qualidade ou gerar consumo de energia elevado. Os setpoints recomendados são enviados ao APC, que coordena ajustes de maneira suave e controlada, enquanto o PID mantém cada variável estável em tempo real.
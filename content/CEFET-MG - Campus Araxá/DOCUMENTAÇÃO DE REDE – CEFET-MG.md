# DOCUMENTAÇÃO TÉCNICA DA REDE – CEFET-MG

## Sumário

1. Introdução
2. Fundamentos de Endereçamento IPv4
3. Blocos Públicos  
    3.1 Bloco 200.128.128.0/18  
    3.2 Subdivisão Interna: 200.128.128.0/22  
    3.3 Bloco 200.131.0.0/16  
    3.4 Subdivisão do bloco 200.131.0.0/16
4. Segmentação por VLANs
5. Blocos Privados IPv4
6. Considerações de Arquitetura
7. Apêndice A – Derivação Binária e Cálculo de Sub-redes

---
## 1. Introdução

Este documento descreve, em nível técnico, a estrutura de endereçamento IPv4 da rede do CEFET-MG. São abordados os blocos públicos atribuídos, suas subdivisões, a segmentação lógica por VLANs e o uso de redes privadas.

O foco é a rastreabilidade dos cálculos e a compreensão formal da estrutura de rede.

---
## 2. Fundamentos de Endereçamento IPv4

Um endereço IPv4 possui 32 bits, divididos em:

- Parte de rede (prefixo)
- Parte de host

A notação CIDR `/n` indica que os primeiros `n` bits pertencem à rede.

Exemplo:

```
200.128.128.0/18
```

- 18 bits de rede
- 14 bits de host

---
## 3. Blocos Públicos

### 3.1 Bloco 200.128.128.0/18 [A1]

- Endereço de rede: 200.128.128.0
- Máscara: 255.255.192.0
- Intervalo: 200.128.128.0 – 200.128.191.255

Este bloco representa uma alocação contínua de endereços públicos.

---
### 3.2 Subdivisão Interna: 200.128.128.0/22 [A2]

- Endereço de rede: 200.128.128.0
- Máscara: 255.255.252.0
- Intervalo: 200.128.128.0 – 200.128.131.255

Essa rede corresponde a uma subdivisão do bloco /18.

---
### 3.3 Bloco 200.131.0.0/16 [A3]

- Endereço de rede: 200.131.0.0
- Máscara: 255.255.0.0
- Intervalo: 200.131.0.0 – 200.131.255.255

Este bloco fornece capacidade ampliada de endereçamento.

---
### 3.4 Subdivisão do bloco 200.131.0.0/16 [A4]

A VLAN 1 utiliza a sub-rede:

- 200.131.40.0/24

Isso implica que o bloco /16 está sendo segmentado em múltiplas redes /24.

- Incremento no terceiro octeto: 1
- Cada sub-rede possui 256 endereços

---
## 4. Segmentação por VLANs

A rede é segmentada logicamente para isolar funções e otimizar controle de tráfego.

| VLAN    | Finalidade                                               | Rede             | Intervalo                       |
| ------- | -------------------------------------------------------- | ---------------- | ------------------------------- |
| VLAN 1  | Dispositivos (servidores internos, câmeras, impressoras) | 200.131.40.0/24  | 200.131.40.0 – 200.131.40.255   |
| VLAN 10 | Servidores públicos                                      | 200.128.128.0/22 | 200.128.128.0 – 200.128.131.255 |
| VLAN 20 | Alunos                                                   | 200.128.132.0/22 | 200.128.132.0 – 200.128.135.255 |
| VLAN 65 | Telefonia                                                | 10.65.1.0/24     | 10.65.1.0 – 10.65.1.255         |

---
## 5. Blocos Privados IPv4

|Bloco|Máscara|Intervalo|
|---|---|---|
|10.0.0.0/8|255.0.0.0|10.0.0.0 – 10.255.255.255|
|172.16.0.0/12|255.240.0.0|172.16.0.0 – 172.31.255.255|
|192.168.0.0/16|255.255.0.0|192.168.0.0 – 192.168.255.255|

---
## 6. Considerações de Arquitetura

- Separação entre serviços públicos e internos
- Uso de VLANs para isolamento de domínios de broadcast
- Uso de rede privada para serviços não expostos
- Subdivisão hierárquica baseada em CIDR

---
## 7. Apêndice A – Derivação Binária e Cálculo de Sub-redes

### [A1] 200.128.128.0/18

Endereço em binário:

```
200      .128      .128      .0
11001000 .10000000 .10000000 .00000000
```

Máscara /18:

```
11111111.11111111.11000000.00000000
```

Separação:

```
Rede:   11001000.10000000.10
Host:                        000000.00000000
```

Bits de host:

$$  
32 - 18 = 14  
$$

Total:

$$  
2^{14} = 16.384  
$$

Faixa no 3º octeto:

```
10000000 (128)
até
10111111 (191)
```

---
### [A2] 200.128.128.0/22

Máscara:

```
11111111.11111111.11111100.00000000
```

Rede:

```
11001000.10000000.100000|00.00000000
```

Bits de host:

$$  
10  
$$

Faixa:

```
10000000 (128)
até
10000011 (131)
```

---
### [A3] 200.131.0.0/16

Máscara:

```
11111111.11111111.00000000.00000000
```

Bits de host:

$$  
16  
$$

---
### [A4] 200.131.40.0/24

Endereço:

```
200      .131      .40       .0
11001000 .10000011 .00101000 .00000000
```

Máscara:

```
11111111.11111111.11111111.00000000
```

Separação:

- 24 bits de rede
- 8 bits de host

Faixa:

```
.00000000 (0)
até
.11111111 (255)
```

Total:

$$  
2^{8} = 256  
$$

---
### Observação Geral

A lógica de subnetting utilizada baseia-se em:

1. Conversão decimal → binário
2. Aplicação da máscara (AND lógico)
3. Determinação de:
    - Endereço de rede
    - Broadcast
    - Intervalo válido
4. Uso de incrementos baseados nos bits variáveis
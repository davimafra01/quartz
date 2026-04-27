## Sumário

1. Introdução  
2. Blocos Públicos  
   2.1 Primeiro Bloco Público (200.128.128.0/18)  
   2.2 Sub-rede Interna (200.128.128.0/22)  
   2.3 Segundo Bloco Público (200.131.0.0/16)  
3. Segmentação por VLANs  
4. Blocos Privados IPv4  
5. Considerações Gerais  
6. Apêndice A – Metodologia de Cálculo e Derivação dos Intervalos  

---
## 1. Introdução

Este documento descreve a estrutura de endereçamento IP da rede do CEFET-MG, incluindo os blocos públicos atribuídos, sua subdivisão interna, a segmentação por VLANs e o uso de endereços privados.

O objetivo é fornecer uma visão clara, organizada e técnica da rede, servindo como base para operação, manutenção e expansão.

---
## 2. Blocos Públicos

### 2.1 Primeiro Bloco Público (200.128.128.0/18) [A1]

- **Endereço de rede:** 200.128.128.0  
- **Máscara:** /18  
- **Endereço inicial:** 200.128.128.0  
- **Endereço final:** 200.128.191.255  

Este bloco representa um conjunto contínuo de endereços IP públicos disponíveis para uso institucional.

---
### 2.2 Sub-rede Interna (200.128.128.0/22) [A2]

- **Endereço de rede:** 200.128.128.0  
- **Máscara:** /22  
- **Endereço inicial:** 200.128.128.0  
- **Endereço final:** 200.128.131.255  

Trata-se de uma subdivisão do bloco público maior, utilizada para organização interna da rede.

---
### 2.3 Segundo Bloco Público (200.131.0.0/16) [A3]

- **Endereço de rede:** 200.131.0.0  
- **Máscara:** /16  
- **Endereço inicial:** 200.131.0.0  
- **Endereço final:** 200.131.255.255  

Este bloco amplia significativamente a disponibilidade de endereços públicos para a instituição.

---
## 3. Segmentação por VLANs

A segmentação lógica da rede é realizada por meio de VLANs, permitindo isolamento entre diferentes domínios administrativos ou funcionais.

| VLAN    | Rede             | Intervalo                       | Hosts  |
| ------- | ---------------- | ------------------------------- | ------ |
| VLAN 1  | 200.131.40.0/24  | 200.131.40.0 – 200.131.40.255   | 256    |
| VLAN 10 | 200.128.128.0/22 | 200.128.128.0 – 200.128.131.255 | 1.024  |
| VLAN 20 | 200.128.132.0/22 | 200.128.132.0 – 200.128.135.255 | 65.536 |
| VLAN 65 | 10.65.1.0/24     | 10.65.1.0 – 10.65.1.255         | 256    |

Observa-se que a rede utiliza tanto endereçamento público quanto privado, conforme a finalidade da VLAN.

---
## 4. Blocos Privados IPv4

Os blocos privados seguem as definições padronizadas para redes internas. Para fins de conhecimento:

### 4.1 Bloco 10.0.0.0/8 [A4]

- Intervalo: 10.0.0.0 – 10.255.255.255  

### 4.2 Bloco 172.16.0.0/12 [A5]

- Intervalo: 172.16.0.0 – 172.31.255.255  

### 4.3 Bloco 192.168.0.0/16 [A6]

- Intervalo: 192.168.0.0 – 192.168.255.255  

---
## 5. Considerações Gerais

A arquitetura de endereçamento da rede apresenta:

- Uso estruturado de blocos públicos atribuídos  
- Subdivisão eficiente em redes menores  
- Segmentação lógica por VLANs  
- Integração com redes privadas para uso interno  

Essa organização favorece escalabilidade, controle e segurança da infraestrutura.

---
## 6. Apêndice A – Metodologia de Cálculo e Derivação dos Intervalos

### [A1] Bloco 200.128.128.0/18

Máscara /18:

$$
32 - 18 = 14 \text{ bits para hosts}
$$

Total de endereços:

$$
2^{14} = 16.384
$$

Faixa no terceiro octeto:

- Incremento: 64 (pois 256 - 192 = 64)  
- Intervalo: 128 até 191  

---
### [A2] Sub-rede 200.128.128.0/22

Máscara /22:

$$
32 - 22 = 10 \text{ bits para hosts}
$$

Total de endereços:

$$
2^{10} = 1.024
$$

Faixa no terceiro octeto:

- Incremento: 4  
- Intervalo: 128 até 131  

---
### [A3] Bloco 200.131.0.0/16

Máscara /16:

$$
32 - 16 = 16 \text{ bits para hosts}
$$

Total de endereços:

$$
2^{16} = 65.536
$$

---
### [A4] Bloco 10.0.0.0/8

$$
32 - 8 = 24
$$

$$
2^{24} = 16.777.216
$$

---
### [A5] Bloco 172.16.0.0/12

$$
32 - 12 = 20
$$

$$
2^{20} = 1.048.576
$$

---
### [A6] Bloco 192.168.0.0/16

$$
32 - 16 = 16
$$

$$
2^{16} = 65.536
$$
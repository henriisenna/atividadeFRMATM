# Atividade FRM & ATM
Instituto Federal de Mato Grosso Estudante: Henrique Luiz de Sousa Senna Matrícula: 2018178440047 Curso: Engenharia da Computação Disciplina: Redes de Computadores II 

# Apresentação de Resultados obtidos:
Visão geral do projeto

![WhatsApp Image 2023-04-11 at 17 04 13 jpeg](https://user-images.githubusercontent.com/54629648/231667954-12aada20-27f8-40f2-88ed-b4c216e01fe3.png)

## Listagem dos IP´S

|Rede|Roteador|IP|
|-|-|-|
|FR|R1|10.10.0.1|
|FR|R2|10.10.0.2|
|FR|R5|10.10.0.3|
|ATM|R3|10.10.10.1|
|ATM|R4|10.10.10.3|
|ATM|R5|10.10.10.2|

## Listagem das portas FRSW:

|Nome|Porta|DLCI|Porta|DLCI|
|-|-|-|-|-|
|FRSW1|1|101|10|202|
|FRSW1|1|102|12|203|
|FRSW2|1|101|10|202|
|FRSW2|1|103|11|203|
|FRSW3|1|101|11|203|
|FRSW3|1|102|12|203|

___

## Listagem das portas do ATMSW:

|Name|Port|VPI|VCI|Port|VPI|VCI|
|-|-|-|-|-|-|-|
|ATMSW1|1|10|100|10|10|200|
|ATMSW1|1|11|101|11|11|201|
|ATMSW2|1|10|100|10|10|200|
|ATMSW2|1|20|200|12|10|200|
|ATMSW3|1|11|100|11|11|201|
|ATMSW3|1|12|100|12|10|200|

### Configuração dos Roteadores na rede Frame-Relay:
# R1:
```
configure terminal
int Serial1/0
ip address 10.10.0.1 255.255.255.0
encapsulation frame-relay
frame-relay intf-type dte
frame-relay map ip 10.10.0.2 101 broadcast
no shut
end
```
# R2:
```
configure terminal
int Serial1/0
ip address 10.10.0.2 255.255.255.0
encapsulation frame-relay
frame-relay intf-type dte
frame-relay map ip 10.10.0.1 101 broadcast
no shut
end
```

### Configuração dos Roteadores na rede ATM.

# R3:
```
configure terminal
int atm1/0
no shutdown
exit
int atm1/0.10 multipoint 
ip add 10.10.10.1 255.255.255.0
pvc 10/100
protocol ip 10.10.10.2 broadcast
encapsulation aal5snap
pvc 11/101
protocol ip 10.10.10.3 broadcast
encapsulation aal5snap
end
```

# R4:
```
configure terminal
int atm1/0
no shutdown
int atm1/0.10 multipoint 
ip add 10.10.10.3 255.255.255.0
pvc 11/100
protocol ip 10.10.10.1 broadcast
encapsulation aal5snap
pvc 12/100
protocol ip 10.10.10.2 broadcast
encapsulation aal5snap
end
```
### Interface Serial Frame-Relay:
```
configure terminal
int Serial1/0
ip add 10.0.0.3 255.255.255.0
encapsulation frame-relay
frame-relay intf-type dte
frame-relay map ip 10.0.0.2 101 broadcast
frame-relay map ip 10.0.0.1 102 broadcast
no shut
end
```

### Interface ATM:
```
configure terminal
int atm2/0
no shutdown
int atm2/0.10 multipoint 
ip add 10.10.10.2 255.255.255.0
pvc 10/100
protocol ip 10.10.10.1 broadcast
encapsulation aal5snap
pvc 20/200
protocol ip 10.10.10.3 broadcast
encapsulation aal5snap
end
```
# Resultado dos Pings: 

# R1 Para R2:

![r1-r2](https://user-images.githubusercontent.com/54629648/231662229-498e0fea-c79c-4d52-b0a2-b04e8bb1f1b4.png)

# R1 Para R5

![r1-r5](https://user-images.githubusercontent.com/54629648/231664516-4f4b4467-e1e9-4417-b819-35e0ac86e792.png)

# R2 Para R1:

![r2-r1](https://user-images.githubusercontent.com/54629648/231662434-3caf1d59-c973-4568-acab-dae385daaf67.png)

# R2 Para R5

![r2-r5](https://user-images.githubusercontent.com/54629648/231664986-d62ab2da-0d28-4630-9091-4f778f92bca4.png)

# R3 Para R5

![r3-r5](https://user-images.githubusercontent.com/54629648/231662364-aa6a98c9-34b3-4442-b9eb-8f8d4f5526a4.png)

# R3 Para R4

![r3-r4](https://user-images.githubusercontent.com/54629648/231662345-85a7ca12-7819-4b78-b15d-96a1fda734f8.png)

# R4 Para R5

![r4-r5](https://user-images.githubusercontent.com/54629648/231662286-2d64a998-61e1-4c51-ada8-0d350d9e7931.png)

# R4 Para R3

![r4-r3](https://user-images.githubusercontent.com/54629648/231662266-583c365b-51a9-4285-a8c3-f57e296acd9f.png)

# R5 Para R2:

![r5-r2](https://user-images.githubusercontent.com/54629648/231666407-631c1504-463d-4e00-833c-3269a97c4ce9.png)

# R5 Para R3

![r5-r3](https://user-images.githubusercontent.com/54629648/231662319-aa559c80-4fad-4291-a014-57f47c730170.png)

# R5 Para R1

![r5-r1](https://user-images.githubusercontent.com/54629648/231666445-fe109eeb-0924-4ab0-8e8a-7998f9b19524.png)

# R5 Para R4

![r5-r4](https://user-images.githubusercontent.com/54629648/231666457-c46c81f0-e9dc-4c30-9cd2-794630bc2674.png)

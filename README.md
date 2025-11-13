# Projeto Conceitual – Sistema de Ordem de Serviço (Oficina Mecânica)
Projeto desenvolvido como parte do Desafio de Banco de Dados da **Digital Innovation One (DIO)**.  
O objetivo é criar um **esquema conceitual do zero**, a partir da narrativa proposta, modelando o funcionamento de uma oficina mecânica.

---

## Narrativa Utilizada

- Clientes levam veículos à oficina para conserto ou revisão.
- Cada veículo é associado a uma **equipe de mecânicos**, que identifica os serviços necessários.
- Após o diagnóstico, uma **Ordem de Serviço (OS)** é emitida com data prevista de conclusão.
- O valor da OS é composto por:
  - serviços realizados (mão de obra),
  - peças utilizadas.
- Mecânicos possuem: código, nome, endereço e especialidade.
- Cada OS possui: número, data de emissão, valor total, status e data de conclusão.

---

## Entidades e Atributos

### **Cliente**
- `idCliente` (PK)  
- `Nome`  
- `Endereço`  
- `Telefone`  

---

### **Veículo**
- `idVeículo` (PK)  
- `Modelo`  
- `Marca`  
- `Ano`  
- `Placa`  
- `Cliente_idCliente` (FK)

---

### **Equipe**
- `idEquipe` (PK)  
- `Nome`

---

### **Mecanico**
- `idMecanico` (PK)  
- `Nome` 
- `Especialidade`  
- `Equipe_idEquipe` (FK)

---

### **OS** (Ordem de Serviço)
- `idOS` (PK)  
- `Data Inicial`  
- `Data Final`  
- `Status`  
- `Valor`  
- `Veículo_idVeiculo` (FK)  
- `Equipe_idEquipe` (FK)

---

### **Peca**
- `idPeca` (PK)  
- `Nome`  
- `Valor da unidade`

---

### **Servico**
- `idServico` (PK)  
- `Descricao`  
- `Valor da mao de obra`

---

### **Peca_has_OS** (Relação N:N entre Peça e OS)
- `Peca_idPeca` (FK)  
- `OS_idOS` (FK)  
- `Quantidade`

---

### **ServicoConcluido** (Relação N:N entre Serviço e OS)
- `OS_idOS` (FK)  
- `Servico_idServico` (FK)  
- `quantidade`

---

## 🔗 Relacionamentos

| Entidade A | Relacionamento | Entidade B | Tipo |
|------------|----------------|------------|------|
| Cliente | possui | Veículos | 1:N |
| Veículo | gera | OS | 1:N |
| Equipe | executa | OS | 1:N |
| Equipe | contém | Mecânicos | 1:N |
| OS | utiliza | Serviços | N:N |
| OS | utiliza | Peças | N:N |

---

## 🖼️ Diagrama Conceitual

![Diagrama da Oficina](https://raw.githubusercontent.com/Sugaharaa/Projeto-DIO-SQL-OS/main/Diagrama/diagrama.png)



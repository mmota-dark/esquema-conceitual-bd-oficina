# Esquema Conceitual - Oficina Mecânica 📝

Este projeto representa o **esquema conceitual de um sistema de controle e gerenciamento de ordens de serviço em uma oficina mecânica**.  

## Narrativa

- Clientes levam veículos à oficina para conserto ou revisão.  
- Cada veículo é designado a uma equipe de mecânicos, que identifica os serviços necessários e abre uma **Ordem de Serviço (OS)**.  
- A OS contém data de emissão, previsão de conclusão, valor total e status.  
- Os serviços têm seus valores calculados a partir de uma tabela de referência de mão-de-obra.  
- Peças utilizadas também são registradas na OS.  
- O cliente precisa autorizar a execução dos serviços.  
- A equipe de mecânicos realiza a execução da OS.  
- Mecânicos possuem **código, nome, endereço e especialidade**.  

## Modelo Entidade-Relacionamento (MER)

### Entidades Principais
- **Cliente**: id_cliente, nome, endereço, telefone, email  
- **Veículo**: id_veiculo, placa, marca, modelo, ano, id_cliente  
- **Ordem de Serviço (OS)**: id_os, data_emissao, data_conclusao, status, valor_total, id_cliente, id_veiculo, id_equipe    
- **Serviço**: id_servico, descricao, valor_mao_obra  
- **Peça**: id_peca, nome_peça, valor_unitario_pec  
- **Equipe Mecânicos**: id_equipe, nome_eq  
- **Mecânico**: id_mecanico, nome_mec, endereco_mec, especialidade_mec, id_equipe    

### Relacionamentos
- Cliente **possui** veículo(s) (1:N)  
- Cliente, Veículo, Equipe Mecânicos **estão associados a** Ordem de Serviço (OS)
- Mecânico **pertence** a Equipe Mecânicos (N:N)
- OS **inclui** serviços (N:M via OS_SERVICO)  
- OS **utiliza** peças (N:M via OS_PECA)  
- OS **é composta por** Serviço
- OS **é composta por** Peça

## Observações
- Criadas tabelas de associação para OS_SERVICO e OS_PECA.  
- O atributo **valor_total** da OS é calculado com base na soma dos serviços e peças.  
- Caso o cliente não autorize, a OS não é executada (atributo status cobre essa situação).
- O esquema foi desenvolvido usando o [draw.io](https://app.diagrams.net/)

---
## Imagem:

![Diagrama Conceitual Oficina Mecânica](https://github.com/mmota-dark/esquema-conceitual-bd-oficina/blob/main/Esquema-Conceitual-BD-Oficina-Mecanica-drawio.png)

---
O esquema conceitual desenvolvido busca representar de forma clara o fluxo de informações dentro de uma oficina mecânica, desde o registro do cliente até a execução e finalização da ordem de serviço. Esse modelo serve como base para o desenvolvimento lógico e físico do banco de dados, garantindo consistência e facilitando futuras expansões do sistema, como relatórios gerenciais e integração com sistemas financeiros.

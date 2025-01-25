# DIO Modelo EER: E-Commerce
Projeto de Modelagem Conceitual de Banco de Dados usando **MySQL Workbench**

Este repositório contém o esquema de banco de dados conceitual para uma plataforma de e-commerce projetada para gerenciar vendas de produtos por vendedores terceirizados por meio de uma plataforma on-line centralizada. O esquema modela as principais entidades e seus relacionamentos.

## Visão Geral

Aqui, assumo que plataforma de e-commerce permite que os clientes comprem produtos listados por vendedores terceirizados, e que a plataforma lida com inventário (estoque)


- **Gerenciamento de estoque centralizado**: Um único sistema de estoque compartilhado entre todos os vendedores.
- **Suporte flexível ao cliente**: Tratamento separado de clientes individuais (CPF) e empresariais (CNPJ).
- **Opções de pagamento**: Suporte para vários métodos de pagamento pré-registrados para clientes.
- **Rastreamento de entrega**: Um mecanismo para rastrear status de entrega, incluindo um histórico detalhado de alterações de status.

## Schema Highlights

O esquema inclui as seguintes entidades principais:

### 1. **Cliente**

- Suporta contas individuais e empresariais (CPF ou CNPJ).
- Captura informações essenciais como nome, endereço e número de registro.
- Garante diferenciação clara entre os tipos de clientes por meio de um campo `tipoCliente` ("PF" ou "PJ").

### 2. **Produto**

- Representa itens disponíveis para venda.
- Gerenciado em um inventário centralizado, independentemente do vendedor.
- Associado a um fornecedor, mas pode ser listado por vários vendedores.

### 3. **Fornecedor**

- Gerencia os fornecedores responsáveis pelo fornecimento dos produtos.

### 4. **TerceiroVendedor**

- Permite que vendedores listem seus produtos na plataforma.
- Rastreia relacionamentos com produtos por meio da tabela `Produtos_por_Vendedor`.

### 5. **Estoque**

- Sistema de inventário centralizado rastreia quantidades de produtos disponíveis na plataforma.

### 6. **Pedido**

- Rastreia as compras do cliente, incluindo produtos associados, detalhes de entrega e status do pagamento.
- Permite o rastreamento da janela de devolução com um campo para `data_devolucao`.

### 7. **Entrega (Entrega)**

- Armazena detalhes da entrega, incluindo o status atual e um código de rastreamento exclusivo.
- Uma tabela separada `Historico_Status_Entrega` registra todas as alterações de status para auditoria e suporte ao cliente.

### 8. **Pagamento**

- Captura informações de pagamento para cada pedido.
- Os clientes podem registrar vários métodos de pagamento por meio de uma tabela `Pagamento`.

## Principais relacionamentos

- **Cliente -> Pedido**: Um cliente pode fazer vários pedidos.
- **Pedido -> Produto**: Os pedidos podem incluir vários produtos, e os produtos podem pertencer a vários pedidos.
- **TerceiroVendedor -> Produto**: Os vendedores podem listar vários produtos, e os produtos podem ser listados por vários vendedores.
- **Entrega -> Histórico\_Status\_Entrega**: Cada entrega pode ter várias atualizações de status ao longo do tempo.

## Uso

Este repositório foi criado para orientar o desenvolvimento da camada de banco de dados para uma plataforma de e-commerce. Os desenvolvedores podem usar o esquema para configurar seu banco de dados e modificá-lo com base nos requisitos de negócios em evolução.

Contribuições são bem-vindas!

![Ecommerce](https://github.com/user-attachments/assets/45f245bd-59f6-465b-a19c-5dc71b3354e2)

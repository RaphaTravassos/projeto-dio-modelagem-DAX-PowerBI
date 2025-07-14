## 💼 Desafio DIO: Modelagem Dimensional e Transformação com DAX no Power BI

---

## 📌 Descrição do Desafio

A proposta foi transformar a tabela única fornecida (`Financials`) em um modelo dimensional, separando os dados em tabelas de dimensão e fato para facilitar análises e melhorar a performance do modelo. As tabelas criadas foram:

### 🔒 Tabela de Backup:
- `Financials_origem` (oculta, usada como referência)

### ⭐ Tabelas Dimensão:

***- `D_Produtos`***
  - Contém: ID_Produto, Produto, Média de Unidades Vendidas, Média, Mediana, Valor Máximo e Mínimo de Vendas.
  
***- `D_Produtos_Detalhes`***  
  - Contém: ID_Produto, Discount Band, Sale Price, Units Sold, Manufacturing Price.
  
***- `D_Descontos`***  
  - Contém: ID_Produto, Discount, Discount Band.  
  - Inclui coluna condicional criada via DAX.
  
***- `D_Detalhes`*** 
  - Contém atributos adicionais que não foram contemplados nas outras dimensões (Segment, Country, etc).
  
***- `D_Calendário`***  
  - Criada com a função DAX `CALENDAR()` para suporte temporal.

### 📊 Tabela Fato:
***- `F_Vendas`*** 
  - Contém: SK_ID, ID_Produto, Produto, Units Sold, Sales Price, Discount Band, Segment, Country, Sales, Profit, Date.

---

## 🧠 Etapas da Construção

### 1. **D_Produtos**
- Criada por meio do **agrupamento** (Group By) da coluna `Product`.
- Utilizamos a opção **Avançado** para calcular: média de unidades vendidas, média/mediana/máximo/mínimo do valor de vendas.
- Geramos um **ID_Produto** para relacionamentos.

### 2. **D_Descontos**
- Duplicação da tabela `Financials`.
- Remoção de colunas não relacionadas a desconto.
- Criação de coluna condicional para classificar faixas de desconto.
- Remoção de duplicatas e criação de chave.

### 3. **D_Detalhes**
- Criada para armazenar `Segment` e `Country`.
- Colunas selecionadas da `Financials` e adição de coluna de índice para composições únicas.

### 4. **D_Produtos_Detalhes**
- Selecionadas as colunas: Product, Discount, Units Sold, Manufacturing Price, Sale Price.
- Criação de coluna `ID_Produto`.

### 5. **D_Calendário**
- Criada com DAX: Utilizando o **`CALENDAR`**.

### 6. **F_Vendas**
- Criada a partir da `Financials`.
- Incluída coluna de índice e `ID_Produto` para relacionamento com tabelas dimensão.

---

## 🛠️ Ferramentas e Funções Utilizadas

- **Power BI Desktop**
- **Power Query**: agrupamento, remoção de duplicatas, transformação de colunas.
- **DAX**: `CALENDAR`, criação de índices, colunas calculadas.
- **Modelagem Estrela (Star Schema)**: separação entre fatos e dimensões, chaves substitutas.

---

## 🖼️ Modelo Estrela (Star Schema)

> <img width="886" height="474" alt="image" src="https://github.com/user-attachments/assets/9742f4b4-39b2-4524-a96f-7a2b25a7b1e8" />


A imagem acima mostra a organização final do modelo dimensional criado, otimizando a análise dos dados de vendas com relacionamentos entre dimensões e fato.

---

## 📁 Estrutura do Repositório

📂 desafio-powerbi-modelagem
├── 📄 README.md
├── 📊 desafio_modelagem.pbix
├── 📸 modelo_star_schema.png

---

## Prints do processo:

***Tabela Produtos***


<img width="886" height="472" alt="image" src="https://github.com/user-attachments/assets/b65eecf9-35fb-44a2-88be-9d6e3d8a87e0" />

---

***Tabela Descontos***


<img width="886" height="472" alt="image" src="https://github.com/user-attachments/assets/9d4a55a1-a84b-42ac-929f-b398382fd1f3" />
<img width="886" height="472" alt="image" src="https://github.com/user-attachments/assets/23e44627-7578-4aab-9009-9d2350c03df6" />

---

***Tabela Categoria***


<img width="886" height="472" alt="image" src="https://github.com/user-attachments/assets/5521de68-c046-4068-86c3-f4c48881d7bb" />

---

***Tabela Produtos Detalhes***


<img width="886" height="472" alt="image" src="https://github.com/user-attachments/assets/8648af68-9ae0-43eb-96fd-e3936c3cf059" />
<img width="886" height="469" alt="image" src="https://github.com/user-attachments/assets/27fa3475-631c-414f-8121-84797d6170cc" />

---

***Tabela Fato Vendas***


<img width="1917" height="1025" alt="image" src="https://github.com/user-attachments/assets/0a7452a7-180f-415a-b165-5ce890e914bc" />

---
***Tabela Calendário***


<img width="1917" height="1032" alt="image" src="https://github.com/user-attachments/assets/8a89bd3e-5fa8-4d89-b232-5a9350da964b" />

---
***Tabela Detalhes***


<img width="1918" height="1024" alt="image" src="https://github.com/user-attachments/assets/dbe3d3f7-e1a0-4e63-98ea-ebf95f22ccd2" />


---
# 🙋‍♂️ Autor

**Raphael Travassos**  
Analista de Dados | Power BI | Python | SQL | Modelagem Dimensional  
[LinkedIn]([https://www.linkedin.com/in/seu-linkedin](https://www.linkedin.com/in/raphael-travassos-dos-santos/))  

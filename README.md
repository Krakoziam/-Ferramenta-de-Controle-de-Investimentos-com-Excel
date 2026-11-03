# ⛏️💰 Filho Investimentos - Simulador de Carteira de FIIs

Bem-vindo ao repositório do **Filho Investimentos**! Este projeto consiste em uma ferramenta em Excel desenvolvida para auxiliar investidores no planejamento financeiro e na alocação de ativos em Fundos de Investimento Imobiliário (FIIs), de acordo com seu perfil de risco e objetivos de longo prazo.

---

## 🎯 1. Perguntas que a Ferramenta Responde

A planilha foi estruturada para responder às principais dúvidas de quem está planejando sua independência financeira. Abaixo estão as perguntas e a localização exata de cada resposta/parâmetro na aba principal (`Planilha1`):

* **Quanto investir por mês?** 
  * Localização: Célula **`C17`** *(com o rótulo na `B17`)* — calculado automaticamente com base na renda mensal e no percentual disposto a investir.
* **Por quantos anos investir?** 
  * Localização: Célula **`C18`** *(com o rótulo na `B18`)* — entrada definida pelo usuário para o horizonte de tempo do investimento.
* **Qual a Taxa de Rendimento Mensal?** 
  * Localização: Célula **`C19`** *(com o rótulo na `B19`)* — estimativa de retorno mensal dos investimentos.
* **Qual será o Patrimônio Acumulado?** 
  * Localização: Célula **`C20`** *(com o rótulo na `B20`)* — resultado da projeção de juros compostos ao final do período estipulado.
* **Qual será o valor dos Dividendos Mensais?** 
  * Localização: Célula **`C21`** *(com o rótulo na `B21`)* — estimativa de renda passiva mensal gerada pelo patrimônio acumulado de acordo com o rendimento da carteira.

---

## 🧮 2. Como as Funções `VF` e `PROCV` Entram nos Cálculos

### Função `VF` (Valor Futuro)
A função `VF` é utilizada para calcular o **Patrimônio Acumulado** (`C20`) ao final do período de aportes, aplicando o efeito dos juros compostos sobre os investimentos mensais. 

* **Fórmula utilizada:**
  ```excel
  =VF(taxa_mensal; qtd_anos*12; aporte*-1)
  ```
* **Como funciona:** 
  * `taxa_mensal`: É a taxa de juros por período.
  * `qtd_anos*12`: Converte o período de anos para meses (número total de períodos de capitalização).
  * `aporte*-1`: O valor do aporte mensal é multiplicado por `-1` (valor invertido) para que o Excel retorne um resultado positivo no cálculo do Valor Futuro, já que, por padrão financeiro, saídas de caixa (aportes) são representadas negativamente.

### Função `PROCV` (Procura Vertical)
A função `PROCV` é utilizada na tabela de alocação (células `C36:C41`) para buscar dinamicamente o **Percentual Sugerido** para cada segmento de FII, cruzando o perfil de investidor selecionado com a tabela auxiliar localizada na `Planilha2`.

* **Fórmula utilizada:**
  ```excel
  =PROCV($C$32&"-"&B36; Planilha2!$A:$D; 4; FALSO)
  ```
* **Como funciona:**
  * `$C$32&"-"&B36`: Cria uma chave única de busca concatenando o **Perfil de Investidor** (ex: `Moderado`) com o **Segmento do FII** (ex: `PAPEL`), gerando o texto `"Moderado-PAPEL"`.
  * `Planilha2!$A:$D`: É a matriz onde os dados de referência estão armazenados.
  * `4`: Indica que o valor a ser retornado está na 4ª coluna da tabela auxiliar (a coluna onde constam as porcentagens).
  * `FALSO`: Garante que a busca traga apenas a correspondência exata da chave pesquisada.

---

## 🏷️ 3. Intervalos Nomeados Criados

Para tornar as fórmulas mais legíveis, organizadas e fáceis de manter, foram criados os seguintes intervalos nomeados na planilha:

| Nome do Intervalo | Referência / Descrição |
| :--- | :--- |
| **`salario`** | Renda mensal informada pelo usuário (`C12`). |
| **`sugestao_investimento`** | Percentual da renda que o usuário se dispõe a investir mensalmente (`C13`). |
| **`aporte`** | Valor financeiro a ser investido por mês (`C17`). |
| **`qtd_anos`** | Quantidade de anos que o dinheiro ficará rendendo com novos aportes (`C18`). |
| **`taxa_mensal`** | Taxa de rendimento mensal esperada durante a fase de acumulação (`C19`). |
| **`patrimonio`** | Montante total acumulado ao final do período projetado (`C20`). |
| **`rendimento_carteira`** | Percentual de *Dividend Yield* mensal médio esperado para a carteira de FIIs (`C33`). |

---

## 📊 4. Percentuais de Alocação por Perfil

Os percentuais de distribuição da carteira por segmento de FII seguem exatamente a metodologia e as recomendações apresentadas pelo **Expert durante a aula**. Eles estão estruturados na aba auxiliar (`Planilha2`) da seguinte forma:

| Segmento de FII | 🛡️ Conservador | ⚖️ Moderado | 🚀 Agressivo |
| :--- | :---: | :---: | :---: |
| **PAPEL** | 30% | 32% | 50% |
| **TIJOLO** | 50% | 35% | 10% |
| **HÍBRIDOS** | 10% | 8% | 5% |
| **FOFs** | 10% | 5% | 5% |
| **DESENVOLVIMENTO** | 0% | 10% | 20% |
| **HOTELARIAS** | 0% | 10% | 10% |
| **TOTAL** | **100%** | **100%** | **100%** |

---

## 🎨 5. O Que Foi Alterado em Relação à Ferramenta do Expert

Para dar uma identidade própria ao projeto, foram realizadas customizações visuais mantendo a integridade dos cálculos financeiros originais:

1. **Novo Nome e Banner Personalizado:** A marca da planilha foi alterada para **Filho Investimentos**, acompanhada de um novo banner exclusivo com a ilustração de um anão minerador (com picareta e bolsa de moedas de ouro) em fundo amarelo (`#FFC000`) e borda preta.
2. **Paleta de Cores:** A identidade visual das tabelas, cabeçalhos e células de destaque foi toda adaptada para tons quentes (amarelo, laranja pastel e detalhes em preto/branco), alinhando o design da planilha às cores do novo banner.

## 📷 6. Prints da Ferramenta

Moderado:

<img width="525" height="887" alt="image" src="https://github.com/user-attachments/assets/06840d2c-63a7-4b99-8d16-0122b64ffbed" />

Agressivo:

<img width="521" height="892" alt="image" src="https://github.com/user-attachments/assets/177fe363-00d3-4ede-bee5-953153466d92" />


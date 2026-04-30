# Leitor Fiscal 🧾

Sistema para leitura e análise de **NF-e / NFC-e (XML)** e **Cupons Fiscais (PDF)**, com dashboard por período e exportação para Excel e CSV.

Roda 100% no navegador — sem servidor, sem banco de dados.

---

## Como publicar (GitHub + Vercel)

### 1. Criar repositório no GitHub
1. Acesse [github.com/new](https://github.com/new)
2. Dê um nome ao repositório (ex: `leitor-fiscal`)
3. Deixe **público** e clique em **Create repository**

### 2. Subir os arquivos
Arraste os arquivos `index.html` e `vercel.json` para o repositório, ou use o botão **Add file → Upload files**.

### 3. Conectar ao Vercel
1. Acesse [vercel.com](https://vercel.com) e faça login com sua conta GitHub
2. Clique em **Add New Project**
3. Selecione o repositório `leitor-fiscal`
4. Clique em **Deploy** — não precisa mudar nenhuma configuração

Pronto! O Vercel vai gerar uma URL pública. A cada novo arquivo ZIP que você subir no GitHub, o Vercel atualiza automaticamente.

---

## Funcionalidades

- **Import XML**: NF-e (mod. 55) e NFC-e (mod. 65) — parsing completo no navegador
- **Import PDF**: Cupons fiscais — extração de texto automática
- **Duas datas**: data de emissão (`dhEmi`) e data de saída/entrada (`dhSaiEnt`) separadas em todos os relatórios
- **Dashboard**: total gasto, média por nota, gráficos por mês (emissão e saída), ranking de emissores
- **Filtros**: por período (emissão ou saída), tipo de documento, emissor/CNPJ
- **Exportação Excel** (.xlsx): 3 abas — Notas Fiscais, Itens, Por Emissor
- **Exportação CSV**: pronto para abrir no Excel (separador `;`, BOM UTF-8)
- **Detalhe**: painel lateral com todos os dados extraídos, itens, pagamentos e chave de acesso

---

## Dados extraídos do XML (NF-e)

| Campo | Descrição |
|-------|-----------|
| Emissor (CNPJ, nome, UF) | Quem emitiu |
| Destinatário (CNPJ/CPF, nome) | Quem recebeu |
| Número, série, chave de acesso | Identificação da nota |
| Natureza da operação | Tipo de operação (venda, transferência…) |
| Data de emissão (`dhEmi`) | Quando a nota foi gerada |
| Data de saída/entrada (`dhSaiEnt`) | Quando a mercadoria saiu ou entrou |
| Itens: descrição, NCM, CFOP, qtd, valor unitário | Produtos |
| Totais: produtos, desconto, frete, ICMS, PIS, COFINS | Valores fiscais |
| Formas de pagamento | Dinheiro, cartão, boleto… |

---

## Observação sobre PDFs

PDFs com texto selecionável funcionam bem. PDFs escaneados (imagem) precisam de OCR externo — nesse caso, a extração pode ser incompleta.

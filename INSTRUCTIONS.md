# 📖 SGV Turbo — Guia de uso

Este documento explica passo a passo como usar cada função da extensão **SGV Turbo**. Não é necessário nenhum conhecimento técnico — basta seguir as etapas na ordem indicada.

> **Pré-requisito:** a extensão já deve estar instalada no Chrome. Caso ainda não tenha instalado, siga as instruções no [README](./README.md) antes de continuar.

---

## Sumário

- [Como o painel aparece](#-como-o-painel-aparece)
- [Analisador de DV](#-analisador-de-dv)
  - [Analisar uma DV](#analisar-uma-dv)
  - [Grade da Transportadora](#aba-grade-da-transportadora)
- [Consultor de Assistências](#-consultor-de-assistências)
  - [Consultar assistências em lote](#consultar-assistências-em-lote)
  - [Alterar status em massa](#alterar-status-em-massa)
  - [Solicitar NF](#aba-solicitar-nf)
- [Lançador Financeiro](#-lançador-financeiro)

---

## 🖥️ Como o painel aparece

A extensão detecta automaticamente em qual página do SGV você está e exibe o módulo correto. Você não precisa fazer nada — basta abrir a página normalmente.

| Página do SGV | Módulo exibido |
|---|---|
| Devoluções (DVs) | Analisador de DV |
| Assistências Técnicas | Consultor de Assistências |
| Contas / Lançamentos | Lançador Financeiro |

O painel aparece como uma **barra lateral flutuante** no canto da tela. Se ele não estiver visível:

1. Clique no ícone 🔥 na barra do Chrome
2. Escolha o módulo que deseja abrir

---

## 📋 Analisador de DV

### Analisar uma DV

Este é o fluxo principal do módulo. Ao abrir qualquer formulário de DV no SGV, a extensão já começa a trabalhar automaticamente.

**Passo 1 — Abrir a DV**

Acesse a página de Devoluções no SGV e abra a DV que deseja analisar normalmente. O painel da extensão vai carregar junto com a página.

```
┌─────────────────────────────────┐
│  🔥 SGV Turbo — Analisador de DV│
│─────────────────────────────────│
│  Analisando DV...  ⏳           │
└─────────────────────────────────┘
```

**Passo 2 — Ler o resultado da análise**

Em segundos, o painel exibe o diagnóstico automático da DV:

```
┌─────────────────────────────────┐
│  ✅ APROVADA                    │
│─────────────────────────────────│
│  Motivo detectado:              │
│  Coleta pela transportadora     │
│                                 │
│  ⚠️ Valores conferidos: OK      │
│  ⚠️ Itens conferidos: OK        │
└─────────────────────────────────┘
```

Os possíveis resultados são:

| Resultado | Significado |
|---|---|
| ✅ Aprovada | A DV atende todos os critérios e pode ser aprovada |
| ⏳ Aguardar | Falta alguma informação ou condição para aprovar |
| ❌ Recusada | A DV não atende os critérios — deve ser recusada |

Junto com o resultado, a extensão exibe:
- O **motivo detectado automaticamente** (ex: "Barrado na Expedição", "Retornou ao CD")
- Se os **valores** entre a DV e o pedido original conferem
- Se os **itens** da DV batem com os itens do pedido

> Se o motivo detectado estiver errado, você pode alterá-lo manualmente no seletor exibido no painel.

**Passo 3 — Gerar a mensagem de aprovação**

Clique no botão **"Gerar mensagem"**. A extensão monta automaticamente o texto formatado com base na análise feita.

```
┌─────────────────────────────────┐
│  Mensagem gerada:               │
│  ─────────────────────────────  │
│  "Aprovado. Motivo: coleta      │
│   pela transportadora. Valor    │
│   conferido: R$ 120,00."        │
│                                 │
│  [ Copiar mensagem ]            │
└─────────────────────────────────┘
```

Clique em **"Copiar mensagem"** e cole no campo correspondente dentro do SGV.

**Passo 4 — Gravar no pedido**

Após colar a mensagem no campo do pedido dentro do SGV, clique em **Gravar** normalmente pelo sistema.

**Passo 5 — Gravar na DV**

Volte ao formulário da DV, cole a mensagem no campo de **Observações**, altere o dropdown de status para **Aprovada** e clique em **Gravar**.

---

### Tags visuais na lista de DVs

Antes mesmo de abrir uma DV, a extensão exibe **etiquetas coloridas** diretamente na lista de DVs do SGV, para facilitar a triagem:

```
┌──────┬───────────────────────────────────────────┬────────┐
│  DV  │  Cliente                                  │ Status │
├──────┼───────────────────────────────────────────┼────────┤
│ 1042 │  João Silva        [Barrado na Expedição]  │ Pend.  │
│ 1043 │  Maria Souza       [Cancelamento - Impr.]  │ Pend.  │
│ 1044 │  Carlos Pereira                            │ Pend.  │
└──────┴───────────────────────────────────────────┴────────┘
```

DVs com **2 ou mais dias em aberto** aparecem com a data destacada em vermelho, para priorização.

---

### Aba: Grade da Transportadora

Esta aba permite conferir automaticamente a planilha de retornos enviada pela transportadora, sem precisar consultar cada entrada manualmente.

**Passo 1 — Acessar a aba**

No painel do Analisador de DV, clique na aba **"Grade da Transportadora"**.

**Passo 2 — Fazer o upload da planilha**

Clique em **"Selecionar arquivo"** e escolha o arquivo `.xlsx` enviado pela transportadora. A extensão lê automaticamente as colunas de NF, CPF e Nome do cliente.

```
┌─────────────────────────────────┐
│  Grade da Transportadora        │
│─────────────────────────────────│
│  [ Selecionar arquivo .xlsx ]   │
│                                 │
│  Arquivo carregado:             │
│  retornos_abril.xlsx            │
│  32 entradas encontradas        │
│                                 │
│  [ Iniciar consulta ]           │
└─────────────────────────────────┘
```

**Passo 3 — Iniciar a consulta**

Clique em **"Iniciar consulta"**. A extensão consulta cada entrada no SGV automaticamente, uma por uma, exibindo o progresso em tempo real:

```
┌─────────────────────────────────┐
│  Consultando...  18/32          │
│  ████████████░░░░░░  56%        │
│                                 │
│  NF 00123 — Maria Silva         │
│  CPF 123.456.789-00             │
│  Resultado: ✅ COLETA           │
│                                 │
│  NF 00124 — João Pereira        │
│  CPF 987.654.321-00             │
│  Resultado: ❌ BARRADO          │
└─────────────────────────────────┘
```

**Passo 4 — Copiar os resultados**

Ao finalizar, clique em **"Copiar resultados"**. O conteúdo é copiado no formato tabular (NF, nome, resultado), pronto para colar diretamente em uma planilha do Excel.

---

## 🔍 Consultor de Assistências

### Consultar assistências em lote

Em vez de abrir cada assistência individualmente, este módulo permite buscar o status de várias de uma só vez.

**Passo 1 — Acessar a página de Assistências**

Navegue até a página de Assistências Técnicas no SGV. O painel do Consultor aparece automaticamente.

**Passo 2 — Colar os códigos**

No campo de texto do painel, cole os códigos das assistências que deseja consultar — um código por linha:

```
┌─────────────────────────────────┐
│  🔍 Consultor de Assistências   │
│─────────────────────────────────│
│  Cole os códigos abaixo:        │
│  ┌───────────────────────────┐  │
│  │ 10234                     │  │
│  │ 10235                     │  │
│  │ 10236                     │  │
│  │ 10237                     │  │
│  └───────────────────────────┘  │
│                                 │
│  [ Consultar ]                  │
└─────────────────────────────────┘
```

**Passo 3 — Iniciar a consulta**

Clique em **"Consultar"**. A extensão busca cada assistência automaticamente, sem travar a tela.

**Passo 4 — Ler os resultados**

Os resultados aparecem organizados em uma lista, com as seguintes informações para cada assistência:

```
┌────────────────────────────────────────────────────────────┐
│  ☐  10234 │ Em andamento │ Cod. 5021 - Notebook Dell       │
│            Último comentário: "Aguardando peça"            │
├────────────────────────────────────────────────────────────┤
│  ☐  10235 │ Concluída    │ Cod. 3847 - Monitor LG          │
│            Último comentário: "Produto enviado ao cliente"  │
├────────────────────────────────────────────────────────────┤
│  ☐  10236 │ Pendente     │ Cod. 2210 - Teclado Logitech    │
│            Último comentário: "Pedido à fábrica"           │
└────────────────────────────────────────────────────────────┘
```

Para copiar todos os resultados no formato código + status (para colar em planilha), clique em **"Copiar resultados"**.

---

### Alterar status em massa

Após consultar as assistências, você pode alterar o status de várias ao mesmo tempo.

**Passo 1 — Selecionar as assistências**

Marque o checkbox ao lado de cada assistência que deseja alterar. Para selecionar todas de uma vez, clique em **"Selecionar todas"**:

```
┌────────────────────────────────────────────────────────────┐
│  [✔] Selecionar todas                                      │
├────────────────────────────────────────────────────────────┤
│  ✔  10234 │ Em andamento │ Cod. 5021 - Notebook Dell       │
│  ✔  10235 │ Concluída    │ Cod. 3847 - Monitor LG          │
│  ✔  10236 │ Pendente     │ Cod. 2210 - Teclado Logitech    │
└────────────────────────────────────────────────────────────┘
```

**Passo 2 — Escolher o novo status**

No seletor abaixo da lista, escolha o status que deseja aplicar para todas as assistências selecionadas:

```
┌─────────────────────────────────┐
│  Novo status:                   │
│  [ Em andamento          ▼ ]    │
└─────────────────────────────────┘
```

**Passo 3 — Escolher um comentário**

Selecione um dos comentários pré-definidos na lista. Não é necessário digitar nada:

```
┌─────────────────────────────────┐
│  Comentário:                    │
│  ○ Aguardando peça              │
│  ● Produto enviado para fábrica │
│  ○ Pedido à fábrica e impresso  │
│  ○ Aguardando retorno da fábrica│
│  ○ ...                          │
└─────────────────────────────────┘
```

**Passo 4 — Aplicar**

Clique em **"Alterar selecionadas"**. A extensão aplica o novo status e o comentário em todas as assistências marcadas simultaneamente, via requisição direta ao sistema — sem recarregar a página:

```
┌─────────────────────────────────┐
│  Alterando...                   │
│                                 │
│  ✅ 10234 — Atualizado          │
│  ✅ 10235 — Atualizado          │
│  ✅ 10236 — Atualizado          │
│                                 │
│  3 de 3 concluídos              │
└─────────────────────────────────┘
```

Cada registro exibe individualmente se foi atualizado com sucesso ou se houve algum erro.

---

### Aba: Solicitar NF

Esta aba gera automaticamente uma mensagem padronizada para solicitar a nota fiscal de um produto de assistência.

**Passo 1 — Acessar a aba**

No painel do Consultor de Assistências, clique na aba **"Solicitar NF"**.

**Passo 2 — Selecionar a assistência**

A aba usa os dados da última assistência consultada. Confirme se o código e o produto exibidos estão corretos.

**Passo 3 — Copiar a mensagem**

Clique em **"Gerar mensagem"**. O texto é montado automaticamente com os dados da assistência e fica pronto para copiar e enviar.

```
┌─────────────────────────────────┐
│  Mensagem gerada:               │
│  ─────────────────────────────  │
│  "Solicitamos a NF referente    │
│   à assistência 10234,          │
│   produto: Notebook Dell        │
│   Cod. 5021."                   │
│                                 │
│  [ Copiar mensagem ]            │
└─────────────────────────────────┘
```

---

## 💰 Lançador Financeiro

Este módulo aparece automaticamente na página de lançamentos de contas do SGV e agiliza o cadastro de novos lançamentos financeiros.

**Passo 1 — Acessar a página de Contas**

Navegue até a página de Lançamentos / Contas no SGV. O painel do Lançador aparece automaticamente na lateral.

**Passo 2 — Preencher os dados do lançamento**

Preencha os campos no painel:

```
┌─────────────────────────────────┐
│  💰 Lançador Financeiro         │
│─────────────────────────────────│
│  Descrição:                     │
│  [ _________________________ ]  │
│                                 │
│  Valor:   [ ______________ ]    │
│  Data:    [ ______________ ]    │
│  Tipo:    [ Débito       ▼ ]    │
└─────────────────────────────────┘
```

**Passo 3 — Buscar o contato**

No campo **"Contato"**, digite o nome da pessoa ou empresa. A extensão consulta automaticamente a base de contatos do SGV e exibe os resultados:

```
┌─────────────────────────────────┐
│  Contato:                       │
│  [ Fornecedor X             ]   │
│  ─────────────────────────────  │
│  🔍 Fornecedor XYZ Ltda         │
│     Fornecedor XPTO ME          │
└─────────────────────────────────┘
```

Clique no contato correto para selecioná-lo.

**Passo 4 — Confirmar e gravar**

Com todos os campos preenchidos, clique em **"Gravar"**. A extensão confirma o lançamento diretamente no sistema.

```
┌─────────────────────────────────┐
│  ✅ Lançamento gravado!         │
└─────────────────────────────────┘
```

---

## ❓ Dúvidas frequentes

**O painel não apareceu na página.**
Clique no ícone 🔥 na barra do Chrome e selecione o módulo manualmente. Se o problema persistir, recarregue a página com `F5`.

**A análise da DV ficou com resultado errado.**
O motivo detectado pode ser alterado manualmente no seletor do painel antes de gerar a mensagem. A análise é uma sugestão — a decisão final é sempre do operador.

**A consulta de assistências travou no meio.**
Clique em **"Cancelar"** e tente novamente. Se o problema persistir, pode ser instabilidade na rede ou no sistema SGV.

**O resultado da Grade da Transportadora está vazio.**
Verifique se o arquivo `.xlsx` possui as colunas de NF, CPF e Nome do cliente no formato esperado. Arquivos com colunas faltando ou renomeadas podem não ser lidos corretamente.

---

> Dúvidas ou problemas não listados aqui? Fale com o responsável pela extensão.

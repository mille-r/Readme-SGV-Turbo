# 🔥 SGV Turbo

**SGV Turbo** é uma extensão para o navegador Google Chrome que acelera e automatiza tarefas repetitivas no sistema interno **SGV** (app.mamm.com.br/SGV) e no sistema de pedidos **Vercan**. Ela foi criada para quem trabalha diariamente com devoluções, assistências técnicas, lançamentos financeiros e controle de entregas — e cansou de fazer as mesmas ações manuais dezenas de vezes por dia.

> A extensão funciona como um painel lateral que aparece automaticamente nas páginas certas do SGV, sem precisar trocar de aba ou abrir outras janelas.

---

## 📦 O que a extensão faz

A SGV Turbo possui **cinco módulos principais**, cada um atuando em uma área diferente do sistema:

---

### 📋 1. Analisador de DV

Aparece automaticamente na página de consulta e nos formulários de Devoluções (DVs).

**O problema que resolve:** Analisar uma DV exige checar vários campos ao mesmo tempo — tipo da devolução, destino, motivo, valores, flag de retira — e decidir se ela pode ser aprovada ou não. Esse processo é manual, demorado e sujeito a erro.

**O que a extensão faz:**

- **Analisa a DV automaticamente** assim que você abre o formulário, lendo todos os campos relevantes e cruzando com uma tabela de regras interna. Em segundos, exibe se a DV deve ser ✅ **Aprovada**, ⏳ **Aguardar** ou ❌ **Recusada** — junto com as instruções do que fazer.
- **Confere valores** entre a DV e o pedido original (reembolso, crédito, abatimento e total), alertando quando há divergência.
- **Compara itens** da DV com os itens do pedido, mostrando se batem em quantidade e valor.
- **Detecta o motivo automaticamente** com base no texto das observações da DV (ex: "coleta pela transportadora", "barrado na expedição", "retornou ao CD"), mas permite que o operador altere manualmente se necessário.
- **Gera mensagem de aprovação** com um clique, já formatada para ser copiada e colada no sistema.
- **Exibe tags visuais na lista de DVs** (ex: "Barrado na Expedição", "Cancelamento - Imprimir controle") para facilitar a triagem antes mesmo de abrir o formulário.
- **Destaca em vermelho** datas de DVs com 2 ou mais dias em aberto, para priorizar o atendimento.

**Aba: Fila Automática** - FUNÇÃO EM TESTE ⚠️

Permite processar várias DVs de uma vez, sem precisar abrir uma por uma:

- Você inicia a fila e a extensão percorre cada DV pendente automaticamente, analisa, grava a aprovação no pedido e na DV, e passa para a próxima.
- DVs que precisam de atenção especial (ex: barrado na expedição sem papel em mãos, combinações não mapeadas) são pausadas e apresentadas ao operador para decisão manual.
- Tem **Modo Teste** que simula todo o processo sem gravar nada no sistema, ideal para validar antes de rodar de verdade.

**Aba: Grade da Transportadora**

Para conferir a planilha de retornos enviada pela transportadora:

- Você faz o upload do arquivo `.xlsx` da transportadora.
- A extensão lê automaticamente as colunas de NF, CPF e Nome do cliente.
- Consulta cada entrada no sistema SGV e classifica como **COLETA** ou **BARRADO**.
- Exibe o resultado linha a linha com barra de progresso, e permite copiar tudo para a área de transferência.

---

### 🔍 2. Consultor de Assistências

Aparece automaticamente na página de consulta de Assistências Técnicas.

**O problema que resolve:** Consultar ou atualizar o status de dezenas de assistências exige abrir cada uma manualmente. Com o módulo de assistências, isso vira um processo em lote.

**O que a extensão faz:**

- **Consulta em lote:** você cola vários códigos de assistência (um por linha) e a extensão busca o status de todos automaticamente, um por um, sem travar a tela.
- **Exibe os resultados** com código, status atual, código e nome do produto, e o último comentário registrado — tudo em um painel organizado.
- **Seleção e edição em massa:** após consultar, você seleciona as assistências que deseja alterar (ou usa "selecionar todas") e aplica um novo status para todas de uma vez.
- **Comentários pré-definidos:** ao alterar o status, você pode escolher um comentário já formatado em uma lista de opções — sem precisar digitar. Exemplos: "Aguardando peça", "Produto enviado para fábrica", "Pedido à fábrica e impresso para separação".
- **Copia resultados** para a área de transferência com um clique, no formato código + status, pronto para colar em planilhas ou relatórios.

**Aba: Solicitar NF**

Gera automaticamente uma mensagem padronizada para solicitar nota fiscal de um produto de assistência, já preenchida com os dados da assistência consultada.

**Aba: Gerar Relatório**

Para análise e acompanhamento de incidências de assistências técnicas:

- Com um clique, a extensão analisa **todas as assistências visíveis na página** — percorrendo automaticamente todas as páginas de resultados.
- Agrupa os dados por produto, contando o número de incidências de cada um e as peças mais solicitadas.
- **Gera um PDF profissional** com ranking de produtos por incidência, lista de peças por produto com número e descrição, período analisado e data de geração — pronto para ser enviado ao fabricante ou usado internamente.
- Ideal para identificar os produtos com mais problemas técnicos e embasar solicitações de peças ou melhorias junto aos fornecedores.

---

### 💰 3. Lançador Financeiro

Aparece automaticamente na página de lançamentos de contas.

**O problema que resolve:** Cadastrar um lançamento financeiro no SGV exige preencher vários campos em sequência, incluindo buscar o contato pelo nome. A extensão acelera esse processo.

**O que a extensão faz:**

- Oferece um painel lateral para preencher os dados do lançamento (descrição, valor, data, tipo).
- **Busca de contato por nome:** você digita o nome e a extensão consulta a base de contatos do sistema, exibindo os resultados para você selecionar — sem precisar navegar para outra página.
- Confirma e grava o lançamento com um clique.

---

### 🚚 4. Soma de Entregas

Aparece automaticamente na página de Entregas / Pedidos Disponíveis do SGV.

**O problema que resolve:** A página de pedidos disponíveis para entrega exibe uma lista de pedidos, mas não mostra o valor total do conjunto — o que exigiria abrir cada pedido manualmente e somar os valores.

**O que a extensão faz:**

- **Calcula automaticamente o valor total** de todos os pedidos listados na página assim que ela carrega, consultando cada pedido em paralelo para ser rápido.
- **Exibe o total diretamente na página**, logo acima da lista de resultados, no formato de moeda (R$).
- **Atualiza automaticamente** sempre que uma nova pesquisa é realizada ou a lista é modificada — sem precisar recarregar a página ou clicar em nada.

---

### 🏷️ 5. Etiquetas

Aparece automaticamente na página de etiquetas do sistema **Vercan** (opcaomoveis.verp.vercan.com.br).

**O problema que resolve:** Imprimir etiquetas de vários pedidos exige baixar e abrir o PDF de cada um individualmente. Com dezenas de pedidos, isso se torna um processo demorado e repetitivo.

**O que a extensão faz:**

- **Adiciona checkboxes** ao lado de cada pedido listado na página, permitindo selecionar quais etiquetas você quer baixar.
- **Baixa e une automaticamente** os PDFs de todas as etiquetas selecionadas, gerando um **único arquivo PDF** com todas as etiquetas em sequência.
- Exibe o progresso do download em tempo real (ex: "3/10 etiquetas...") e, ao finalizar, faz o download automático do arquivo unificado.
- Elimina a necessidade de abrir e imprimir cada etiqueta separadamente — basta selecionar, clicar e imprimir o PDF consolidado.

---

## 🚀 Por que usar o SGV Turbo?

| Sem a extensão | Com o SGV Turbo |
|---|---|
| Abrir cada DV, checar campos manualmente, decidir se aprova | Decisão automática em segundos com base nas regras definidas |
| Copiar e colar mensagem de aprovação manualmente | Mensagem gerada e copiada com um clique |
| Processar e conferir manualmente valores e parâmetros da DV | Análise automática ao abrir a DV, conferindo todas as informações necessárias |
| Conferir planilha da transportadora à mão | Upload do .xlsx e resultado automático por entrada |
| Consultar assistências uma a uma | Consulta em lote, resultado de todas de uma vez |
| Alterar status de assistência manualmente em cada registro | Seleção múltipla e alteração em lote com um clique |
| Montar relatório de assistências manualmente | PDF gerado automaticamente com ranking de incidências por produto |
| Somar valores dos pedidos de entrega manualmente | Total calculado e exibido automaticamente na própria página |
| Baixar e imprimir etiquetas uma a uma | Seleção em lote e download de um único PDF com todas as etiquetas |

---

## ⏱️ Relatório de desempenho — tempo economizado

Os dados abaixo comparam o tempo médio gasto para executar 20 unidades de cada tarefa **manualmente no SGV** versus utilizando o **SGV Turbo**. Os valores foram calculados com base em tempos médios de carregamento de página, velocidade de digitação (~60 WPM) e interações típicas de mouse/cursor em rede de velocidade média.

> Além da economia de tempo, a automação elimina erros de digitação, esquecimento de campos e inconsistências entre registros — reduzindo a taxa de erros a zero nas operações executadas pela extensão.

---

### 📋 Analisador de DV — sem controle de retira (20 DVs)

| Etapa manual | Tempo est. |
|---|---|
| Abrir a DV | ~6s |
| Analisar campos de informação | ~20s |
| Analisar campos de valores | ~15s |
| Abrir informações do pedido | ~5s |
| Analisar valores do pedido | ~15s |
| Escrever mensagem (campo principal) | ~20s |
| Gravar | ~4s |
| Escrever observação na DV | ~18s |
| Alterar dropdown para Aprovada + Gravar | ~9s |
| **Total por DV** | **~112s (~1min 52s)** |

| | Manual | SGV Turbo | Economia |
|---|---|---|---|
| Tempo total (20 DVs) | ~37min 20s | ~3min | **~34min (~92%)** |

---

### 📋 Analisador de DV — com controle de retira (20 DVs)

Inclui todas as etapas acima, mais:

| Etapa extra — controle de retira | Tempo est. |
|---|---|
| Abrir aba controle de retira | ~4s |
| Clicar em Localizar | ~3s |
| Selecionar a DV na lista | ~5s |
| Selecionar data (datepicker) | ~6s |
| Setar entregador | ~4s |
| Gravar | ~4s |
| Imprimir | ~4s |
| **Subtotal retira por DV** | **~30s** |
| **Total por DV com retira** | **~142s (~2min 22s)** |

| | Manual | SGV Turbo | Economia |
|---|---|---|---|
| Tempo total (20 DVs com retira) | ~47min 20s | ~5min | **~42min (~89%)** |

---

### 🔍 Consultor de Assistências — alteração de status + comentário (20 assistências)

| Etapa manual | Tempo est. |
|---|---|
| Navegar até a assistência | ~8s |
| Abrir o registro | ~4s |
| Localizar e alterar o status | ~8s |
| Localizar campo de comentário e digitar | ~18s |
| Salvar e voltar à lista | ~9s |
| **Total por assistência** | **~47s** |

| | Manual | SGV Turbo | Economia |
|---|---|---|---|
| Tempo total (20 assistências) | ~15min 40s | ~49s | **~14min 51s (~94%)** |

---

### 📊 Comparativo geral — 20 unidades de cada tarefa (60 ações no total)

| Tarefa | Manual | SGV Turbo |
|---|---|---|
| DV sem retira (×20) | ~37min 20s | ~3min |
| DV com retira (×20) | ~47min 20s | ~5min |
| Assistências (×20) | ~15min 40s | ~49s |
| **Total** | **~1h 40min** | **~8min 49s** |

> **Economia total: ~1h 31min — aproximadamente 91% menos tempo** para executar o mesmo volume de trabalho.

---

## 🛠️ Como instalar

A extensão é instalada manualmente no Chrome em modo desenvolvedor. Siga os passos:

1. Baixe o arquivo `.zip` da extensão e **extraia a pasta** em um local fixo no seu computador (não mova nem apague a pasta depois).
2. Abra o Google Chrome e acesse: `chrome://extensions`
3. Ative o **"Modo do desenvolvedor"** (chave no canto superior direito).
4. Clique em **"Carregar sem compactação"** e selecione a pasta extraída.
5. A extensão aparecerá na lista e o ícone 🔥 aparecerá na barra do Chrome.

> **Importante:** a pasta da extensão precisa permanecer no lugar onde foi extraída. Se você mover ou apagar a pasta, a extensão para de funcionar e precisa ser instalada novamente.

---

## 💡 Como usar

Não é necessário configurar nada. A extensão detecta automaticamente em qual página você está e exibe o painel correto:

- Na página de **Devoluções** → aparece o Analisador de DV
- Na página de **Assistências** → aparece o Consultor de Assistências
- Na página de **Contas** → aparece o Lançador Financeiro
- Na página de **Entregas / Pedidos Disponíveis** → aparece a Soma de Entregas automaticamente
- Na página de **Etiquetas do Vercan** → aparece o módulo de Etiquetas

Se o painel não estiver visível, clique no ícone 🔥 da extensão na barra do Chrome e escolha o módulo desejado.

Cada módulo e cada aba dentro dos módulos pode ser ativado ou desativado individualmente nas **configurações da extensão** — clique em ⚙️ Configurar funcionalidades no popup do ícone 🔥 para gerenciar quais painéis e abas você quer que apareçam.

---

## ⚠️ Observações

- Os módulos do SGV funcionam **somente** nas páginas do SGV (`app.mamm.com.br/SGV`). O módulo de Etiquetas funciona somente no Vercan (`opcaomoveis.verp.vercan.com.br`). A extensão não acessa nenhum outro site.
- Nenhum dado é enviado para servidores externos. Tudo acontece diretamente entre o seu navegador e os sistemas SGV e Vercan.
- Requer Google Chrome. Não é compatível com outros navegadores.

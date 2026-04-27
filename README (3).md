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

**Aba: NF DV**

Para localizar rapidamente a nota fiscal de compra de um produto envolvido em uma DV:

- Você informa o código do produto.
- A extensão consulta o histórico de compras do sistema, encontra a NF mais recente e exibe o número junto com os dados do produto (descrição, código do fabricante, fornecedor).
- Se o produto não for encontrado no período padrão, oferece a opção de buscar em um período maior.
- O número da NF pode ser copiado com um clique.

**Aba: Solicitar Troca**

Para agilizar o processo de solicitação de troca junto ao fabricante a partir de um chamado de assistência técnica:

- Você informa o número do **Chamado** (aberto no sistema `news.mamm.com.br`).
- A extensão acessa o chamado automaticamente, extrai o **PV** vinculado, identifica o **produto reclamado** e o **defeito** descritos no chamado, e busca o **nome do cliente** e a **data de compra** no SGV.
- Preenche automaticamente o campo do fabricante e o e-mail de destino com base na lista de fabricantes cadastrada.
- Ao clicar em **Copiar & Abrir Gmail**: copia o corpo do e-mail já formatado em HTML, abre o Gmail com assunto e destinatário preenchidos, **baixa automaticamente todos os arquivos de mídia do chamado** (fotos, vídeos, documentos) com nome no formato `PV(X) - CH(X)`, e **gera e baixa o PDF do pedido de venda** automaticamente.

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

Gera automaticamente uma mensagem padronizada para solicitar nota fiscal de transporte de um produto de assistência técnica, já preenchida com os dados da assistência consultada (número, PV, produto, peças, dimensões, peso e transportadora).

**Aba: Gerar Relatório**

Para análise e acompanhamento de incidências de assistências técnicas:

- Com um clique, a extensão analisa **todas as assistências visíveis na página** — percorrendo automaticamente todas as páginas de resultados.
- Agrupa os dados por produto, contando o número de incidências de cada um e as peças mais solicitadas.
- **Gera um PDF profissional** com ranking de produtos por incidência, lista de peças por produto com número e descrição, período analisado e data de geração — pronto para ser enviado ao fabricante ou usado internamente.
- Ideal para identificar os produtos com mais problemas técnicos e embasar solicitações de peças ou melhorias junto aos fornecedores.

**Geração de e-mails integrada à consulta**

Após consultar as assistências em lote, o botão **📧 Gerar E-mails Selecionadas** aparece diretamente na aba de Consulta, sem precisar trocar de aba:

- A extensão busca automaticamente os dados de cada assistência selecionada (produto, chamado, fabricante) e gera um **card individual** para cada uma.
- Cruza o fabricante com a **lista de fabricantes** e preenche o destinatário e CC automaticamente. Os campos ficam editáveis antes do envio.
- Ao clicar em **Copiar & Abrir Gmail**, copia o e-mail formatado em HTML, abre o Gmail com assunto e destinatário preenchidos e **baixa automaticamente os arquivos anexados ao chamado** (fotos, documentos) do sistema `news.mamm.com.br`.
- A mesma lista de fabricantes é utilizada pela aba **Solicitar Troca** do Analisador de DV, garantindo consistência entre os dois módulos.

**Lista de Fabricantes**

Acessível pelo botão **🏭 Lista de Fabricantes** no popup do ícone 🔥, disponível a qualquer momento independentemente da página aberta:

- Exibe todos os fabricantes cadastrados com nome, e-mail e CC.
- Possui campo de busca para localizar rapidamente um fabricante pelo nome.
- A lista é **sincronizada automaticamente com um banco de dados** alimentado e mantido pela equipe de assistência técnica — sempre que um novo fabricante é cadastrado ou um e-mail é atualizado, a extensão reflete a mudança em tempo real.
- O botão **🔄 Atualizar lista** força uma nova sincronização manualmente quando necessário.

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
| Buscar NF de compra de um produto navegando no sistema fiscal | Código do produto → número da NF em segundos |
| Abrir chamado, buscar PV, escrever e-mail de solicitação de troca, buscar e-mail do fabricante, baixar anexos, gerar PDF do pedido | Número do chamado → e-mail pronto, anexos e PDF gerados automaticamente |
| Consultar assistências uma a uma | Consulta em lote, resultado de todas de uma vez |
| Alterar status de assistência manualmente em cada registro | Seleção múltipla e alteração em lote com um clique |
| Montar relatório de assistências manualmente | PDF gerado automaticamente com ranking de incidências por produto |
| Abrir chamado no news.mamm.com.br para baixar cada anexo individualmente | Anexos baixados automaticamente ao gerar o e-mail de assistência |
| Buscar e-mail do fabricante em planilha ou agenda | Lista de fabricantes sempre atualizada no popup, sincronizada com o banco de dados da assistência técnica |
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

### 🔎 NF DV — busca de nota fiscal de compra (20 produtos)

| Etapa manual | Tempo est. |
|---|---|
| Navegar até o sistema de compras/fiscal | ~10s |
| Pesquisar pelo produto | ~15s |
| Filtrar e localizar a NF no período correto | ~60s |
| Anotar/copiar o número da NF | ~5s |
| **Total por produto** | **~90s (~1min 30s)** |

| | Manual | SGV Turbo | Economia |
|---|---|---|---|
| Tempo total (20 produtos) | ~30min | ~1min 20s | **~28min 40s (~96%)** |

---

### 🔁 Solicitar Troca — e-mail de troca ao fabricante (20 chamados)

| Etapa manual | Tempo est. |
|---|---|
| Abrir chamado e identificar o PV | ~15s |
| Buscar o PV no SGV para pegar dados do cliente e data | ~20s |
| Identificar produto e defeito no chamado | ~25s |
| Buscar e-mail do fabricante | ~20s |
| Escrever e-mail formatado | ~90s |
| Baixar anexos do chamado um a um | ~40s |
| Gerar/salvar PDF do pedido | ~30s |
| **Total por chamado** | **~240s (~4min)** |

| | Manual | SGV Turbo | Economia |
|---|---|---|---|
| Tempo total (20 chamados) | ~80min | ~4min | **~76min (~95%)** |

---

### 📊 Comparativo geral — 20 unidades de cada tarefa (100 ações no total)

| Tarefa | Manual | SGV Turbo |
|---|---|---|
| DV sem retira (×20) | ~37min 20s | ~3min |
| DV com retira (×20) | ~47min 20s | ~5min |
| Assistências (×20) | ~15min 40s | ~49s |
| NF DV (×20) | ~30min | ~1min 20s |
| Solicitar Troca (×20) | ~80min | ~4min |
| **Total** | **~3h 30min** | **~14min** |

> **Economia total: ~3h 16min — aproximadamente 93% menos tempo** para executar o mesmo volume de trabalho.

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

- Os módulos do SGV funcionam **somente** nas páginas do SGV (`app.mamm.com.br/SGV`). O módulo de Etiquetas funciona somente no Vercan (`opcaomoveis.verp.vercan.com.br`). A extensão não acessa nenhum outro site além do `news.mamm.com.br` para buscar dados de chamados de assistência.
- Nenhum dado é enviado para servidores externos. Tudo acontece diretamente entre o seu navegador e os sistemas SGV, Vercan e News.
- Requer Google Chrome. Não é compatível com outros navegadores.
- Para as funcionalidades que acessam chamados no `news.mamm.com.br` (aba Solicitar Troca e download de anexos do Consultor de Assistências), é necessário estar logado nesse sistema no navegador.

🛠️ Como foi construído — Tecnologias e conceitos utilizados

🧱 Extensão do Chrome
O SGV Turbo é uma Chrome Extension — um pacote de arquivos que o próprio Chrome instala e executa. A estrutura é baseada em três tipos de script:
Content Scripts — arquivos JavaScript injetados automaticamente pelo Chrome nas páginas do SGV e do Vercan. É o coração da extensão: eles leem o conteúdo da página (campos, tabelas, formulários), criam o painel lateral visualmente e executam as automações. Cada módulo tem seu próprio content script (content.js, assistencia_content.js, financeiro_content.js, entregas_content.js).
Background Script — script que roda em segundo plano, fora de qualquer página. É usado para tarefas que o content script não pode fazer diretamente: buscar arquivos de outros domínios (como os anexos do news.mamm.com.br), gerar PDFs via Chrome Debugger API, e sincronizar a lista de fabricantes com o banco de dados externo.
Manifest (manifest.json) — arquivo de configuração da extensão. Define quais páginas cada script monitora, quais permissões o Chrome deve conceder (acesso a abas, downloads, debugger etc.) e quais arquivos compõem a extensão.

🖥️ Injeção de interface no sistema
O painel lateral do SGV Turbo não é parte do sistema SGV — ele é criado e injetado dinamicamente pelo content script usando DOM Manipulation: criação de elementos HTML (div, button, input, select) via JavaScript puro, estilizados com CSS próprio injetado na página. É como "colar" uma janela nova dentro de um site que não foi feito para isso.
MutationObserver é a técnica usada para detectar mudanças na página sem ficar verificando repetidamente. Em vez de checar a cada segundo se um popup do SGV foi aberto, o MutationObserver observa a árvore do DOM e dispara uma função somente quando algo muda — muito mais eficiente para o navegador.

🤖 Automação de formulários
Para aprovar DVs, alterar status de assistências e preencher lançamentos financeiros, a extensão usa DOM Interaction — simula as mesmas ações que um usuário faria manualmente: localiza campos pelos seus seletores CSS ou IDs, preenche valores, dispara eventos de teclado (change, click, keydown) e aguarda o sistema processar antes de continuar.
Como o SGV é um sistema legado em ASP.NET com postbacks (a página recarrega parcialmente a cada ação), a extensão usa setTimeout e verificação de estado para esperar o resultado antes de prosseguir para o próximo passo — sem travar o navegador.

📡 Comunicação entre scripts
Content scripts e background script não se comunicam diretamente — eles usam a Chrome Extensions Messaging API: chrome.runtime.sendMessage envia uma mensagem e chrome.runtime.onMessage a recebe. Isso é necessário porque cada script roda em um contexto isolado do Chrome. Por exemplo: quando a aba Solicitar Troca precisa baixar um anexo do news.mamm.com.br, o content script envia uma mensagem ao background, que faz o download e devolve o arquivo em base64.

🗄️ Armazenamento de dados
chrome.storage.sync — armazena as preferências do usuário (quais módulos estão ativos, configurações das abas) na conta Google do Chrome, sincronizando entre computadores automaticamente.
chrome.storage.local — armazena dados maiores localmente, como a lista de fabricantes baixada do banco de dados, com timestamp do último sync.
localStorage — usado pontualmente para guardar dados de sessão entre navegações de página (como a lista de DVs em processamento na Fila Automática).

☁️ Banco de dados externo
A lista de fabricantes é sincronizada com o Supabase via Edge Function — uma função que roda nos servidores do Supabase e devolve a lista atualizada em JSON. O background script faz essa requisição ao iniciar o Chrome e sempre que o usuário clica em "Atualizar lista". Se a sincronização falhar, a extensão usa a lista em cache salva localmente.

📄 Geração de PDF
Para gerar o PDF do pedido de venda na aba Solicitar Troca, a extensão usa a Chrome Debugger API — uma API avançada do Chrome que permite controlar uma aba como se fosse um desenvolvedor usando o DevTools. A extensão abre a página do pedido em segundo plano, ativa o debugger, aciona o comando de impressão em PDF e captura o arquivo resultante, tudo sem que o usuário precise interagir com nada.

📊 Leitura de planilhas
SheetJS (xlsx) é a biblioteca usada para ler os arquivos .xlsx da Grade da Transportadora diretamente no navegador. O arquivo é carregado via FileReader, convertido para um objeto JavaScript e percorrido linha a linha para extrair NF, CPF e nome do cliente — sem precisar de nenhum servidor.

🔗 Requisições HTTP dentro da extensão
Para consultar dados no SGV (status de assistências, valores de pedidos, dados de DVs), a extensão usa fetch diretamente nas páginas do SGV — já que o content script roda no mesmo contexto do site, ele tem as mesmas permissões de sessão que o usuário logado, sem precisar de autenticação separada. Para acessar outros domínios (como news.mamm.com.br), o background script faz as requisições, contornando as restrições de CORS que impediriam o content script de fazê-las diretamente.

Idealizado e desenvolvido por Rodrigo Miller

# Changelog: COPAIBA TOUCH @ Alpha - Atualizações Recentes

## Visão Geral
As presentes atualizações focam em estabelecer suporte nativo e uma interface acessível para dispositivos móveis (smartphones e tablets), além do fechamento de lacunas sistêmicas que causavam a desincronização de respostas do usuário em navegadores estritos. Foram introduzidas melhorias de experiência de usuário (UX) focadas em produtividade, incluindo histórico completo de edição e predefinições fonéticas fixas.

---

## 1. Melhorias de Responsividade para Mobile
* **Refatoração do Cabeçalho**: O layout do cabeçalho superior foi otimizado, adotando adaptações elásticas e redimensionamento progressivo (flexão modular e quebra de fluxo via horizontal-scroll) que impedem que a interface deforme ou saia do escopo de visão do usuário em telas reduzidas.
* **Tabela de Parâmetros Adaptativa**: A planilha que sumariza a edição de `oto.ini` não se contrai mais em resoluções com largura severamente restrita. Inseriu-se um sistema contido de rolagem horizontal nativo em sua raiz (`overflow-x`), mantendo as informações e os coliformes tabulares intactos.
* **Calibragem das Áreas de Toque**: A largura base para a captação do contato digital (touch target) dos marcadores interativos do gráfico (Waveform) foi devidamente triplicada apenas na media query referente aos aspectos orientados ao design de toque. Isso provê aos usuários uma seleção menos frágil para manipulação e calibração de `overlap`, `offset`, `cutoff`, etc.

## 2. Correções de Manutenção e Interação (Bug Fixes)
* **Retenção dos Ajustes no Waveform**: Corrigida a anomalia em que a barra modificadora, ao ser rebaixada ou estendida no elemento do gráfico de ondas, era revertida visualmente à sua posição matriz no momento em que se cessava o cursor. A ação foi sincronizada atrelando o redesenho primário em bloco de forma obrigatória no encerramento (drop state) do elemento e forçando a sincronização do DOM atrelada aos dados temporários de sessão.
* **Transição Lógica de Eventos Direcionais**: Em adição à correção de retenção visual, toda a lógica computacional do `Canvas` e dos `Drag Handles` que sustentavam seu alicerce em eventos ultrapassados focados exclusivamente em ponteiros ópticos de Mouse, foi inteiramente substituída pela modernidade do `Pointer Events API`. Essa transição permite identificação irrefutável e captura responsiva de canetas Stylus, toques digitais fluidos de smartphone e interações de mouse de modo uníssono, prevenindo interações falhas ("bugs de clique vazio").
* **Bloqueio de Segurança de Importação pelo Navegador Móvel**: Detectado e contornado o filtro hostil imposto pelos navegadores iOS (Safari) e Android WebViews (Chrome) contra instigações em elementos de carregamento de pastas e arquivos originárias de scripts dinâmicos, sempre que estes dependiam da ocultação total orientada pela classe de estilo `display: none` ou afins. O contorno técnico adotou classe nativa de isolamento invisível (Screen Reader Only - SR-Only), impedindo o bloqueio programático ao se carregar o conteúdo do usuário na página pelo Mobile.

## 3. Integrações Inéditas e Ferramentas (Novos Recursos)
* **Rodapé Operacional Mobile (Footer Toolbar)**: Quando lida por ecrã portável móvel, a interface agora instanciará uma barra funcional contida e em repouso permanente no limite inferior do campo de visão, a fim de fornecer acessos diretos. Os componentes inseridos incluem:
  * Controles sequenciais de navegação (Anterior / Próximo).
  * Acionamento da reprodução de áudio isolada de blocos (Tocar).
  * Função rápida de renomeação visual direta (Renomear).
  * Funções de restabelecimento (Desfazer / Refazer).
* **Módulo de Histórico Completo de Ações (Undo e Redo)**: O sistema de pilhas que estava contido apenas de forma preparatória nos construtores da classe agora foi preenchido. Instanciou-se um gerenciador de memória baseado em rastreamento integral (Row-CLone Mapping), com retenção configurável de 30 memórias recursivas de desfazer. Cada reposição retroage ou realoca exatamente o comportamento e a seleção integral modificada nas tabelas, sendo disparada de forma proativa antes de apagamentos, duplicações de valores arrastados ou aplicação em subconjunto e lote. 
* **Botões Dedicados de Presets Fonéticos (Macro)**: Inseridos abaixo da seção de Painéis de Parâmetros Rápidos. Servem para injeção automática e sequencial de configurações comumente requisitadas a vozes síntese. As macros instanciadas são:
  * **CV**: `Overlap: 25`, `Preutter: 50`, `Consonant: 100`, `Cutoff: -170`
  * **VC**: `Overlap: 65`, `Preutter: 100`, `Consonant: 125`, `Cutoff: -140`
  * **VCV**: `Overlap: 120`, `Preutter: 300`, `Consonant: 350`, `Cutoff: -400`
  * **VV**: `Overlap: 80`, `Preutter: 65`, `Consonant: 100`, `Cutoff: -120`

## 4. Renovação Visual e Identidade (Visual Overhaul)
* **Mudança de Nome**: O projeto foi oficialmente renomeado de "Copaiba Web" para **COPAIBA TOUCH**, refletindo seu novo foco em portabilidade e interações táteis.
* **Paleta de Alto Contraste (Slate & Sky)**: Implementação de um sistema de cores profissional baseado nos tons Slate (ardósia) e Sky (céu). O objetivo foi garantir legibilidade absoluta em ambientes de alta ou baixa luminosidade.
* **Otimização da Waveform**:
  * No **Modo Escuro**, a waveform agora possui tom `Sky 400` vibrante sobre fundo Slate profundo, garantindo visibilidade neon.
  * No **Modo Claro**, a waveform adota o tom `Slate 800` sólido para máximo contraste contra o fundo claro.
  * A espessura da linha de renderização foi aumentada em 50% para facilitar a visualização de picos de transientes durante a edição rápida.
* **Refinamento de Componentes (Premium UI)**: Todos os botões, cards e inputs foram redesenhados com bordas suaves, tipografia Inter (sans-serif moderna) e efeitos de transição (hover) mais polidos, conferindo um aspecto de aplicação "State of the Art".


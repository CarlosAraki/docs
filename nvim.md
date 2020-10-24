insert i
/ find
u undo
<C r> antiundo
dd deleteline
dw delete word
de delete to word end
p put character deleted
a append
number G go to line 

Check out one of my other projects 👉 weekend.dev!

Vim Cheat Sheet
Global
	:h[elp] palavra chave - abrir a página de ajuda para um termo
	:sav[eas] arquivo - salvar um arquivo como
	:clo[se] - fechar o painel atual
	:ter[minal] - open a terminal window
	K - abrir a página do manual para a palavra abaixo do cursor
Tip Run vimtutor in a terminal to learn the first Vim commands.
Movimento do cursor
	h - mover o cursor para esquerda
	j - mover o cursor para baixo
	k - mover o cursor para cima
	l - mover o cursor para direita
	H - mover para o cursor para a parte superior da tela
	M - mover para o cursor para o meio da tela
	L - mover para o cursor para a parte inferior da tela
	w - pular adiante em direção ao inicio de uma palavra
	W - pular adiante em direção ao inicio de uma palavra (podendo conter pontuação)
	e - pular adiante em direção ao fim de uma palavra
	E - pular adiante para o fim de uma palavra (podendo conter pontuação)
	b - pular para trás para o início de uma palavra
	B - pular para trás para o início de uma palavra (podendo conter pontuação)
	% - mover para a ocorrência de um dos caracteres compatíveis (pares padrões: '()', '{}', '[]' - execute :h matchpairs no vim para mais informações)
	0 - pular para o início da linha
	^ - pular para o primeiro caractere (sem ser espaço) da linha
	$ - pular para o fim da linha
	g_ - pular para o último character não vazio da linha
	gg - ir para a primeira linha do documento
	G - ir para a última linha do documento
	5gg or 5G - ir para a linha 5
	fx - pular para a próxima ocorrencia do caractere x
	tx - pular para antes da próxima ocorrencia do caractere x
	Fx - pular para a ocorrencia anterior do caractere x
	Tx - pular para depois da ocorrência do caractere x
	; - repetir o último movimento de f, t, F ou T
	, - repetir o último movimento de f, t, F ou T de forma invesa
	} - pular para o próximo parágrafo (ou função/bloco, quando estiver editando código)
	{ - pular para o parágrafo anterior (ou função/bloco, quando estiver editando código)
	zz - centralizar o cursor na tela
	Ctrl + e - move screen down one line (without moving cursor)
	Ctrl + y - move screen up one line (without moving cursor)
	Ctrl + b - mover o cursor uma tela cheia para tras
	Ctrl + f - mover o cursor uma tela cheia para frente
	Ctrl + d - mover o cursor uma tela e meia para frente
	Ctrl + u - mover o cursor uma tela e meia para tras
	Tip Adicione um prefixo a um comando de movimento com um número para repetir o mesmo. Exemplo: 4j irá mover 4 linhas para baixo.
Modo de inserção - inserir/acrescentar texto
	i - inserir antes do cursor
	I - inserir no começo da linha
	a - inserir depois do cursor
	A - inserir no final da linha
	o - inserir uma nova linha em baixo da linha atual
	O - inserir uma nova linha em cima da linha atual
	ea - inserir no final da palavra
	Ctrl + h - delete the character before the cursor during insert mode
	Ctrl + w - delete word before the cursor during insert mode
	Ctrl + j - begin new line during insert mode
	Ctrl + t - indent (move right) line one shiftwidth during insert mode
	Ctrl + d - de-indent (move left) line one shiftwidth during insert mode
	Ctrl + n - insert (auto-complete) next match before the cursor during insert mode
	Ctrl + p - insert (auto-complete) previous match before the cursor during insert mode
	Ctrl + rx - insert the contents of register x
	Esc - sair do modo de inserção
Editando
	r - substituir um único caractere
	J - juntar a linha que está em baixo da linha atual
	gJ - join line below to the current one without space in between
	gwip - reflow paragraph
	g~ - switch case up to motion
	gu - change to lowercase up to motion
	gU - change to uppercase up to motion
	cc - substituir a linha toda
	C - change (replace) to the end of the line
	c$ - substituir no final da linha
	ciw - change (replace) entire word
	cw - substituir no final da palavra
	s - deletar um caractere e substituir texto
	S - deletar linha e substituir texto (igual o comando cc)
	xp - transpor duas letras (deletar e colar)
	u - desfazer
	U - restaura linha inteira
	Ctrl + r - refazer
	. - repetir o último comando
	Marcação de texto (modo visual)
	v - iniciar modo visual, marcar linhas e fazer um comando (como y-yank)
	V - iniciar modo visual marcando a linha toda
	o - mover para o fim/inicio da marcação
	Ctrl + v - iniciar modo de bloco visual
	O - mover para o fim/inicio do bloco
	aw - marcar uma palavra
	ab - um bloco com ()
	aB - um bloco com {}
	at - a block with <> tags
	ib - um bloco interno com ()
	iB - um bloco interno com {}
	it - inner block with <> tags
	Esc - sair do modo visual
	Tip Instead of b or B one can also use ( or { respectively.
Comandos visuais
	> - deslocar texto para direita
	< - deslocar texto para esquerda
	y - copiar texto marcado
	d - deletar texto marcado
	~ - alterar entre maiúscula e minúscula
	u - change marked text to lowercase
	U - change marked text to uppercase
Registradores
	:reg[isters] - mostrar conteúdo dos registradores
	"xy - colar no registrador x
	"xp - colar o conteúdo do registrador x
	"+y - yank into the system clipboard register
	"+p - paste from the system clipboard register
	Tip Registradores são guardados em ~/.viminfo, e são carregados no início do vim.
	Tip Special registers:
		 0 - last yank
		 " - unnamed register, last delete or yank
		 % - current file name
		 # - alternate file name
		 * - clipboard contents (X11 primary)
		 + - clipboard contents (X11 clipboard)
		 / - last search pattern
		 : - last command-line
		 . - last inserted text
		 - - last small (less than a line) delete
		 = - expression register
		 _ - black hole register
Marcadores
	:marks - listar todos os marcadores
	ma - atribuir a posição atual no marcador A
	`a - pular para a posição do marcador A
	y`a - copiar texto para a posição do marcador A
	`0 - go to the position where Vim was previously exited
	`" - go to the position when last editing this file
	`. - go to the position of the last change in this file
	`` - go to the position before the last jump
	:ju[mps] - list of jumps
	Ctrl + i - go to newer position in jump list
	Ctrl + o - go to older position in jump list
	:changes - list of changes
	g, - go to newer position in change list
	g; - go to older position in change list
	Ctrl + ] - jump to the tag under cursor
	Tip To jump to a mark you can either use a backtick (`) or an apostrophe ('). Using an apostrophe jumps to the beginning (first non-black) of the line holding the mark.
Macros
	qa - gravar o macro a
	q - parar a gravação do macro
	@a - executar o macro a
	@@ - re executar o último macro
Copiar e colar
	yy - copiar uma linha
	2yy - copiar duas linhas
	yw - copiar uma palavra
	y$ - copiar até o final da linha
	p - colar depois do cursor
	P - colar antes do cursor
	dd - deletar (cortar) uma linha
	2dd - deletar (cortar) duas linhas
	dw - deletar (cortar) uma palavra
	D - deletar (cortar) até o final da linha
	d$ - deletar (cortar) até o final da linha
	x - deletar (cortar) caractere
	Indent text
	>> - indent (move right) line one shiftwidth
	<< - de-indent (move left) line one shiftwidth
	>% - indent a block with () or {} (cursor on brace)
	>ib - indent inner block with ()
	>at - indent a block with <> tags
	3== - re-indent 3 lines
	=% - re-indent a block with () or {} (cursor on brace)
	=iB - re-indent inner block with {}
	gg=G - re-indent entire buffer
	]p - paste and adjust indent to current line
	Saindo
	:w - escrever (salvar) arquivo, mas não sair
	:w !sudo tee % - write out the current file using sudo
	:wq or :x or ZZ - escrever (salvar) arquivo e sair
	:q - sair (não funciona se existirem mudanças não salvas)
	:q! or ZQ - sair e descartar mudanças não salvas
	:wqa - write (save) and quit on all tabs
	Procurar e substituir
	/pattern - procurar por padrão
	?pattern - procurar por padrão na direção oposta
	\vpattern - padrão `mágico`: caracteres não-alfanuméricos são interpretados como símbolos especias de expressões regulares (sem necessidade de escapar os caracteres)
	n - repetir busca na mesma direção
	N - repetir busca na direção oposta
	:%s/old/new/g - substituir todas as ocorrências de old por new dentro do buffer
	:%s/old/new/gc - substituir todas as ocorrências de old por new dentro do buffer pedindo confirmação
	:noh[lsearch] - remover o destaque dos resultados de busca
Procurar em múltiplos arquivos
	:vim[grep] /pattern/ {`{file}`} - procurar por padrão em múltiplos arquivos
	e.g. :vim[grep] /foo/ **/*
	:cn[ext] - pular para próxima ocorrência
	:cp[revious] - pular para ocorrência anterior
	:cope[n] - abrir uma janela com a lista de ocorrências
	:ccl[ose] - close the quickfix window
Abas
	:tabnew or :tabnew {page.words.file} - abrir um arquivo em uma aba nova
	Ctrl + wT - mover a janela atual para uma aba própria
	gt or :tabn[ext] - mover para a próxima aba
	gT or :tabp[revious] - mover para a aba anterior
	#gt - mover para a aba de número #
	:tabm[ove] # - mover aba atual para posição # (indexado do 0)
	:tabc[lose] - fechar a aba atual e todas suas janelas
	:tabo[nly] - fechar todas as abas exceto a aba atual
	:tabdo command - executar o comando em todas as abas (e.g. :tabdo q - fechar todas as abas abertas)
	Trabalhando com múltiplos arquivos
	:e[dit] arquivo - editar um arquivo em um novo buffer
	:bn[ext] - ir para o próximo buffer
	:bp[revious] - ir para o buffer anterior
	:bd[elete] - deletar um buffer (fechar um arquivo)
	:b[uffer]# - go to a buffer by #
	:b[uffer] file - go to a buffer by file
	:ls or :buffers - listar todos os buffers abertos
	:sp[lit] arquivo - abrir um arquivo em um novo buffer e dividir a janela
	:vs[plit] arquivo - abrir um arquivo em um novo buffer e dividir janelas verticalmente
	:vert[ical] ba[ll] - edit all buffers as vertical windows
	:tab ba[ll] - edit all buffers as tabs
	Ctrl + ws - dividir janela
	Ctrl + wv - dividir janelas verticalmente
	Ctrl + ww - trocar de janelas
	Ctrl + wq - fechar janela
	Ctrl + wx - exchange current window with next one
	Ctrl + w= - make all windows equal height & width
	Ctrl + wh - mover o cursor para a janela a direita (vertical)
	Ctrl + wl - mover o cursor para a janela a esquerda (vertical)
	Ctrl + wj - mover o cursor para a janela abaixo (horizontal)
	Ctrl + wk - mover o cursor para a janela acima (horizontal)
	Diff
	zf - manually define a fold up to motion
	zd - delete fold under the cursor
	za - toggle fold under the cursor
	zo - open fold under the cursor
	zc - close fold under the cursor
	zr - reduce (open) all folds by one level
	zm - fold more (close) all folds by one level
	zi - toggle folding functionality
	]c - jump to start of next change
	[c - jump to start of previous change
	do or :diffg[et] - obtain (get) difference (from other buffer)
	dp or :diffpu[t] - put difference (to other buffer)
	:diffthis - make current window part of diff
	:dif[fupdate] - update differences
	:diffo[ff] - switch off diff mode for current window

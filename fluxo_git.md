# Fluxo git para codee.tech

## Lógica do branch
Para funcionar o sistema em produção ele sempre tem que ter a versão mais estável e portanto tem que ser validado pelo cliente antes de vir no ar então a lógica do ticket será sempre da seguinte forma:
1. Damos um `git checkout homolog` para entrar na branch de homologação.
2. Damos um `git pull` para pegar os arquivos atualizados no servidor
3. Criaremos uma **Branch local** da **homolog** a partir de `git checkout -b <nome_branch>`
4. Criaremos a branch remotamente no servidor com `git push origin <nome_branch>`
5. Linkaremos agora a Branch **Local** com a Branch **Remota** com o comando `git branch --set-upstream-to=origin/<nome_branch> <nome_branch> `
6. Verifique que está tudo ok dando um `git pull`
8. Adicione todos os arquivos pertinentes para fechar o ticket com `git add *`
    * Caso tenha adicionado um arquivo errado de um `git reset <file>`
        * OBS: No caso dos arquivos errados por Exemplo `git reset application/modules/*.dat `
9. Faça o Commit necessário pra mudança dos arquivos com `git commit -m "<Comentários_Relevantes>"`
10. Mande para o servidor remoto com `git push` 
11. Mude de Branch de *Homologação* com `git checkout homolog` 
12. Junte os arquivos para homologação com `git merge <nome_branch>`
    * caso de conflito verifique com `git status` quais são os arquivos conflitantes
        * *Head* é a versão que estará em Homologação
        * *<nome_branch>* será a versão conflitante 
    * Arrume o conflito alterando o arquivo em Homologação da forma correta  e volte para o passo 8
13. Com os arquivos **corretos** no pós o *merge* utilize `git push` novamente para colocar a resolução do ticket em homologação.
    * No servidor de Homologação/Master sempre só utilizaremos `git pull -X theirs`
14. Após concluido o ticket necessitamos destruir a branch tanto local quanto remotamente
15. Verificaremos que Branch que temos tanto remotas quanto locais com `git branch -a`
16. Deletaremos primeiro a Branch **Local** com o comando `git branch -d <nome_branch>`
17. Deletaremos agora a Branch **Remota** com o comando `git push origin --delete <nome_branch> `

# `O que é um Conflito de Merge no Git?`

Um conflito de merge no Git é um evento que ocorre quando o Git não consegue resolver automaticamente as diferenças de código entre dois commits. O Git só consegue fazer o merge automaticamente se os commits estiverem em linhas ou ramos diferentes.

1. O que é um conflito de merge no Git?  
Um conflito de merge no Git ocorre quando dois ou mais desenvolvedores editam as mesmas linhas de um arquivo simultaneamente, e o Git tem dificuldade para conciliar as alterações.

2. Como identificar um conflito de merge no Git?  
O Git informa sobre um conflito de merge após uma tentativa de `git merge`, marcando o arquivo afetado com indicadores de conflito.

3. Como resolver conflitos de merge no Git?  
Conflitos de merge no Git podem ser resolvidos usando ferramentas de merge ou manualmente, editando o código conflitante e realizando o commit do arquivo resolvido.

4. O que são ferramentas de merge do Git?  
Ferramentas de merge do Git são utilitários, como o KDiff3 ou o Meld, que oferecem uma interface gráfica para gerenciar e resolver conflitos de merge.

5. O que faz o comando `git merge --abort`?  
O comando `git merge --abort` reverte a ação de merge, restaurando o projeto para o estado anterior à tentativa de merge.

6. Posso evitar conflitos de merge no Git?  
Embora não possam ser evitados completamente, commits menores e frequentes, boa comunicação e o uso do `git pull` antes de enviar alterações podem reduzir as chances de conflitos.

A seguir, um exemplo de como um conflito de merge no Git funciona:

![pull-push](/manual-git-grupo1/imagens/pull-push.jpg)

Vamos assumir que existem dois desenvolvedores: Desenvolvedor A e Desenvolvedor B. Ambos puxam o mesmo arquivo de código do repositório remoto e fazem alterações nesse arquivo. Depois das alterações, o Desenvolvedor A envia o arquivo de volta ao repositório remoto. Agora, quando o Desenvolvedor B tenta enviar sua versão modificada, não consegue, pois o arquivo já foi alterado no repositório remoto.

Para evitar esse tipo de conflito, os desenvolvedores trabalham em ramos separados e isolados. O comando `git merge` combina os ramos separados e resolve quaisquer edições conflitantes.

Agora que vimos os conceitos básicos sobre conflitos de merge no Git, vamos analisar os diferentes tipos de conflitos.

# `Como Resolver Conflitos de Merge no Git?`

Há algumas etapas que podem simplificar a resolução de conflitos de merge no Git.

**Etapa 1**: A maneira mais fácil de resolver um arquivo com conflito é abri-lo e fazer as alterações necessárias.

**Etapa 2**: Após editar o arquivo, use o comando `git add` para colocar o novo conteúdo mesclado na staging area.

**Etapa 3**: A etapa final é criar um novo commit com o comando `git commit`.

**Etapa 4**: O Git criará um novo commit de merge para finalizar a fusão.

Vamos agora analisar alguns comandos Git que desempenham papel importante na resolução de conflitos.

# `Comandos Git para Resolver Conflitos`

1. `git log --merge`  
Exibe a lista de commits que estão causando o conflito.

2. `git diff`  
Mostra as diferenças entre estados de arquivos ou repositórios.

3. `git checkout`  
Usado para desfazer alterações em um arquivo ou mudar de branch.

4. `git reset --mixed`  
Desfaz alterações na área de trabalho e na staging area.

5. `git merge --abort`  
Sai do processo de merge e retorna ao estado anterior ao início da fusão.

6. `git reset`  
Restaura arquivos com conflito ao seu estado original durante um conflito de merge.

# `Tipos de Conflitos de Merge no Git`

Há dois momentos em que um merge pode entrar em estado de conflito:

1. **Ao Iniciar o Processo de Merge**  
Se houver alterações pendentes na staging area do diretório de trabalho, o merge não será iniciado.  
Neste caso, os conflitos acontecem devido a alterações pendentes que precisam ser estabilizadas com comandos Git apropriados.

2. **Durante o Processo de Merge**  
Falhas durante o processo indicam conflitos entre o branch local e o branch sendo mesclado.  
Nesse caso, o Git resolve o máximo possível automaticamente, mas certas partes precisam ser resolvidas manualmente nos arquivos conflitantes.

Vamos agora ver como resolver conflitos de merge no Git na prática.

# `Exemplo: Resolvendo Conflitos de Merge no Git`

Primeiro, inicialize dois repositórios:

```
git init A
git init B
```

![001](/manual-git-grupo1/imagens/001.jpg)

Adicione o endereço remoto no repositório A:

```
git remote add origin *endereço*
```

![002](/manual-git-grupo1/imagens/002.jpg)

A próxima etapa é puxar todas as alterações do repositório central para o repositório local.

```
git pull origin master

```

![003](/manual-git-grupo1/imagens/003.jpg)

Repita o mesmo processo para adicionar a origem no repositório B:

```
git remote add origin *endereço*

```

![004](/manual-git-grupo1/imagens/004.jpg)

Execute novamente o comando `pull` para obter todo o conteúdo do repositório remoto para o local:

```
git pull origin master
```

![005](/manual-git-grupo1/imagens/005.jpg)

Esses dois repositórios representam os ambientes de dois desenvolvedores diferentes.

Vamos voltar ao repositório A:

```
cd ../A
```

![006](/manual-git-grupo1/imagens/006.jpg)

No repositório A, o arquivo README é aberto para fazer modificações:

```
vi README.md
```

![007](/manual-git-grupo1/imagens/007.jpg)

Faça as alterações necessárias no arquivo e salve.

Execute o comando `git status` para verificar as mudanças:

```
git status
```

![008](/manual-git-grupo1/imagens/008.jpg)

A seguir, adicione as alterações à staging area e faça o commit:

```
git add .
git commit -m "mensagem do commit"
```

![009](/manual-git-grupo1/imagens/009.jpg)

Depois do commit, envie o arquivo alterado para o repositório remoto:

```
git push origin master
```

![010](/manual-git-grupo1/imagens/010.jpg)

Agora, volte para o repositório B:

```
cd B
```

![011](/manual-git-grupo1/imagens/011.jpg)

Abra o arquivo README:

```
vi README.md
```

![012](/manual-git-grupo1/imagens/012.jpg)

Faça alterações, salve e feche o arquivo. Em seguida, adicione e faça o commit:

```
git add .
git commit -m "mensagem do commit"
```

![013](/manual-git-grupo1/imagens/013.jpg)

Tente enviar o arquivo ao repositório remoto:

```
git push
```

![014](/manual-git-grupo1/imagens/014.jpg)

Um erro aparece, indicando que as atualizações foram rejeitadas.

Agora, execute:

```
git rebase origin master
```

![015](/manual-git-grupo1/imagens/015.jpg)

Neste momento, há conflitos visíveis que devem ser resolvidos manualmente.

Se quiser pular este commit, digite `git rebase --skip`, ou para cancelar o rebase, use `git rebase --abort`.

Depois de gerenciar o conflito manualmente, abra a ferramenta de merge:

```
git mergetool
```

![016](/manual-git-grupo1/imagens/016.jpg)

Ao usar esse comando, todos os arquivos serão processados:

![017](/manual-git-grupo1/imagens/017.jpg)

Estes são todos os processos e modificações no arquivo.

Você verá três versões diferentes do arquivo e poderá visualizar o que foi adicionado ou removido.

Após rolar a tela, você pode verificar exatamente onde o conflito ocorreu.

![018](/manual-git-grupo1/imagens/018.jpg)

Você pode decidir se quer manter ou remover uma linha específica. Aqui, vamos remover a linha.

![019](/manual-git-grupo1/imagens/019.jpg)

Modificações manuais nos permitiram resolver o conflito. Salve e feche o arquivo final.

![020](/manual-git-grupo1/imagens/020.jpg)

Agora, execute:

```
git rebase --continue
```

![021](/manual-git-grupo1/imagens/021.jpg)

Com o conflito resolvido, agora é possível fazer o push do arquivo para o repositório remoto.

![022](/manual-git-grupo1/imagens/022.jpg)

Você pode verificar os commits em seu repositório remoto.

![023](/manual-git-grupo1/imagens/023.jpg)
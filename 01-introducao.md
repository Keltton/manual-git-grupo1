## `O que é Controle de Versão`

Controle de versão é um sistema que registra alterações em um arquivo ou conjunto de arquivos ao longo do tempo, permitindo que você recupere versões específicas posteriormente. Nos exemplos deste material, você usará código-fonte como os arquivos controlados por versão, embora na prática isso possa ser feito com quase qualquer tipo de arquivo no computador.

Se você é designer gráfico ou web e quer manter todas as versões de uma imagem ou layout, um Sistema de Controle de Versão (VCS) é uma ferramenta extremamente útil. Ele permite reverter arquivos selecionados a um estado anterior, reverter todo o projeto a um estado anterior, comparar mudanças ao longo do tempo, ver quem modificou algo que está causando problemas, quem introduziu um erro e quando, entre outras coisas. Usar um VCS geralmente significa que, se algo der errado ou arquivos forem perdidos, você pode recuperá-los com facilidade. Além disso, tudo isso vem com um custo operacional muito baixo.

Uma das ferramentas de VCS mais populares foi um sistema chamado RCS, que ainda é distribuído com muitos computadores atualmente. O RCS funciona armazenando conjuntos de alterações (ou seja, as diferenças entre arquivos) em um formato especial no disco; ele pode então recriar como qualquer arquivo era em um momento específico somando todos os patches.

---

## `Problemas resolvidos pelo Git`

### **Editar uma mensagem de commit**

Às vezes, ao escrever a mensagem do commit, cometemos um erro de digitação. Os comandos a seguir podem ser usados para corrigir isso. Lembre-se de que o comando abaixo cria um novo commit, então evite usar `--amend` para modificar commits que já foram enviados para um repositório central.

```
git commit --amend
git commit --amend -m "Nova mensagem"
```

Se você esquecer de adicionar um arquivo com `git add`, basta adicioná-lo e emendar o commit anterior:

```
git add nome_do_arquivo_esquecido
git commit --amend
```

---

### **Desfazer commits locais**

Às vezes percebemos que houve um erro após alguns commits já terem sido feitos localmente:

```
git reset HEAD~2
git reset --hard HEAD~2
```

---

### **Remover um arquivo do Git sem removê-lo do sistema de arquivos**

Se você não tomar cuidado, pode acabar adicionando arquivos desnecessários com `git add`.

Se usar `git rm`, o arquivo será removido tanto da área de staging quanto do sistema de arquivos.

```
git reset nome_do_arquivo
echo nome_do_arquivo >> .gitignore
```

---

### **Reverter commits já enviados**

Às vezes commits com erros acabam indo para o repositório central mesmo após o uso de `amend` e `rebase`. Nestes casos, use os comandos abaixo:

```
git revert c761f5c
git revert HEAD^
git revert develop~4..develop~2
```

Se não quiser criar commits adicionais de reversão, mas apenas aplicar as mudanças no diretório de trabalho, use a opção `--no-commit` ou `-n`:

```
git revert -n HEAD
```

---

### **Evitar conflitos de merge repetidos**

Corrigir conflitos de merge repetidamente é bem irritante. Suponha que sua equipe esteja trabalhando em várias branches de funcionalidades ao mesmo tempo. Agora você quer fazer o merge de todas elas. Surgem vários conflitos que você resolve. Mas descobre que uma das branches ainda não está pronta, então desfaz o merge. Dias depois, quando a branch estiver pronta, você faz o merge de novo. Graças ao registro de resoluções, você não precisará resolver os mesmos conflitos novamente.

```
git config --global rerere.enabled true
```

---

### **Encontrar o commit que quebrou algo após um merge**

Às vezes é necessário encontrar o commit que alterou o projeto de forma errada. Esse commit pode ser difícil de identificar, o que consome muito tempo. O Git tem um método para encontrar o commit problemático após um merge:

```
git bisect start
git bisect bad
git bisect good revisão

Agora o git vai automaticamente fazer checkout de uma revisão intermediária entre as versões conhecidas como "boa" e "ruim":
git bisect good
git bisect bad
```



## `Breve história do Git`

Git é um software de controle de versão gratuito e de código aberto. Foi criado por Linus Torvalds em 2005. Esta ferramenta foi inicialmente desenvolvida para permitir o trabalho colaborativo de vários desenvolvedores no núcleo (kernel) do Linux.

Basicamente, o Git é um rastreador de conteúdo. Ele pode ser usado para armazenar qualquer tipo de conteúdo — e é mais comumente usado para armazenar código por conta dos recursos adicionais que oferece.

Projetos reais geralmente envolvem múltiplos desenvolvedores trabalhando juntos. Assim, eles precisam de um sistema de controle de versão como o Git para garantir que não haja conflitos de código entre eles.

Além disso, os requisitos em projetos desse tipo mudam com frequência. Um sistema de controle de versão permite que os desenvolvedores revertam alterações e voltem a versões anteriores do código.

O sistema de branches (ramificações) do Git permite que os desenvolvedores trabalhem individualmente em tarefas específicas (por exemplo: Uma branch → Uma tarefa ou Uma branch → Um desenvolvedor). Basicamente, pense no Git como um pequeno software que gerencia sua base de código, se você for um desenvolvedor.



## `Diferença entre Git e GitHub`

**Git:** Git é um sistema de controle de versão distribuído para rastrear mudanças no código-fonte durante o desenvolvimento de software. Ele é projetado para coordenar o trabalho entre programadores, mas pode ser usado para controlar alterações em qualquer conjunto de arquivos. Seus objetivos incluem velocidade, integridade de dados e suporte a fluxos de trabalho distribuídos e não lineares.

**GitHub:** GitHub é um serviço web de hospedagem de repositórios Git, que oferece todas as funcionalidades de controle de revisão distribuído e gerenciamento de código-fonte do Git, além de recursos próprios.


Git é um software.
GitHub é um serviço.            

Git é uma ferramenta de linha de comando.
GitHub é uma interface gráfica baseada na web.

Git é instalado localmente no sistema.
GitHub é hospedado na web.

Git é mantido pela comunidade Linux.
GitHub é mantido pela Microsoft.

Git foca em controle de versão e compartilhamento de código.
GitHub foca em hospedagem centralizada de código-fonte.

Git é um sistema de controle de versão para gerenciar o histórico do código-fonte.
GitHub é um serviço de hospedagem para repositórios Git.

Git foi lançado em 2005.
GitHub foi lançado em 2008.

Git tem licença open-source.
GitHub oferece planos gratuitos e pagos.

Git requer pouca configuração de ferramentas externas.
GitHub possui um marketplace ativo para integração de ferramentas.

Git fornece uma interface gráfica chamada Git Gui.
GitHub fornece uma interface gráfica chamada GitHub Desktop.

Git compete com CVS, Subversion, Mercurial, etc.
GitHub compete com GitLab, Bitbucket, AWS CodeCommit, Azure DevOps Server, etc.## `O que é Controle de Versão`

Controle de versão é um sistema que registra alterações em um arquivo ou conjunto de arquivos ao longo do tempo, permitindo que você recupere versões específicas posteriormente. Nos exemplos deste material, você usará código-fonte como os arquivos controlados por versão, embora na prática isso possa ser feito com quase qualquer tipo de arquivo no computador.

Se você é designer gráfico ou web e quer manter todas as versões de uma imagem ou layout, um Sistema de Controle de Versão (VCS) é uma ferramenta extremamente útil. Ele permite reverter arquivos selecionados a um estado anterior, reverter todo o projeto a um estado anterior, comparar mudanças ao longo do tempo, ver quem modificou algo que está causando problemas, quem introduziu um erro e quando, entre outras coisas. Usar um VCS geralmente significa que, se algo der errado ou arquivos forem perdidos, você pode recuperá-los com facilidade. Além disso, tudo isso vem com um custo operacional muito baixo.

Uma das ferramentas de VCS mais populares foi um sistema chamado RCS, que ainda é distribuído com muitos computadores atualmente. O RCS funciona armazenando conjuntos de alterações (ou seja, as diferenças entre arquivos) em um formato especial no disco; ele pode então recriar como qualquer arquivo era em um momento específico somando todos os patches.

---

## `Problemas resolvidos pelo Git`

### **Editar uma mensagem de commit**

Às vezes, ao escrever a mensagem do commit, cometemos um erro de digitação. Os comandos a seguir podem ser usados para corrigir isso. Lembre-se de que o comando abaixo cria um novo commit, então evite usar `--amend` para modificar commits que já foram enviados para um repositório central.

```
git commit --amend
git commit --amend -m "Nova mensagem"
```

Se você esquecer de adicionar um arquivo com `git add`, basta adicioná-lo e emendar o commit anterior:

```
git add nome_do_arquivo_esquecido
git commit --amend
```

---

### **Desfazer commits locais**

Às vezes percebemos que houve um erro após alguns commits já terem sido feitos localmente:

```
git reset HEAD~2
git reset --hard HEAD~2
```

---

### **Remover um arquivo do Git sem removê-lo do sistema de arquivos**

Se você não tomar cuidado, pode acabar adicionando arquivos desnecessários com `git add`.

Se usar `git rm`, o arquivo será removido tanto da área de staging quanto do sistema de arquivos.

```
git reset nome_do_arquivo
echo nome_do_arquivo >> .gitignore
```

---

### **Reverter commits já enviados**

Às vezes commits com erros acabam indo para o repositório central mesmo após o uso de `amend` e `rebase`. Nestes casos, use os comandos abaixo:

```
git revert c761f5c
git revert HEAD^
git revert develop~4..develop~2
```

Se não quiser criar commits adicionais de reversão, mas apenas aplicar as mudanças no diretório de trabalho, use a opção `--no-commit` ou `-n`:

```
git revert -n HEAD
```

---

### **Evitar conflitos de merge repetidos**

Corrigir conflitos de merge repetidamente é bem irritante. Suponha que sua equipe esteja trabalhando em várias branches de funcionalidades ao mesmo tempo. Agora você quer fazer o merge de todas elas. Surgem vários conflitos que você resolve. Mas descobre que uma das branches ainda não está pronta, então desfaz o merge. Dias depois, quando a branch estiver pronta, você faz o merge de novo. Graças ao registro de resoluções, você não precisará resolver os mesmos conflitos novamente.

```
git config --global rerere.enabled true
```

---

### **Encontrar o commit que quebrou algo após um merge**

Às vezes é necessário encontrar o commit que alterou o projeto de forma errada. Esse commit pode ser difícil de identificar, o que consome muito tempo. O Git tem um método para encontrar o commit problemático após um merge:

```
git bisect start
git bisect bad
git bisect good revisão

Agora o git vai automaticamente fazer checkout de uma revisão intermediária entre as versões conhecidas como "boa" e "ruim":
git bisect good
git bisect bad
```



## `Breve história do Git`

Git é um software de controle de versão gratuito e de código aberto. Foi criado por Linus Torvalds em 2005. Esta ferramenta foi inicialmente desenvolvida para permitir o trabalho colaborativo de vários desenvolvedores no núcleo (kernel) do Linux.

Basicamente, o Git é um rastreador de conteúdo. Ele pode ser usado para armazenar qualquer tipo de conteúdo — e é mais comumente usado para armazenar código por conta dos recursos adicionais que oferece.

Projetos reais geralmente envolvem múltiplos desenvolvedores trabalhando juntos. Assim, eles precisam de um sistema de controle de versão como o Git para garantir que não haja conflitos de código entre eles.

Além disso, os requisitos em projetos desse tipo mudam com frequência. Um sistema de controle de versão permite que os desenvolvedores revertam alterações e voltem a versões anteriores do código.

O sistema de branches (ramificações) do Git permite que os desenvolvedores trabalhem individualmente em tarefas específicas (por exemplo: Uma branch → Uma tarefa ou Uma branch → Um desenvolvedor). Basicamente, pense no Git como um pequeno software que gerencia sua base de código, se você for um desenvolvedor.



## `Diferença entre Git e GitHub`

**Git:** Git é um sistema de controle de versão distribuído para rastrear mudanças no código-fonte durante o desenvolvimento de software. Ele é projetado para coordenar o trabalho entre programadores, mas pode ser usado para controlar alterações em qualquer conjunto de arquivos. Seus objetivos incluem velocidade, integridade de dados e suporte a fluxos de trabalho distribuídos e não lineares.

**GitHub:** GitHub é um serviço web de hospedagem de repositórios Git, que oferece todas as funcionalidades de controle de revisão distribuído e gerenciamento de código-fonte do Git, além de recursos próprios.


Git é um software.
GitHub é um serviço.            

Git é uma ferramenta de linha de comando.
GitHub é uma interface gráfica baseada na web.

Git é instalado localmente no sistema.
GitHub é hospedado na web.

Git é mantido pela comunidade Linux.
GitHub é mantido pela Microsoft.

Git foca em controle de versão e compartilhamento de código.
GitHub foca em hospedagem centralizada de código-fonte.

Git é um sistema de controle de versão para gerenciar o histórico do código-fonte.
GitHub é um serviço de hospedagem para repositórios Git.

Git foi lançado em 2005.
GitHub foi lançado em 2008.

Git tem licença open-source.
GitHub oferece planos gratuitos e pagos.

Git requer pouca configuração de ferramentas externas.
GitHub possui um marketplace ativo para integração de ferramentas.

Git fornece uma interface gráfica chamada Git Gui.
GitHub fornece uma interface gráfica chamada GitHub Desktop.

Git compete com CVS, Subversion, Mercurial, etc.
GitHub compete com GitLab, Bitbucket, AWS CodeCommit, Azure DevOps Server, etc.## `O que é Controle de Versão`

Controle de versão é um sistema que registra alterações em um arquivo ou conjunto de arquivos ao longo do tempo, permitindo que você recupere versões específicas posteriormente. Nos exemplos deste material, você usará código-fonte como os arquivos controlados por versão, embora na prática isso possa ser feito com quase qualquer tipo de arquivo no computador.

Se você é designer gráfico ou web e quer manter todas as versões de uma imagem ou layout, um Sistema de Controle de Versão (VCS) é uma ferramenta extremamente útil. Ele permite reverter arquivos selecionados a um estado anterior, reverter todo o projeto a um estado anterior, comparar mudanças ao longo do tempo, ver quem modificou algo que está causando problemas, quem introduziu um erro e quando, entre outras coisas. Usar um VCS geralmente significa que, se algo der errado ou arquivos forem perdidos, você pode recuperá-los com facilidade. Além disso, tudo isso vem com um custo operacional muito baixo.

Uma das ferramentas de VCS mais populares foi um sistema chamado RCS, que ainda é distribuído com muitos computadores atualmente. O RCS funciona armazenando conjuntos de alterações (ou seja, as diferenças entre arquivos) em um formato especial no disco; ele pode então recriar como qualquer arquivo era em um momento específico somando todos os patches.

---

## `Problemas resolvidos pelo Git`

### **Editar uma mensagem de commit**

Às vezes, ao escrever a mensagem do commit, cometemos um erro de digitação. Os comandos a seguir podem ser usados para corrigir isso. Lembre-se de que o comando abaixo cria um novo commit, então evite usar `--amend` para modificar commits que já foram enviados para um repositório central.

```
git commit --amend
git commit --amend -m "Nova mensagem"
```

Se você esquecer de adicionar um arquivo com `git add`, basta adicioná-lo e emendar o commit anterior:

```
git add nome_do_arquivo_esquecido
git commit --amend
```

---

### **Desfazer commits locais**

Às vezes percebemos que houve um erro após alguns commits já terem sido feitos localmente:

```
git reset HEAD~2
git reset --hard HEAD~2
```

---

### **Remover um arquivo do Git sem removê-lo do sistema de arquivos**

Se você não tomar cuidado, pode acabar adicionando arquivos desnecessários com `git add`.

Se usar `git rm`, o arquivo será removido tanto da área de staging quanto do sistema de arquivos.

```
git reset nome_do_arquivo
echo nome_do_arquivo >> .gitignore
```

---

### **Reverter commits já enviados**

Às vezes commits com erros acabam indo para o repositório central mesmo após o uso de `amend` e `rebase`. Nestes casos, use os comandos abaixo:

```
git revert c761f5c
git revert HEAD^
git revert develop~4..develop~2
```

Se não quiser criar commits adicionais de reversão, mas apenas aplicar as mudanças no diretório de trabalho, use a opção `--no-commit` ou `-n`:

```
git revert -n HEAD
```

---

### **Evitar conflitos de merge repetidos**

Corrigir conflitos de merge repetidamente é bem irritante. Suponha que sua equipe esteja trabalhando em várias branches de funcionalidades ao mesmo tempo. Agora você quer fazer o merge de todas elas. Surgem vários conflitos que você resolve. Mas descobre que uma das branches ainda não está pronta, então desfaz o merge. Dias depois, quando a branch estiver pronta, você faz o merge de novo. Graças ao registro de resoluções, você não precisará resolver os mesmos conflitos novamente.

```
git config --global rerere.enabled true
```

---

### **Encontrar o commit que quebrou algo após um merge**

Às vezes é necessário encontrar o commit que alterou o projeto de forma errada. Esse commit pode ser difícil de identificar, o que consome muito tempo. O Git tem um método para encontrar o commit problemático após um merge:

```
git bisect start
git bisect bad
git bisect good revisão

Agora o git vai automaticamente fazer checkout de uma revisão intermediária entre as versões conhecidas como "boa" e "ruim":
git bisect good
git bisect bad
```



## `Breve história do Git`

Git é um software de controle de versão gratuito e de código aberto. Foi criado por Linus Torvalds em 2005. Esta ferramenta foi inicialmente desenvolvida para permitir o trabalho colaborativo de vários desenvolvedores no núcleo (kernel) do Linux.

Basicamente, o Git é um rastreador de conteúdo. Ele pode ser usado para armazenar qualquer tipo de conteúdo — e é mais comumente usado para armazenar código por conta dos recursos adicionais que oferece.

Projetos reais geralmente envolvem múltiplos desenvolvedores trabalhando juntos. Assim, eles precisam de um sistema de controle de versão como o Git para garantir que não haja conflitos de código entre eles.

Além disso, os requisitos em projetos desse tipo mudam com frequência. Um sistema de controle de versão permite que os desenvolvedores revertam alterações e voltem a versões anteriores do código.

O sistema de branches (ramificações) do Git permite que os desenvolvedores trabalhem individualmente em tarefas específicas (por exemplo: Uma branch → Uma tarefa ou Uma branch → Um desenvolvedor). Basicamente, pense no Git como um pequeno software que gerencia sua base de código, se você for um desenvolvedor.



## `Diferença entre Git e GitHub`

**Git:** Git é um sistema de controle de versão distribuído para rastrear mudanças no código-fonte durante o desenvolvimento de software. Ele é projetado para coordenar o trabalho entre programadores, mas pode ser usado para controlar alterações em qualquer conjunto de arquivos. Seus objetivos incluem velocidade, integridade de dados e suporte a fluxos de trabalho distribuídos e não lineares.

**GitHub:** GitHub é um serviço web de hospedagem de repositórios Git, que oferece todas as funcionalidades de controle de revisão distribuído e gerenciamento de código-fonte do Git, além de recursos próprios.


Git é um software.
GitHub é um serviço.            

Git é uma ferramenta de linha de comando.
GitHub é uma interface gráfica baseada na web.

Git é instalado localmente no sistema.
GitHub é hospedado na web.

Git é mantido pela comunidade Linux.
GitHub é mantido pela Microsoft.

Git foca em controle de versão e compartilhamento de código.
GitHub foca em hospedagem centralizada de código-fonte.

Git é um sistema de controle de versão para gerenciar o histórico do código-fonte.
GitHub é um serviço de hospedagem para repositórios Git.

Git foi lançado em 2005.
GitHub foi lançado em 2008.

Git tem licença open-source.
GitHub oferece planos gratuitos e pagos.

Git requer pouca configuração de ferramentas externas.
GitHub possui um marketplace ativo para integração de ferramentas.

Git fornece uma interface gráfica chamada Git Gui.
GitHub fornece uma interface gráfica chamada GitHub Desktop.

Git compete com CVS, Subversion, Mercurial, etc.
GitHub compete com GitLab, Bitbucket, AWS CodeCommit, Azure DevOps Server, etc.## `O que é Controle de Versão`

Controle de versão é um sistema que registra alterações em um arquivo ou conjunto de arquivos ao longo do tempo, permitindo que você recupere versões específicas posteriormente. Nos exemplos deste material, você usará código-fonte como os arquivos controlados por versão, embora na prática isso possa ser feito com quase qualquer tipo de arquivo no computador.

Se você é designer gráfico ou web e quer manter todas as versões de uma imagem ou layout, um Sistema de Controle de Versão (VCS) é uma ferramenta extremamente útil. Ele permite reverter arquivos selecionados a um estado anterior, reverter todo o projeto a um estado anterior, comparar mudanças ao longo do tempo, ver quem modificou algo que está causando problemas, quem introduziu um erro e quando, entre outras coisas. Usar um VCS geralmente significa que, se algo der errado ou arquivos forem perdidos, você pode recuperá-los com facilidade. Além disso, tudo isso vem com um custo operacional muito baixo.

Uma das ferramentas de VCS mais populares foi um sistema chamado RCS, que ainda é distribuído com muitos computadores atualmente. O RCS funciona armazenando conjuntos de alterações (ou seja, as diferenças entre arquivos) em um formato especial no disco; ele pode então recriar como qualquer arquivo era em um momento específico somando todos os patches.

---

## `Problemas resolvidos pelo Git`

### **Editar uma mensagem de commit**

Às vezes, ao escrever a mensagem do commit, cometemos um erro de digitação. Os comandos a seguir podem ser usados para corrigir isso. Lembre-se de que o comando abaixo cria um novo commit, então evite usar `--amend` para modificar commits que já foram enviados para um repositório central.

```
git commit --amend
git commit --amend -m "Nova mensagem"
```

Se você esquecer de adicionar um arquivo com `git add`, basta adicioná-lo e emendar o commit anterior:

```
git add nome_do_arquivo_esquecido
git commit --amend
```

---

### **Desfazer commits locais**

Às vezes percebemos que houve um erro após alguns commits já terem sido feitos localmente:

```
git reset HEAD~2
git reset --hard HEAD~2
```

---

### **Remover um arquivo do Git sem removê-lo do sistema de arquivos**

Se você não tomar cuidado, pode acabar adicionando arquivos desnecessários com `git add`.

Se usar `git rm`, o arquivo será removido tanto da área de staging quanto do sistema de arquivos.

```
git reset nome_do_arquivo
echo nome_do_arquivo >> .gitignore
```

---

### **Reverter commits já enviados**

Às vezes commits com erros acabam indo para o repositório central mesmo após o uso de `amend` e `rebase`. Nestes casos, use os comandos abaixo:

```
git revert c761f5c
git revert HEAD^
git revert develop~4..develop~2
```

Se não quiser criar commits adicionais de reversão, mas apenas aplicar as mudanças no diretório de trabalho, use a opção `--no-commit` ou `-n`:

```
git revert -n HEAD
```

---

### **Evitar conflitos de merge repetidos**

Corrigir conflitos de merge repetidamente é bem irritante. Suponha que sua equipe esteja trabalhando em várias branches de funcionalidades ao mesmo tempo. Agora você quer fazer o merge de todas elas. Surgem vários conflitos que você resolve. Mas descobre que uma das branches ainda não está pronta, então desfaz o merge. Dias depois, quando a branch estiver pronta, você faz o merge de novo. Graças ao registro de resoluções, você não precisará resolver os mesmos conflitos novamente.

```
git config --global rerere.enabled true
```

---

### **Encontrar o commit que quebrou algo após um merge**

Às vezes é necessário encontrar o commit que alterou o projeto de forma errada. Esse commit pode ser difícil de identificar, o que consome muito tempo. O Git tem um método para encontrar o commit problemático após um merge:

```
git bisect start
git bisect bad
git bisect good revisão

Agora o git vai automaticamente fazer checkout de uma revisão intermediária entre as versões conhecidas como "boa" e "ruim":
git bisect good
git bisect bad
```



## `Breve história do Git`

Git é um software de controle de versão gratuito e de código aberto. Foi criado por Linus Torvalds em 2005. Esta ferramenta foi inicialmente desenvolvida para permitir o trabalho colaborativo de vários desenvolvedores no núcleo (kernel) do Linux.

Basicamente, o Git é um rastreador de conteúdo. Ele pode ser usado para armazenar qualquer tipo de conteúdo — e é mais comumente usado para armazenar código por conta dos recursos adicionais que oferece.

Projetos reais geralmente envolvem múltiplos desenvolvedores trabalhando juntos. Assim, eles precisam de um sistema de controle de versão como o Git para garantir que não haja conflitos de código entre eles.

Além disso, os requisitos em projetos desse tipo mudam com frequência. Um sistema de controle de versão permite que os desenvolvedores revertam alterações e voltem a versões anteriores do código.

O sistema de branches (ramificações) do Git permite que os desenvolvedores trabalhem individualmente em tarefas específicas (por exemplo: Uma branch → Uma tarefa ou Uma branch → Um desenvolvedor). Basicamente, pense no Git como um pequeno software que gerencia sua base de código, se você for um desenvolvedor.



## `Diferença entre Git e GitHub`

**Git:** Git é um sistema de controle de versão distribuído para rastrear mudanças no código-fonte durante o desenvolvimento de software. Ele é projetado para coordenar o trabalho entre programadores, mas pode ser usado para controlar alterações em qualquer conjunto de arquivos. Seus objetivos incluem velocidade, integridade de dados e suporte a fluxos de trabalho distribuídos e não lineares.

**GitHub:** GitHub é um serviço web de hospedagem de repositórios Git, que oferece todas as funcionalidades de controle de revisão distribuído e gerenciamento de código-fonte do Git, além de recursos próprios.


Git é um software.
GitHub é um serviço.            

Git é uma ferramenta de linha de comando.
GitHub é uma interface gráfica baseada na web.

Git é instalado localmente no sistema.
GitHub é hospedado na web.

Git é mantido pela comunidade Linux.
GitHub é mantido pela Microsoft.

Git foca em controle de versão e compartilhamento de código.
GitHub foca em hospedagem centralizada de código-fonte.

Git é um sistema de controle de versão para gerenciar o histórico do código-fonte.
GitHub é um serviço de hospedagem para repositórios Git.

Git foi lançado em 2005.
GitHub foi lançado em 2008.

Git tem licença open-source.
GitHub oferece planos gratuitos e pagos.

Git requer pouca configuração de ferramentas externas.
GitHub possui um marketplace ativo para integração de ferramentas.

Git fornece uma interface gráfica chamada Git Gui.
GitHub fornece uma interface gráfica chamada GitHub Desktop.

Git compete com CVS, Subversion, Mercurial, etc.
GitHub compete com GitLab, Bitbucket, AWS CodeCommit, Azure DevOps Server, etc.dsadas
## `O que é Controle de Versão`

Controle de versão é um sistema que registra alterações em um arquivo ou conjunto de arquivos ao longo do tempo, permitindo que você recupere versões específicas posteriormente. Nos exemplos deste material, você usará código-fonte como os arquivos controlados por versão, embora na prática isso possa ser feito com quase qualquer tipo de arquivo no computador.

Se você é designer gráfico ou web e quer manter todas as versões de uma imagem ou layout, um Sistema de Controle de Versão (VCS) é uma ferramenta extremamente útil. Ele permite reverter arquivos selecionados a um estado anterior, reverter todo o projeto a um estado anterior, comparar mudanças ao longo do tempo, ver quem modificou algo que está causando problemas, quem introduziu um erro e quando, entre outras coisas. Usar um VCS geralmente significa que, se algo der errado ou arquivos forem perdidos, você pode recuperá-los com facilidade. Além disso, tudo isso vem com um custo operacional muito baixo.

Uma das ferramentas de VCS mais populares foi um sistema chamado RCS, que ainda é distribuído com muitos computadores atualmente. O RCS funciona armazenando conjuntos de alterações (ou seja, as diferenças entre arquivos) em um formato especial no disco; ele pode então recriar como qualquer arquivo era em um momento específico somando todos os patches.

---

## `Problemas resolvidos pelo Git`

### **Editar uma mensagem de commit**

Às vezes, ao escrever a mensagem do commit, cometemos um erro de digitação. Os comandos a seguir podem ser usados para corrigir isso. Lembre-se de que o comando abaixo cria um novo commit, então evite usar `--amend` para modificar commits que já foram enviados para um repositório central.

```
git commit --amend
git commit --amend -m "Nova mensagem"
```

Se você esquecer de adicionar um arquivo com `git add`, basta adicioná-lo e emendar o commit anterior:

```
git add nome_do_arquivo_esquecido
git commit --amend
```

---

### **Desfazer commits locais**

Às vezes percebemos que houve um erro após alguns commits já terem sido feitos localmente:

```
git reset HEAD~2
git reset --hard HEAD~2
```

---

### **Remover um arquivo do Git sem removê-lo do sistema de arquivos**

Se você não tomar cuidado, pode acabar adicionando arquivos desnecessários com `git add`.

Se usar `git rm`, o arquivo será removido tanto da área de staging quanto do sistema de arquivos.

```
git reset nome_do_arquivo
echo nome_do_arquivo >> .gitignore
```

---

### **Reverter commits já enviados**

Às vezes commits com erros acabam indo para o repositório central mesmo após o uso de `amend` e `rebase`. Nestes casos, use os comandos abaixo:

```
git revert c761f5c
git revert HEAD^
git revert develop~4..develop~2
```

Se não quiser criar commits adicionais de reversão, mas apenas aplicar as mudanças no diretório de trabalho, use a opção `--no-commit` ou `-n`:

```
git revert -n HEAD
```

---

### **Evitar conflitos de merge repetidos**

Corrigir conflitos de merge repetidamente é bem irritante. Suponha que sua equipe esteja trabalhando em várias branches de funcionalidades ao mesmo tempo. Agora você quer fazer o merge de todas elas. Surgem vários conflitos que você resolve. Mas descobre que uma das branches ainda não está pronta, então desfaz o merge. Dias depois, quando a branch estiver pronta, você faz o merge de novo. Graças ao registro de resoluções, você não precisará resolver os mesmos conflitos novamente.

```
git config --global rerere.enabled true
```

---

### **Encontrar o commit que quebrou algo após um merge**

Às vezes é necessário encontrar o commit que alterou o projeto de forma errada. Esse commit pode ser difícil de identificar, o que consome muito tempo. O Git tem um método para encontrar o commit problemático após um merge:

```
git bisect start
git bisect bad
git bisect good revisão

Agora o git vai automaticamente fazer checkout de uma revisão intermediária entre as versões conhecidas como "boa" e "ruim":
git bisect good
git bisect bad
```



## `Breve história do Git`

Git é um software de controle de versão gratuito e de código aberto. Foi criado por Linus Torvalds em 2005. Esta ferramenta foi inicialmente desenvolvida para permitir o trabalho colaborativo de vários desenvolvedores no núcleo (kernel) do Linux.

Basicamente, o Git é um rastreador de conteúdo. Ele pode ser usado para armazenar qualquer tipo de conteúdo — e é mais comumente usado para armazenar código por conta dos recursos adicionais que oferece.

Projetos reais geralmente envolvem múltiplos desenvolvedores trabalhando juntos. Assim, eles precisam de um sistema de controle de versão como o Git para garantir que não haja conflitos de código entre eles.

Além disso, os requisitos em projetos desse tipo mudam com frequência. Um sistema de controle de versão permite que os desenvolvedores revertam alterações e voltem a versões anteriores do código.

O sistema de branches (ramificações) do Git permite que os desenvolvedores trabalhem individualmente em tarefas específicas (por exemplo: Uma branch → Uma tarefa ou Uma branch → Um desenvolvedor). Basicamente, pense no Git como um pequeno software que gerencia sua base de código, se você for um desenvolvedor.



## `Diferença entre Git e GitHub`

**Git:** Git é um sistema de controle de versão distribuído para rastrear mudanças no código-fonte durante o desenvolvimento de software. Ele é projetado para coordenar o trabalho entre programadores, mas pode ser usado para controlar alterações em qualquer conjunto de arquivos. Seus objetivos incluem velocidade, integridade de dados e suporte a fluxos de trabalho distribuídos e não lineares.

**GitHub:** GitHub é um serviço web de hospedagem de repositórios Git, que oferece todas as funcionalidades de controle de revisão distribuído e gerenciamento de código-fonte do Git, além de recursos próprios.


Git é um software.
GitHub é um serviço.            

Git é uma ferramenta de linha de comando.
GitHub é uma interface gráfica baseada na web.

Git é instalado localmente no sistema.
GitHub é hospedado na web.

Git é mantido pela comunidade Linux.
GitHub é mantido pela Microsoft.

Git foca em controle de versão e compartilhamento de código.
GitHub foca em hospedagem centralizada de código-fonte.

Git é um sistema de controle de versão para gerenciar o histórico do código-fonte.
GitHub é um serviço de hospedagem para repositórios Git.

Git foi lançado em 2005.
GitHub foi lançado em 2008.

Git tem licença open-source.
GitHub oferece planos gratuitos e pagos.

Git requer pouca configuração de ferramentas externas.
GitHub possui um marketplace ativo para integração de ferramentas.

Git fornece uma interface gráfica chamada Git Gui.
GitHub fornece uma interface gráfica chamada GitHub Desktop.

Git compete com CVS, Subversion, Mercurial, etc.
GitHub compete com GitLab, Bitbucket, AWS CodeCommit, Azure DevOps Server, etc.ddsa
## `O que é Controle de Versão`

Controle de versão é um sistema que registra alterações em um arquivo ou conjunto de arquivos ao longo do tempo, permitindo que você recupere versões específicas posteriormente. Nos exemplos deste material, você usará código-fonte como os arquivos controlados por versão, embora na prática isso possa ser feito com quase qualquer tipo de arquivo no computador.

Se você é designer gráfico ou web e quer manter todas as versões de uma imagem ou layout, um Sistema de Controle de Versão (VCS) é uma ferramenta extremamente útil. Ele permite reverter arquivos selecionados a um estado anterior, reverter todo o projeto a um estado anterior, comparar mudanças ao longo do tempo, ver quem modificou algo que está causando problemas, quem introduziu um erro e quando, entre outras coisas. Usar um VCS geralmente significa que, se algo der errado ou arquivos forem perdidos, você pode recuperá-los com facilidade. Além disso, tudo isso vem com um custo operacional muito baixo.

Uma das ferramentas de VCS mais populares foi um sistema chamado RCS, que ainda é distribuído com muitos computadores atualmente. O RCS funciona armazenando conjuntos de alterações (ou seja, as diferenças entre arquivos) em um formato especial no disco; ele pode então recriar como qualquer arquivo era em um momento específico somando todos os patches.

---

## `Problemas resolvidos pelo Git`

### **Editar uma mensagem de commit**

Às vezes, ao escrever a mensagem do commit, cometemos um erro de digitação. Os comandos a seguir podem ser usados para corrigir isso. Lembre-se de que o comando abaixo cria um novo commit, então evite usar `--amend` para modificar commits que já foram enviados para um repositório central.

```
git commit --amend
git commit --amend -m "Nova mensagem"
```

Se você esquecer de adicionar um arquivo com `git add`, basta adicioná-lo e emendar o commit anterior:

```
git add nome_do_arquivo_esquecido
git commit --amend
```

---

### **Desfazer commits locais**

Às vezes percebemos que houve um erro após alguns commits já terem sido feitos localmente:

```
git reset HEAD~2
git reset --hard HEAD~2
```

---

### **Remover um arquivo do Git sem removê-lo do sistema de arquivos**

Se você não tomar cuidado, pode acabar adicionando arquivos desnecessários com `git add`.

Se usar `git rm`, o arquivo será removido tanto da área de staging quanto do sistema de arquivos.

```
git reset nome_do_arquivo
echo nome_do_arquivo >> .gitignore
```

---

### **Reverter commits já enviados**

Às vezes commits com erros acabam indo para o repositório central mesmo após o uso de `amend` e `rebase`. Nestes casos, use os comandos abaixo:

```
git revert c761f5c
git revert HEAD^
git revert develop~4..develop~2
```

Se não quiser criar commits adicionais de reversão, mas apenas aplicar as mudanças no diretório de trabalho, use a opção `--no-commit` ou `-n`:

```
git revert -n HEAD
```

---

### **Evitar conflitos de merge repetidos**

Corrigir conflitos de merge repetidamente é bem irritante. Suponha que sua equipe esteja trabalhando em várias branches de funcionalidades ao mesmo tempo. Agora você quer fazer o merge de todas elas. Surgem vários conflitos que você resolve. Mas descobre que uma das branches ainda não está pronta, então desfaz o merge. Dias depois, quando a branch estiver pronta, você faz o merge de novo. Graças ao registro de resoluções, você não precisará resolver os mesmos conflitos novamente.

```
git config --global rerere.enabled true
```

---

### **Encontrar o commit que quebrou algo após um merge**

Às vezes é necessário encontrar o commit que alterou o projeto de forma errada. Esse commit pode ser difícil de identificar, o que consome muito tempo. O Git tem um método para encontrar o commit problemático após um merge:

```
git bisect start
git bisect bad
git bisect good revisão

Agora o git vai automaticamente fazer checkout de uma revisão intermediária entre as versões conhecidas como "boa" e "ruim":
git bisect good
git bisect bad
```



## `Breve história do Git`

Git é um software de controle de versão gratuito e de código aberto. Foi criado por Linus Torvalds em 2005. Esta ferramenta foi inicialmente desenvolvida para permitir o trabalho colaborativo de vários desenvolvedores no núcleo (kernel) do Linux.

Basicamente, o Git é um rastreador de conteúdo. Ele pode ser usado para armazenar qualquer tipo de conteúdo — e é mais comumente usado para armazenar código por conta dos recursos adicionais que oferece.

Projetos reais geralmente envolvem múltiplos desenvolvedores trabalhando juntos. Assim, eles precisam de um sistema de controle de versão como o Git para garantir que não haja conflitos de código entre eles.

Além disso, os requisitos em projetos desse tipo mudam com frequência. Um sistema de controle de versão permite que os desenvolvedores revertam alterações e voltem a versões anteriores do código.

O sistema de branches (ramificações) do Git permite que os desenvolvedores trabalhem individualmente em tarefas específicas (por exemplo: Uma branch → Uma tarefa ou Uma branch → Um desenvolvedor). Basicamente, pense no Git como um pequeno software que gerencia sua base de código, se você for um desenvolvedor.



## `Diferença entre Git e GitHub`

**Git:** Git é um sistema de controle de versão distribuído para rastrear mudanças no código-fonte durante o desenvolvimento de software. Ele é projetado para coordenar o trabalho entre programadores, mas pode ser usado para controlar alterações em qualquer conjunto de arquivos. Seus objetivos incluem velocidade, integridade de dados e suporte a fluxos de trabalho distribuídos e não lineares.

**GitHub:** GitHub é um serviço web de hospedagem de repositórios Git, que oferece todas as funcionalidades de controle de revisão distribuído e gerenciamento de código-fonte do Git, além de recursos próprios.


Git é um software.
GitHub é um serviço.            

Git é uma ferramenta de linha de comando.
GitHub é uma interface gráfica baseada na web.

Git é instalado localmente no sistema.
GitHub é hospedado na web.

Git é mantido pela comunidade Linux.
GitHub é mantido pela Microsoft.

Git foca em controle de versão e compartilhamento de código.
GitHub foca em hospedagem centralizada de código-fonte.

Git é um sistema de controle de versão para gerenciar o histórico do código-fonte.
GitHub é um serviço de hospedagem para repositórios Git.

Git foi lançado em 2005.
GitHub foi lançado em 2008.

Git tem licença open-source.
GitHub oferece planos gratuitos e pagos.

Git requer pouca configuração de ferramentas externas.
GitHub possui um marketplace ativo para integração de ferramentas.

Git fornece uma interface gráfica chamada Git Gui.
GitHub fornece uma interface gráfica chamada GitHub Desktop.

Git compete com CVS, Subversion, Mercurial, etc.
GitHub compete com GitLab, Bitbucket, AWS CodeCommit, Azure DevOps Server, etc.## `O que é Controle de Versão`

Controle de versão é um sistema que registra alterações em um arquivo ou conjunto de arquivos ao longo do tempo, permitindo que você recupere versões específicas posteriormente. Nos exemplos deste material, você usará código-fonte como os arquivos controlados por versão, embora na prática isso possa ser feito com quase qualquer tipo de arquivo no computador.

Se você é designer gráfico ou web e quer manter todas as versões de uma imagem ou layout, um Sistema de Controle de Versão (VCS) é uma ferramenta extremamente útil. Ele permite reverter arquivos selecionados a um estado anterior, reverter todo o projeto a um estado anterior, comparar mudanças ao longo do tempo, ver quem modificou algo que está causando problemas, quem introduziu um erro e quando, entre outras coisas. Usar um VCS geralmente significa que, se algo der errado ou arquivos forem perdidos, você pode recuperá-los com facilidade. Além disso, tudo isso vem com um custo operacional muito baixo.

Uma das ferramentas de VCS mais populares foi um sistema chamado RCS, que ainda é distribuído com muitos computadores atualmente. O RCS funciona armazenando conjuntos de alterações (ou seja, as diferenças entre arquivos) em um formato especial no disco; ele pode então recriar como qualquer arquivo era em um momento específico somando todos os patches.

---

## `Problemas resolvidos pelo Git`

### **Editar uma mensagem de commit**

Às vezes, ao escrever a mensagem do commit, cometemos um erro de digitação. Os comandos a seguir podem ser usados para corrigir isso. Lembre-se de que o comando abaixo cria um novo commit, então evite usar `--amend` para modificar commits que já foram enviados para um repositório central.

```
git commit --amend
git commit --amend -m "Nova mensagem"
```

Se você esquecer de adicionar um arquivo com `git add`, basta adicioná-lo e emendar o commit anterior:

```
git add nome_do_arquivo_esquecido
git commit --amend
```

---

### **Desfazer commits locais**

Às vezes percebemos que houve um erro após alguns commits já terem sido feitos localmente:

```
git reset HEAD~2
git reset --hard HEAD~2
```

---

### **Remover um arquivo do Git sem removê-lo do sistema de arquivos**

Se você não tomar cuidado, pode acabar adicionando arquivos desnecessários com `git add`.

Se usar `git rm`, o arquivo será removido tanto da área de staging quanto do sistema de arquivos.

```
git reset nome_do_arquivo
echo nome_do_arquivo >> .gitignore
```

---

### **Reverter commits já enviados**

Às vezes commits com erros acabam indo para o repositório central mesmo após o uso de `amend` e `rebase`. Nestes casos, use os comandos abaixo:

```
git revert c761f5c
git revert HEAD^
git revert develop~4..develop~2
```

Se não quiser criar commits adicionais de reversão, mas apenas aplicar as mudanças no diretório de trabalho, use a opção `--no-commit` ou `-n`:

```
git revert -n HEAD
```

---

### **Evitar conflitos de merge repetidos**

Corrigir conflitos de merge repetidamente é bem irritante. Suponha que sua equipe esteja trabalhando em várias branches de funcionalidades ao mesmo tempo. Agora você quer fazer o merge de todas elas. Surgem vários conflitos que você resolve. Mas descobre que uma das branches ainda não está pronta, então desfaz o merge. Dias depois, quando a branch estiver pronta, você faz o merge de novo. Graças ao registro de resoluções, você não precisará resolver os mesmos conflitos novamente.

```
git config --global rerere.enabled true
```

---

### **Encontrar o commit que quebrou algo após um merge**

Às vezes é necessário encontrar o commit que alterou o projeto de forma errada. Esse commit pode ser difícil de identificar, o que consome muito tempo. O Git tem um método para encontrar o commit problemático após um merge:

```
git bisect start
git bisect bad
git bisect good revisão

Agora o git vai automaticamente fazer checkout de uma revisão intermediária entre as versões conhecidas como "boa" e "ruim":
git bisect good
git bisect bad
```



## `Breve história do Git`

Git é um software de controle de versão gratuito e de código aberto. Foi criado por Linus Torvalds em 2005. Esta ferramenta foi inicialmente desenvolvida para permitir o trabalho colaborativo de vários desenvolvedores no núcleo (kernel) do Linux.

Basicamente, o Git é um rastreador de conteúdo. Ele pode ser usado para armazenar qualquer tipo de conteúdo — e é mais comumente usado para armazenar código por conta dos recursos adicionais que oferece.

Projetos reais geralmente envolvem múltiplos desenvolvedores trabalhando juntos. Assim, eles precisam de um sistema de controle de versão como o Git para garantir que não haja conflitos de código entre eles.

Além disso, os requisitos em projetos desse tipo mudam com frequência. Um sistema de controle de versão permite que os desenvolvedores revertam alterações e voltem a versões anteriores do código.

O sistema de branches (ramificações) do Git permite que os desenvolvedores trabalhem individualmente em tarefas específicas (por exemplo: Uma branch → Uma tarefa ou Uma branch → Um desenvolvedor). Basicamente, pense no Git como um pequeno software que gerencia sua base de código, se você for um desenvolvedor.



## `Diferença entre Git e GitHub`

**Git:** Git é um sistema de controle de versão distribuído para rastrear mudanças no código-fonte durante o desenvolvimento de software. Ele é projetado para coordenar o trabalho entre programadores, mas pode ser usado para controlar alterações em qualquer conjunto de arquivos. Seus objetivos incluem velocidade, integridade de dados e suporte a fluxos de trabalho distribuídos e não lineares.

**GitHub:** GitHub é um serviço web de hospedagem de repositórios Git, que oferece todas as funcionalidades de controle de revisão distribuído e gerenciamento de código-fonte do Git, além de recursos próprios.


Git é um software.
GitHub é um serviço.            

Git é uma ferramenta de linha de comando.
GitHub é uma interface gráfica baseada na web.

Git é instalado localmente no sistema.
GitHub é hospedado na web.

Git é mantido pela comunidade Linux.
GitHub é mantido pela Microsoft.

Git foca em controle de versão e compartilhamento de código.
GitHub foca em hospedagem centralizada de código-fonte.

Git é um sistema de controle de versão para gerenciar o histórico do código-fonte.
GitHub é um serviço de hospedagem para repositórios Git.

Git foi lançado em 2005.
GitHub foi lançado em 2008.

Git tem licença open-source.
GitHub oferece planos gratuitos e pagos.

Git requer pouca configuração de ferramentas externas.
GitHub possui um marketplace ativo para integração de ferramentas.

Git fornece uma interface gráfica chamada Git Gui.
GitHub fornece uma interface gráfica chamada GitHub Desktop.

Git compete com CVS, Subversion, Mercurial, etc.
GitHub compete com GitLab, Bitbucket, AWS CodeCommit, Azure DevOps Server, etc.dasdsad

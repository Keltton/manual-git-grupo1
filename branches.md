O que é um "branch" no Git?
💡 Conceito:
Um branch (ou “ramo”) no Git representa uma linha separada de desenvolvimento dentro do seu repositório. Ele permite que você trabalhe em novas funcionalidades ou correções sem afetar diretamente o código principal.

🧠 Por que usar branches?
Separar desenvolvimento de funcionalidades (feature)

Corrigir bugs sem atrapalhar o que está em produção

Trabalhar em paralelo com outros desenvolvedores

Testar mudanças arriscadas de forma isolada

🔧 Comandos mais usados com git branch
1. git branch
Mostra a lista de branches existentes:

bash
Copiar
Editar
git branch
2. git branch nome-do-branch
Cria um novo branch:

bash
Copiar
Editar
git branch nova-funcionalidade
Isso só cria, mas não muda para ele ainda.

3. git checkout nome-do-branch
Troca para um branch existente:

bash
Copiar
Editar
git checkout nova-funcionalidade
4. git checkout -b nome-do-branch
Atalho para criar e já mudar para o branch:

bash
Copiar
Editar
git checkout -b nova-funcionalidade
5. git merge nome-do-branch
Mescla um branch com o atual:

bash
Copiar
Editar
git checkout main
git merge nova-funcionalidade
6. git branch -d nome-do-branch
Deleta um branch (após mesclado):

bash
Copiar
Editar
git branch -d nova-funcionalidade
Se quiser forçar a exclusão (sem merge), use -D.

🗂️ Exemplo prático completo
bash
Copiar
Editar
# 1. Verifica em qual branch estou
git branch

# 2. Cria um novo branch chamado "login"
git branch login

# 3. Muda para o branch "login"
git checkout login

# 4. Faz mudanças no código e realiza commits
git add .
git commit -m "Implementa tela de login"

# 5. Volta para o branch principal
git checkout main

# 6. Mescla o branch login com o main
git merge login

# 7. Deleta o branch login (opcional)
git branch -d login
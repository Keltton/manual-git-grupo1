# Criar Conta no GitHub

- Acesse: https://github.com
- Clique em Sign up.

Preencha:
- Nome de usuário
- E-mail
- Senha

Siga o processo de verificação.
Escolha um plano (pode ser o gratuito).
Confirme o e-mail recebido.

# Criar Repositório Remoto

- Faça login no GitHub.

- Vá em "Your repositories" -> New.

Preencha:
- Nome do repositório
- Descrição
- Público ou privado
- Marque para adicionar um README.md
- Clique em Create repository.

# Clonar, Push e Pull

- Clonar o repositório
 
No terminal:

- git clone https://github.com/usuario/nome-repositorio.git
- cd nome-repositorio
- Adicionar arquivos e enviar (push)

- git add .
- git commit -m "Minha primeira modificação"
- git push origin main

# Atualizar o repositório local (pull)

- git pull origin main

# Pull Requests e Revisão de Código
- Criar um branch novo

- git checkout -b minha-feature
- Faça alterações, commit e push

- git add .
- git commit -m "Adiciona minha feature"
- git push origin minha-feature
- Criar Pull Request (PR)
- No GitHub, vá para o repositório.

- Clique em "Compare & pull request".

- Adicione título e descrição do que foi feito.

- Clique em "Create pull request".

# Revisão de código

- Outros membros do time podem comentar diretamente nas linhas do código.

- Após aprovação, alguém pode clicar em "Merge pull request" para mesclar.

# Dica de Fluxo de Trabalho em Equipe

- Cada dev cria branchs por tarefa.
- Após concluir, faz PR.
- Outro membro revisa.
- Após aprovação, o PR é mesclado no main.
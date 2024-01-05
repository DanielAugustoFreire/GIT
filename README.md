# 1️⃣ Manipular Arquivos de texto - exemplos com .gitignore

O arquivo `.gitignore` é usado para especificar arquivos e pastas que devem ser ignorados pelo Git. Isso é útil para evitar que arquivos temporários, arquivos de compilação ou arquivos sensíveis sejam incluídos no repositório.

## Exemplo Básico

Se precisamos ignorar uma pasta, por exemplo `para-ser-ignorada/`, podemos adicionar a seguinte linha ao `.gitignore`:

#### Usando echo:

```
echo para-ser-ignorada/ > .gitignore

```
---
#### Usando printf:

```
printf "para-ser-ignorada" > .gitignore

```
---
#### Usando cat:
```
cat > .gitignore
```
Isso permitirá que você insira manualmente o novo conteúdo no terminal. Pressione **Ctrl + D** quando terminar de inserir o texto.
#

# 2️⃣  Restaurar arquivos para o ultimo commit

```
git restore README.md
```
Exemplo restaurando do arquivo README.md

#### ⚠Atencao: 
- Caso tenha realizado alterações localmente e utilize este comando, elas serão excluídas e substituídas pelo conteúdo do commit anterior.
---
# 3️⃣ Mudar os comentarios do commit

- Digamos que voce tem o seguinte git log: 

Danie@DESKTOP-CER4OAS MINGW64 /c/DOI/dio-git-resumos (main)
$ `git log`
```

    commit b5d5cb1de721e48371fd46af456db1d9d728cfa5 (HEAD -> main)
    Author: DanielAugustoFreire <danielaugustosant@hotmail.com>
    Date:   Tue Jan 2 11:19:29 2024 -0300

        segundo commit
```

Para mudar o `segundo commit` pode-se utilizar o seguinte comando: 
```
    git commit --amend -m "2o commit, adicionado tal coisa"
```
OUTPUT:

Danie@DESKTOP-CER4OAS MINGW64 /c/DOI/dio-git-resumos (main)
$ `git log`

```
commit aec8df26dfe41d391ddf29effacdc7bd5cb6e02e (HEAD -> main)
Author: DanielAugustoFreire <danielaugustosant@hotmail.com>
Date:   Tue Jan 2 11:19:29 2024 -0300

    2o commit, adicionado tal coisa
```

# 4️⃣ Git Reset:
O comando `git reset` é uma ferramenta poderosa no Git que é usada para modificar o estado do seu repositório. Vamos explorar as opções e os conceitos associados mais detalhadamente.

#### Mais Utilizados 

- Soft Reset.
- Mixed Reset (default).
- Hard Reset.

# 🍦 Soft Reset: 
O Git move o ponteiro da branch para o commit especificado, mantendo as alterações no seu diretório de trabalho e as mantendo na área de staging (também conhecida como índice). Isso significa que todas as alterações que estavam presentes no commit especificado agora estão na área de staging e você pode criar um novo commit com essas alterações, se desejar.

---
-
-
-
GIT LOG:

commit 10b981e9df93295d5e24d681ca20ebae999a5c5f (HEAD -> main)
Author: DanielAugustoFreire <danielaugustosant@hotmail.com>
Date:   Wed Jan 3 15:26:29 2024 -0300

Segundo Commit

commit 510d10bca6158c284d814ab9ace2ebbf445f435c
Author: DanielAugustoFreire <danielaugustosant@hotmail.com>
Date:   Tue Jan 2 22:11:10 2024 -0300

Primeiro Commit


-
-
-
```
git reset --soft 510d10bca6158c284d814ab9ace2ebbf445f435c
```

Depois desse comando o branch vai para o commit `Primeiro Commit`, mas as alterações que foram feitas no Segundo Commit permanecem na area de staging, 
`Basicamente estao no add`.

#### Git Status:
Antes do Soft Reset:
```
On branch main
nothing to commit, working tree clean

```
Depois do Soft Reset:
```
On branch main
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
       	new file:   resumo/aula-01.md
       	new file:   resumo/aula-02.md



```
# 🍕 Mixed Reset:
Isso move as alterações de volta para o seu diretório de trabalho e remove as alterações da área de staging. Se você quiser fazer alterações diferentes antes de confirmar novamente, isso é útil.

Levando em consideracao o git log de antes, usando este comando: 
```
    git reset 510d10bca6158c284d814ab9ace2ebbf445f435c

    ||

    git reset --mixed 510d10bca6158c284d814ab9ace2ebbf445f435c
```

Depois desse comando o branch vai para o commit `Primeiro Commit`, mas as alterações que foram feitas no Segundo Commit **NAO** permanecem na area de staging, 
`Basicamente Sao Untracked Files`.

#### Git Status:
Antes do Soft Reset:
```
On branch main
nothing to commit, working tree clean

```
Depois do Soft Reset:
```
On branch main
Untracked files:
  (use "git add <file>..." to include in what will be committed)
       	resumo/

nothing added to commit but untracked files present (use "git add" to track)

```

# 💪 HARD Reset:
O git reset --hard é geralmente utilizado quando você deseja descartar completamente todas as alterações locais não confirmadas e redefinir seu repositório para um estado anterior na história.

Levando em consideracao o git log de antes, usando este comando: 
```
    git reset --hard 510d10bca6158c284d814ab9ace2ebbf445f435c

```
Todas as alterações no diretório de trabalho e na área de staging (índice) são removidas e substituídas pelo conteúdo do commit especificado. Isso significa que as alterações não confirmadas são permanentemente descartadas.

#### Git Status:
Antes do Soft Reset:
```
On branch main
nothing to commit, working tree clean

```
Depois do Soft Reset:
```
On branch main
nothing to commit, working tree clean

```
O HARD reset apaga tudo que nao estiver no commit especificado, entao se tiver coisas importantes evite usar ele.
# 5️⃣ Enviando e Baixando Alteracoes com o repositorio Remoto

#### Conectar seu repositorio local com o repositorio remoto:

    git remote add origin https://github.com/DanielAugustoFreire/git-testando.git

#### Enviar para o repositorio remoto: GIT PUSH

O comando git push é usado para enviar as alterações locais do seu repositório Git para um repositório remoto. Isso é útil quando você fez modificações em seu código local e deseja atualizar o repositório remoto com essas alterações. O formato básico do comando é o seguinte:

Exemplo:

    git push -u origin main

## 🛑Para remover um repositório remoto 
Em um ambiente Bash, você pode usar o comando git remote rm. Aqui está um exemplo de como você pode fazer isso:

    git remote rm <nome_do_repositorio_remoto>

Substitua <nome_do_repositorio_remoto> pelo nome do repositório remoto que você deseja remover. Se você não souber o nome do repositório remoto, pode usar o comando git remote -v para listar todos os repositórios remotos associados ao seu repositório local.

Se voce tiver um repositorio chamado origin

    git remote rm origin

<<<<<<< HEAD
# 6️⃣Branch
Um branch no Git é simplesmente um ponteiro móvel para um desses commits. O nome do branch padrão no Git é master. Conforme você começa a fazer commits, você recebe um branch master que aponta para o último commit que você fez. Cada vez que você faz um novo commit, ele avança automaticamente.

#### Criando uma Branch

    git checkout -b nova_branch

.

    git branch nova_branch

`git branch [nome_da_branch]` apenas cria a branch, `git checkout -b [nome_da_branch]` cria a branch e muda para ela ao mesmo tempo. O uso de git checkout -b é mais conveniente quando você quer começar a trabalhar em uma nova branch imediatamente após criá-la.

# Alternando para uma branch existente
    git checkout [nome_da_branch_existente]
# Listar todas as branches locais
    git branch

# Listar todas as branches (locais e remotas)
    git branch -a
#Listar com o nome do commit
    git branch -v
=======
# 7️⃣ Git Pull e Git Push

O Git Pull e Git Push são comandos essenciais no Git, facilitando a colaboração eficiente em projetos versionados. 

## Git Pull

O `git pull` é utilizado para atualizar o repositório local com as alterações mais recentes do repositório remoto. Ele realiza duas operações principais:

1. **`git fetch`**: Obtém as alterações do repositório remoto, incluindo novas branches ou alterações em branches existentes, mas não aplica essas alterações ao seu código local.

2. **`git merge` ou `git rebase`**: Combina as alterações recuperadas do repositório remoto com o seu código local. Pode criar um commit de merge ou reescrever o histórico usando rebase, dependendo da configuração e do comando específico utilizado.

Exemplo de uso:
```bash
git pull [repositório_remoto] [branch]
```
## Git Push

O git push é usado para enviar suas alterações locais para o repositório remoto. Ele envia commits locais para uma branch específica no repositório remoto.

    git push [repositório_remoto] [branch_local]

Antes de executar o git push, é importante garantir que seu repositório local esteja sincronizado com o repositório remoto. Use git pull para obter as alterações mais recentes antes de enviar suas próprias alterações.

Ambos os comandos são fundamentais para facilitar o trabalho colaborativo em projetos Git, permitindo que diferentes desenvolvedores compartilhem e integrem suas alterações de forma eficiente.


>>>>>>> 599436e0c871d18aa4d8cde3ffdd485bfbc77a4f

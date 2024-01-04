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



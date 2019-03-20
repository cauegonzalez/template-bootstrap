# Tutorial Git - Básico

Realizar configurações globais (executado apenas uma vez)  
`git config --global user.name "Nome Usuário"`  
`git config --global user.email "email.usuario@gdax.com.br"`  
`git config --global color.ui true`  

Leitura recomendada: https://git-scm.com/book/pt-br/v1/Primeiros-passos-No%C3%A7%C3%B5es-B%C3%A1sicas-de-Git

No git existem 3 estágios: `untracked files`, `staging` e `commited files`

#### Primeiro estágio
Untracked files - são arquivos com alterações ainda não adicionadas ao git. Acontece com arquivos novos e/ou modificados. Quando executado o `git status` estes arquivos são apresentados na cor VERMELHA.
#### Segundo estágio
Staging - arquivos já adicionados ao git pelo comando `git add` e então prontos para serem commitados. Quando executado o `git status` estes arquivos são apresentados na cor VERDE.
#### Terceiro estágio
Commited files - são arquivos já commitados. Estes arquivos já estão sob o controle de versão mas apenas na máquina em que foram commitados. Quando executado o `git status` estes arquivos não são apresentados, mas sim uma mensagem de que nada precisa ser commitado e então deve-se realizar o **push**.

## Comandos dia a dia
`git pull` Atualiza os arquivos no branch atual, ideal utilizar sempre que for iniciar uma nova demanda, e antes subir qualquer atualização.

`git checkout -b nomeDoBranch` Cria um novo branch e troca para mesmo. Sempre que for realizar uma nova demanda é extremamente recomendado criar um novo branch.

`git status` Comando utilizado para verificar o status do versionamento, mostrando os arquivos modificados. 

`git add .` Adiciona todos os arquivos/diretórios modificados para etapa staging area onde estarão prontos para realizar o commit.

`git add meuArquitoDiretorio` Adiciona o arquivo modificado para etapa staging area estando pronto para realizar o commit.

`git commit -m "Mensagem do commit"` Consolida as alterações que foram adicionadas na staging area enviando para para o seu repositório local, com uma descrição.

`git push origin nomeDoBranch` Consolida o commit realizado enviando as alterações para o repositório.

`git checkout nomeDoBranch` Altera o branch atual.

## Lista de comandos úteis
1. Comando utilizado para inicializar um repositório local dentro do diretório atual:

    ```  
    git init 
    ``` 
1. Comando utilizado para verificar o status do versionamento:

    ``` 
    git status
    ``` 
1. Comando para adicionar arquivos para o git:

    ``` 
    git add <nome-do-arquivo>
    ``` 
      1. Todos os arquivos que precisarem ser commitados devem antes serem adicionados
      1. Para adicionar todos os arquivos do primeiro estágio pode-se utilizar o comando `git add .`
1. Comando para commitar os arquivos adicionados ao *staging*:

    ``` 
    git commit -m "Mensagem do commit"
    ``` 
1. Comando para mostrar todas as diferenças de cada arquivo:

    ``` 
    git log -p
    ``` 
1. Mostra as últimas 2 diferenças de cada arquivo:

    ``` 
    git log -p -2
    ``` 
1. Comando para mostrar estatísticas (resumo do que foi alterado):

    ``` 
    git log --stat
    ``` 
1. Comando para mostrar cada alteração em uma linha:

    ``` 
    git log --pretty=oneline
    ``` 
1. Comando para mostrar pedaço do hash, autor, hora, descrição:

    ``` 
    git log --pretty=format:"%h - %an, %ar : %s"
    ``` 
1. Comando para mostrar informações dos últimos 2 dias:

    ``` 
    git log --since=2.days
    ``` 
    > Nota: é necessário criar no git um arquivo chamado `.gitignore`. Este arquivo deve ser incluído ao controle de versão e deve conter uma linha para cada item que deve ser ignorado. 

1. Comando que retira o arquivo adicionado, voltando-o para o estágio *untracked*:

    ```
    git reset HEAD nomeDoArquivo.txt
    ``` 

1. Comando que volta o arquivo para a versão do hash informado:

    ```
    git checkout <trecho do hash>
    ```

1. Comando que volta a quantidade de commits apresentada após o til:

    ```
    git reset HEAD~1
    ```
1. Comando que volta a quantidade de commits apresentada após o til, mas deixa os arquivos com suas alterações prontos para commitar novamente:

    ```
    git reset HEAD~1 --soft
    ```
1. Comando que volta a quantidade de commits apresentada após o til e ignora todas as alterações realizadas:

    ```
    git reset HEAD~1 --hard
    ```
## Voltando ao estado original (equivalente ao *revert* do svn)
Imagine que você possui um arquivo no controle de versão chamado *exemplo.php* e depois de realizar diversas alterações nesse arquivo você precise desfazê-las:

    ```
    git checkout -- exemplo.php
    ```

## Branches
1. Comando para listar todos os branches marcanco com um asterisco em qual branch sua cópia está

    ``` 
    git branch
    ```
1. Comando para criar um branch a partir do branch atual chamado *nomeDoBranch* e já alterar para o branch criado

    ``` 
    git checkout -b nomeDoBranch
    ```
1. Comando para alterar para o branch *nomeDoBranch* (sem o **-b**)

    ``` 
    git checkout nomeDoBranch
    ```
1. Comando para realizar o merge entre o branch *nomeDoBranch* e o branch atual

    ``` 
    git merge nomeDoBranch
    ```
1. Comando para organizar os commits em ordem cronológica, trazendo tudo do *nomeDoBranch* para o branch atual

    ``` 
    git rebase nomeDoBranch
    ```

### Removendo um branch
Após desenvolver em um determinado branch, um merge com o branch principal é necessário. Após este merge ser realizado, o branch que foi utilizado somente para desenvolver aquela funcionalidade pode ser removido. Quando o merge já foi realizado, remover o branch não significa remover os commits realizados.

``` 
git branch -D nomeDoBranch 
``` 

## Observações
* Este é um gua básico

## Testes Desenvolvidos por [Leonardo Rohrbacher], [Matheus Duarte], [Khaue Souza]

# Calculadora JavaScript

A calculadora realiza **soma**, **subtração**, **multiplicação** e **divisão**.



1 - Como inicializar repositórios!
Primeiramente logar no seu git 
git config --global user.email "exemplo@exemplo.com"
Este comando é usado para criar um novo repositório GIT.
git init
crie uma cópia de trabalho em um repositório local executando o comando

git clone /caminho/para/o/repositório


2- Como fazer o primeiro commit em um projeto
Você pode enviar arquivos usando

git add <arquivo>
git add *

3- Como realizar commit de mudança
Voce pode enviar uma mensagem falando oque foi alterado no seu codigo ou arquivo novo

git commit -m "comentários das alterações"
Agora o arquivo é enviado para o HEAD, mas ainda não para o repositório remoto.

4- Como compartilhar suas mudanças com outras pessoas da equipe
Suas alterações agora estão no HEAD da sua cópia de trabalho local. Para enviar estas alterações ao seu repositório remoto, execute

git push origin "nomedoarquivo"

5- Como desfazer alterações
Para desfazer alterações em arquivos que vc ja escreveu basta fazer 

git checkout <nome do arquivo>
ele assim pegara o codigo do arquivo remoto e assim seu codigo customizado sera perdido

6-Como resolver conflitos de merge
O comando git merge é usado para mesclar uma ramificação no ramo ativo

git merge <branch-name>

7- Como usar branches
Voce pode transitar entre branchs fazendo o comando 

git checkout <nome da branch>
pode entrar nela e usar ela, sempre dando um

git pull origin <nome da branch>
para deixar ela atualizada com o remoto 

8- Como encontrar bugs
  
O comando git diff é usado para listar os conflitos. Para visualizar conflitos com o arquivo base, use

git diff --base <file-name>
O seguinte comando é usado para exibir os conflitos entre ramos about-to-be-merged antes de mesclá-los:

git diff <source-branch> <target-branch>
Para simplesmente listar todos os conflitos atuais, use:

git diff

A marcação é usada para marcar compromissos específicos com alças simples. Um exemplo pode ser:

git tag 1.1.0 <insert-commitID-here>

Executar o comando git log exibe uma lista de compromissos em uma ramificação, juntamente com os detalhes pertinentes. 
git log

Use busca binária para encontrar o commit que introduziu um bug
git-bisect 

Este comando usa um algoritmo de busca binária para descobrir qual commit no histórico do seu projeto introduziu um bug. Você o usa primeiro dizendo a ele um commit "ruim" que é conhecido por conter o bug, e um commit "bom" que é conhecido por existir antes do bug ser introduzido. Em seguida, git bisectescolhe um commit entre esses dois endpoints e pergunta se o commit selecionado é "bom" ou "ruim". Ele continua reduzindo o intervalo até encontrar o commit exato que introduziu a alteração.
Comandos básicos de bissecção: start, bad, good
Como exemplo, suponha que você esteja tentando encontrar o commit que quebrou um recurso que funcionava na versão v2.6.13-rc2do seu projeto. Você inicia uma sessão de bissecção da seguinte forma:

 git bisect start 
 git bisect bad # A versão atual é ruim 
 git bisect good v2.6.13-rc2 # v2.6.13-rc2 é conhecido por ser bom


Depois de especificar pelo menos um commit ruim e um bom, git bisectselecione um commit no meio desse intervalo de histórico, verifique-o e produza algo semelhante ao seguinte:

Bisecting: 675 revisões restantes para testar depois disso (aproximadamente 10 etapas)
Agora você deve compilar a versão com check-out e testá-la. Se essa versão funcionar corretamente, digite

git bisect bom
Se essa versão estiver quebrada, digite

git bisect ruim
Então git bisectvai responder com algo como

Bisecting: 337 revisões restantes para testar depois disso (aproximadamente 9 etapas)
Continue repetindo o processo: compile a árvore, teste-a e, dependendo se é boa ou ruim, execute git bisect goodou git bisect bad peça o próximo commit que precisa ser testado.
O comando git culpado é usado para examinar o conteúdo de um arquivo linha por linha e ver quando cada linha foi modificada pela última vez e quem foi o autor das modificações
git blame

9- Como escolher determinados commits
git cherry-pick [--edit] [-n] [-m <parent-number>] [-s] [-x] [--ff] [-S[<keyid>]] <commit>…​
git cherry-pick (--continue | --skip | --abort | --quit)


Os passos são bem simples, primeiro vá para a branch do seu colega

git checkout "Nome da branch do seu amigo"
Encontre o ID do commit dele, você pode fazer isso com o git log.

Só para ilustrar, eu usarei este ID para ficar mais fácil a explicação: “f13bd3c3531f26e805c606729857f39987a2420f”

Volte para a sua branch, e digite

git cherry-pick f13bd3c3531f26e805c606729857f39987a2420f
Pronto! Com isso, você copiou apenas o commit que você precisava, sem perder tempo. Por isso é importante trabalhar sempre fazendo pequenos commits.


Assim como em merges e rebase, em cherry pick também podem acontecer conflitos, e você irá resolve-los da mesma forma que um merge/rebase.

Você pode resolve-los usando uma interface gráfica, ou via terminal.

Pelo terminal, temos dois comandos: o continue que é para você executar depois que resolver o conflito no código.

git cherry-pick --continue
E temos o abort, para cancelar o cherry pick.

git cherry-pick --abort

Em síntese, esses são os comandos mais comuns que podem te ajudar:

-e : permite que você edite a mensagem do commit.
-x: adiciona uma mensagem no commit copiado avisando que ele é um cherry pick de um outro commit – “cherry picked from commit”.
–allow-empty: por padrão, o cherry-pick não permite commits em branco, com esse parâmetro, ele sobrescreve esse comportamento.
–allow-empty-message: quando o commit não tem um título, ele é barrado. Assim como no exemplo anterior, esse parâmetro sobrescreve o comportamento.

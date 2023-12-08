<h2>Git e GitHub: Compartilhando e colaborando em projetos</h2>

* Comandos Git:
    * `git config user.name ou user.email`: Visualiza qual é o nome ou email do usuário git atual. Para alterá-los, basta colocar a flag --config antes do `user.name` ou do `user.email`;
    
    * `git add .` : Adiciona todos os arquivos do diretório atual que foram modificados para stage (preparação para o commit);

    * `git commit -m "mensagem"`: Registra um versionamento (commit) do projeto com base nos arquivos que estavam preparados (stage);

    * `git branch -M \<nome_novo>`: Altera o nome da branch atual para o nome_novo;

    * `git remote add origin \<url_do_repositorio_remoto>`: Linka o repositório local com o remoto, podendo ser por HTTPS ou SSH (origin é o apelido padrão dado ao repositório remoto, para não precisar ficar escrevendo sua url toda hora).

    * `git remote -v`: Mostra os repositórios que estão configurados para envio de commits (push) e de baixar commits (fetch).

    * `git push -u origin \<branch_desejada>`: Envia os commits salvos na branch atual para a branch remota main. Com a flag -u, se for somente escrito o comando _git push_, o git saberá que é para enviar os commits para a main remota automaticamente, sem a flag precisaria fazer essa indicação.

    * 

* Para o caso de SSH, é necessário configurar uma chave SSH para conectar um 'repo' remoto (GitHub) no local, deve-se seguir estes passos:
    1. Ir nas configurações de perfil no GitHub e ir em configurações
    2. Entrar na opção de Chaves SSH e GPG
    3. Solicitar a geração de uma chave, colocando o nome e o tipo de chave, que no caso é de autenticação
    4. Gerar uma chave através do comando `ssh-keygen -t ed25519 -C "email_cadastrado_no_Github"` (<a href="https://docs.github.com/pt/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent">Link para instruções</a>)
    5. Após seguir os passos necessários do comando, a chave estará localizada no arquivo com o nome definido na execução do comando ( o que você escreveu ou o que o comando definiu) dentro da pasta _C:\Users\Seu-Usuario\.ssh_.
        * Obs: Pode ser que se vc colocar o nome no arquivo da chave ela não apareça na pasta .ssh mas sim no diretório atual, então é só colocar sem nome msm para salvar na pasta .ssh (definindo assim o nome padrão)
    6. Das duas chaves que serão geradas, uma pública (.pub) e outra privada (sem extensão), iremos copiar o conteúdo do arquivo da chave pública e colar no campo de adição de chave do passo 3 e finalizar a criação da chave SSH no GitHub.
    7. Pronto! Agora é só alegria.

* <a href="https://www.alura.com.br/artigos/nova-exigencia-do-git-de-autenticacao-por-token-o-que-e-o-que-devo-fazer?_gl=1*1e2h0wz*_ga*MTA1MTcwOTE3My4xNjg4MTU1NjE5*_ga_1EPWSW3PCS*MTY5OTYyMzAzMS45MC4xLjE2OTk2MjMwNTUuMC4wLjA.*_fplc*M2dNQUswSGhqRW1RZlUzdnF2Sjg0MEdRUUNUV3ZNUVgzaVg4T0xpd1JxbmRPS2Z4OEIlMkJUT0tMVDhUJTJCemFWZVU2TjVpZSUyQk12cEp0dmNUblQxcUFBVFJQT3dkViUyQk1MVnJETER5RGs3bU5WTmRxRHdkU2JGckQlMkZCWmJ4TXVTZyUzRCUzRA..">Login por Token (HTTPS não é mais suportado?)</a>

* Existem boas práticas ao escrever mensagens de commit:
    * Manter no máximo 72 caracteres (caso a mensagem precise ser maior, pulamos para a próxima linha, mas mantendo os 72 caracteres em cada)

    * Uma recomendação é usar verbos no infinitivo, mostrando o que o commit atual irá fazer. Contudo, dependendo da cultura do lugar, a formatação poderá mudar, porém, o que prevalece é a mensagem estar clara e refletir o que foi feito de fato

    * Evitar colocar muitos detalhes técnicos na mensagem, pois isso além de deixá-la grande, tira o propósito do commit, que é apenas de trazer um resumão do que foi feito. Detalhes técnicos podem ser adicionados na documentação do projeto ou em comentários de código

* Commits devem ser realizados preferencialmente ao finalizar uma tarefa específica, seja consertar um bug ou incrementar uma novo passo de uma funcionalidade, sendo possível manter um rastreio claro do que foi feito. Deve-se evitar portanto modificações muito grandes ou pequenas demais, pois haverão pessoas (incluindo você) que irão ler as modificações do código futuramente. NUNCA SE DEVE DAR COMMIT DE CÓDIGO COM BUG.

* <a href="https://git-scm.com/book/pt-br/v2/Come%C3%A7ando-O-B%C3%A1sico-do-Git">Documentação oficial do Git</a>

* Para permitir que outras pessoas trabalhem em um repositório criado por mim, é necessário adicionar os colaboradores através de seu nome de usuário do GitHub.

* Caso a mudança realizada tenha sido feita por duas ou mais pessoas, podemos dar co-autoria para eles neste formato de mensagem de commit:

```git
$ git commit -m "Adicionar nova funcionalidade.
>
>
Co-authored-by: NOME <nome@email.com>
Co-authored-by: OUTRO-NOME <outro@email.com>"

# Fechar as aspas só depois do último nome
```
* <a href="https://www.alura.com.br/artigos/open-source-uma-breve-introducao">Como colaborar em projetos Open Source</a>

* Para sincronizar as mudanças do repositório remoto com o local (baixar as mudanças feitas), utilizamos o comando ```git pull```.

* Quando trabalhamos colaborativamente em um projeto, há a possibildade de ocorrerem **conflitos**. Os conflitos nada mais são que o choque entre duas mudanças (commits) que estariam sendo implementadas em uma mesma linha de um mesmo arquivo. Isso geralmente ocorre quando não se dá o ```git pull``` antes de começar a trabalhar em um arquivo, não atualizando o estado atual daquela branch antes de começar a trabalhar nela. Para resolver os conflitos, deve-se escolher qual informação prevalecerá entre os conflitos e dar um novo commit com as modificações feitas.

* <a src="https://jtemporal.com/resolvendo-conflitos/">Mais sobre conflitos no Git</a>

* É possível também de acontecer que um dev se arrependa da mudança que ele fez através de um commit. Como o git é um sistema de VERSIONAMENTO, é possível então VOLTAR à versão (commit) antes da mudança feita. Para isso, usamos ```git revert <id_do_commit_a_ser_revertido>```, onde será feito um NOVO COMMIT desfazendo as mudanças que o commit tal fez.

* Para apagar um commit do histórico, utilizamos o comando ```git reset --hard <id_do_commit_ANTERIOR>```. Este comando só é recomendado no âmbito do repositório local. Estes são os principais modos de _reset_ que podemos utilizar:
    * **--soft**: Isso deixa todos os seus arquivos alterados como "Changes to be committed" (volta para a fase de stage)
    * **--hard**: Isso reverte todas as mudanças feitas pelo commit, como se não tivesse acontecido nada.

* <a href="https://git-scm.com/docs/git-reset/pt_BR">Para saber mais sobre o ```git reset```</a>

* Para alterar a mensagem de um commit, podemos utilizar o comando ```git commit --amend -m "Nova mensagem de commit"```. Para alterar o conteúdo do commit em si, basta utilizar só até a flag _--amend_, já que este comando pega o último commit dado como referência

* <a src="https://www.alura.com.br/artigos/escrever-bom-readme">Dicas para escrever um bom README.md</a>

* É possível pedir para o Git ignorar certas pastas ou/e arquivos através de um arquivo chamado ```.gitignore```. O site gitignore.io gera um arquivo para ignorar arquivos derivados da tecnologia escolhida.

* A ferramenta _gist_ do GitHub serve para compartilhar trechos de código de um projeto, sem ter que compartilhá-lo por completo.

<h2>Git e Github: estratégias de ramificação, Conflitos e Pull Requests</h2>

* O que é Open Source? São projetos públicos nos quais permitem colaboração ed várias pessoas.

* As Issues são ferramentas interessantes dentro de um repositório, podendo ter várias utilidades, desde colocar histórias de usuário, épicos até sugestões de melhorias ou bugs relatados dentro do código. Quem irá dizer o propósito das issues do repositório serão os donos dele.

* Para se contribuir em um projeto Open Source deve-se:
    1. Escolher a issue na qual se deseja trabalhar
    
    2. Fazer um fork do projeto e cloná-lo (ou adicionar o remoto caso já exista um repositório local)

    3. Fazer as modificações desejadas e enviá-las ao seu repositorio forkado

    3.1. Compilar todas modificações (commits) em um só através do comando ```git rebase -i HEAD~<id_do_commit_anterior_a_modificacao>```

    3.2. Na janela de rebase, o _pick_ será o commit onde tudo será compactado e _s_ são os commits a serem compactados em um _pick_ do mais antigo estando em cima e o mais novo em baixo.

    3.3. Após isso, criar uma mensagem para o novo commit a ser feito.

    4. Criar um Pull Request para o repositório original, colocando uma descrição do que foi feito. Os donos deste repositório irão analisar a sua solução e aceitar ou não

* Existem outras plataformas de git, como GitLab e o BitBucket
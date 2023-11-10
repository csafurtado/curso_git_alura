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
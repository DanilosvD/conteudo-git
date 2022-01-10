# Git

## Ciclo de vida dos arquivos
   |                Tracked                   |
   |         ---                              |
   |            Arquivos que o git conhece    |
   
   Untracked  | Unmodified | Modified | Staged
   |---       |---         |----       |---
   Arq que o git não reconhece | Arq que o git conhece, mas não foi modificado | O git conhece e modificado | Esperando commit
   git add ----------|---------------------------|-------------------|--> Arquivo
   |                  | Arq modificado----------| git add -----------|--> Arquivo
   | Arquivo <--------| não modificado  e removido|                  |           
   | Arquivo <--------|---------------------------|------------------| git commit
   
   ***

## Criando chave SSH e Token

### Chave SSH

 1. Acessar o GitHub
    
    * Perfil/Setting(configuração)/ssh end gpg Keys/ New ssh Key
     > **Nota:** Aqui, pedirá o nome e a chave, que será criada no segundo passo.
 1. Acessar o Git Bash no seu computador
 
     * `ssh-keygen -t ed25519 -C "seu email"` 
     
          > ***obs:*** O "t" do comando é menúsculo e o "C" é maiúsculo.
      
      * `ssh-keygen -t rsa -b 4096 -C "seu email"`
      
          > ***obs:*** Esse comando é utilizado caso o primeiro não funcione. Devido a incompatibilidade de algumas máquinas com o primeiro comando, esse comando pode ser utilizado.
     
  > **Nota:** Esses comandos criam uma pasta no computador contendo duas chaves, uma pública e outra privada. Quando as chaves forem criadas, será pedido que crie uma senha(opcinal) para a chave ssh.
  
  3. Dentro da pasta criada
  
      * `cat numero da chave publica`
      
       > **Nota:** Digite o comando `cat` mais o número da chave pública. O número termina com **.pub**. Copia a chave e vai no GitHub **(no primeiro passo)** e colar a chave.
       
  4. Dentro da pasta criada
  
       * `eval $(ssh-agent -s)`
       
          > **Nota:** Aqui, será gerado o responsável por gerenciar a sua chave privada.
 
  5. Dentro da pasta criada
    
       * `ssh-add numero da chave privada`
       
          > **Nota:**  O comando `ssh-add` mais o número da chave. Esse é o camando utilizado para atribuir a chave privada ao agente.
    
    
 > **Nota:** Depois de feito tudo isso, lembre-se de na hora de clonar um repositório, não copiar o link **HTTP** e sim **SSH**.
 
 ***

### Token

 1. Acessar o GitHub
   
     * Perfil/Setting(configuração)/developer setting/ Personal access token/Generate new token
      
        > **Nota:** Pronto, token gerado. Agora sempre que for fazer um `push` ou `pull` deverá usar nome de usuário e o token. Lembrando que, quando for copiar o link  deverá copiar o link **HTTP**. E antes que eu esqueça, guardar o token em local seguro!
___

## Comandos Git

### Configuração

* `git config --goblal user.email` "email" 
* `git config --goblal user.name` "nome"
   
   * *Cria nome e email*
   
* `git config --goblal --unsert user.email` "email"
* `git config --goblal --unsert user.email` "nome" 

   * *Apaga nome e email*
   
* `git config --list` - *Lista todas as configurações*

___

### Inicia um repositório

* `git init` - *Inicia um repositório*
___

### Adiciona arquivos 

* `git add` - *Adiciona o arquivo para versionar*
* `git add*` - *Adiciona todos os arquivos para versinar*
___

### Puxar e Empurrar para o GitHub

* `git remote add origin "url"` - *Aponta o repositório local para o repositório remoto*
  > **Nota:** Se já estiver cadastrado a chave **ssh** na máquina a "url" copiada deve ser a **ssh** e não a  **http**. Mas se estiver utilizando o **token** aí sim, utiliza o **http**.  
* `git remote -v`- *Lista os repositórios remoto*
* `git push origin main`- *Empurra o repositório para o GitHub*
  > **Nota:** Caso sua _branch_ principal seja __master__ ela deve ser alterada para __main__. Desde agosto de 2021, o GitHub, adotou a _branch_ __main__ como a _branch_ principal. Se você for fazer um push com sua _branch_ __master__ para o GitHub vai haver conflito.
* `git pull origin main` - *Puxa do GitHub para sua máquina*
___

### Histórico de commit

* `git log` - *Histórico de commit*
* `git log --oneline`- * Histórico de commit em uma linha*

___
### Branch

* `git checkout -b ` - *___Checkout___* Move-se entre _branchs_
                       *___-b___* Indica em qual branch está e cria uma branch
                       
* `git marge` - *Junta as _branchs_, mas tem que eatá na branch principal*

* `git branch ` - *Verifica a quantidade de branch*
* `git branch -d ` - *Apaga a branch* 
* `git branc -m ` -  *Dá o nome da branch ou renomeia*
  >**Nota:** Para renomear, deve-se colocar o nome da branch atual entre aspas e depois o nome da nova branch.
 
 ___ 
 
 
 ### Salva arquivos e alterações 
  
* `git stash save  "nome da descrição"` - *Salva todas as alterações e arquivos dentro de um espaço, assim, fazendo com que esses arquivos e alterações não sejam salvos em outra branch*
* `git stash list`- *Lista todas as stash*
* `git stash pop "número do índeci"` - *Coloca os arquivos e alterações de volta na branch para que possa ser usados.*

___

### Apaga e Restaura commit

* `Git reset --soft "HEAD~1" ou "334bsd2"`- *Reverte o commit. Pode ser pelo HEARD~ ou sha1. Volta para o estado anterior ao commit. Quando fica verde.*
 
*  `Git reset --mixed` - *Reverte para o estado anterior ao add. quando fica vermelho. Pode passar um parâmetro, por exemplo, o HEARD~. Padrão do reset.*

* `Git reset --hard` - *Remove o conteúdo dentro do commit.*

* `Git revert` - *Cria um novo commit e reverte o commit indicado.*

___

## Cursos

 * Curso de Git com terminal básico [**Dio**](https://web.dio.me/course/introducao-ao-git-e-ao-github/learning/75b9fe49-6ed4-4480-83a7-7e37fc356aa9/?back=/browse)
 * Curso de Git sobre Branch [**Dio**](https://web.dio.me/course/trabalhando-com-branches-no-github/learning/32d05c5a-53b7-4f1d-a798-b9a8658240de/?back=/browse)
 * Curso de Git sem terminal com [**Gustavo Guanabara**](https://www.youtube.com/watch?v=xEKo29OWILE&list=PLHz_AreHm4dm7ZULPAmadvNhH6vk9oNZA)

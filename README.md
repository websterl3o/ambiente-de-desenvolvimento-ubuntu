## PHP
```bash
# O primeiro passo para instalar diferentes versões do PHP é adicionar o PPA mantido por Ondrej Surý no Ubuntu
sudo add-apt-repository ppa:ondrej/php

# Agora, é preciso que você atualize o sistema
sudo apt-get update

# Troque o *.* pela versão do PHP que você deseja. Exemplo: php7.2-fpm, php7.4-fpm...
sudo apt install php*.*-fpm
```

Finalmente, você pode verificar a versão do PHP usada no sistema
```bash
php -v
```

### Selecione a versão padrão do PHP
De forma interativa
```bash
sudo update-alternatives --config php
```

Você pode selecionar a versão padrão do PHP utilizando o comando update-alternatives, após fazer isso, rode o comando anterior para confirmar
```bash
# Selecione a versão padrão do PHP
sudo update-alternatives --set php /usr/bin/php*.*

# Desative a versão que estiver utilizando
sudo a2dismod php*.*

# Ative a nova versão
sudo a2enmod php*.*

# Reinicie o servidor nginx
sudo systemctl restart nginx
```

### Instalação de extensões
Para instalar qualquer módulo PHP, especifique a versão do PHP e use o recurso de auto-completar para visualizar todos o 
módulos disponíveis.

```bash
# Agora você pode instalar os módulos mais necessários, basta trocar a versão pela do PHP ou das versões que você quer instalar

sudo apt install openssl php7.2-curl php7.2-gd php7.2-imagick php7.2-json php7.2-mbstring php7.2-mcrypt php7.2-common php7.2-bcmath php7.2-xml php7.2-zip php7.2-mysql php7.2-intl php7.2-mongodb php7.2-gmp php7.2-soap

```

Para acessar a lista de extensões disponíveis: [Link](https://packages.ubuntu.com/focal/php/)

Para trabalhar com envio de arquivo para o verbo PUT HTTP:

[APFD](https://mdref.m6w6.name/apfd)

```bash
sudo apt install php-pear 

sudo apt install php*.*-dev

sudo pecl install apfd
```

## CS-FIXER
[https://cs.symfony.com/](https://cs.symfony.com/)

## MySQL
[https://www.digitalocean.com/community/tutorials/how-to-install-mysql-on-ubuntu-20-04-pt](https://www.digitalocean.com/community/tutorials/how-to-install-mysql-on-ubuntu-20-04-pt)

## MongoDB
Download
[https://docs.mongodb.com/manual/tutorial/install-mongodb-on-ubuntu/](https://docs.mongodb.com/manual/tutorial/install-mongodb-on-ubuntu/)

```bash
# Extensão do mongodb
sudo apt-get install php*.*-mongodb
```

#### MongoDB Compass
Ferramenta de gerenciamento de banco de dados mongodb
Download
[https://www.mongodb.com/try/download/compass](https://www.mongodb.com/try/download/compass)

## Redis
[https://www.digitalocean.com/community/tutorials/how-to-install-and-secure-redis-on-ubuntu-20-04-pt](https://www.digitalocean.com/community/tutorials/how-to-install-and-secure-redis-on-ubuntu-20-04-pt)

## Github
Debian/Ubuntu
É uma boa ideia verificar se você está executando a versão mais recente. Para fazer isso, navegue até a linha de comandos 
shell e execute o seguinte comando para garantir que tudo está up-to-date: `sudo apt-get update`.
Para instalar o Git, execute o seguinte comando: `sudo apt-get install git`.
Uma vez que a saída do comando foi concluída, você pode verificar a instalação digitando: `git version`.
Fedora
Os pacotes Git estão disponíveis usando `dnf`.
Para instalar o Git, navegue até a linha de comandos shell e execute o seguinte comando: `sudo dnf install git`.
Uma vez que a saída do comando foi concluída, você pode verificar a instalação digitando: `git version`.
Observação: você pode baixar as versões adequadas do Git e ler mais sobre como instalar em sistemas Linux específicos, 
como instalar o Git no Ubuntu ou Fedora, [na documentação do git-scm](https://git-scm.com/download/linux).

## Git CLI
Os pacotes baixados de https://cli.github.com ou de https://github.com/cli/cli/releases
são considerados binários oficiais. Nós nos concentramos em distribuições Linux populares 
e as seguintes arquiteturas de CPU: `i386`, `amd64`, `arm64`, `armhf`.

Outras fontes de instalação são mantidas pela comunidade e, portanto, podem estar atrasadas em nosso cronograma de lançamento.

## Fontes oficiais

### Debian, Ubuntu Linux, Raspberry Pi OS (apt)

Instalação

```bash
curl -fsSL https://cli.github.com/packages/githubcli-archive-keyring.gpg | sudo gpg --dearmor -o /usr/share/keyrings/githubcli-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/githubcli-archive-keyring.gpg] https://cli.github.com/packages stable main" | sudo tee /etc/apt/sources.list.d/github-cli.list > /dev/null
sudo apt update
sudo apt install gh
```

**Nota**: Se você receber o erro _"gpg: failed to start the dirmngr '/usr/bin/dirmngr': No such file or directory"_, tente instalar o `dirmngr` pacote: `sudo apt install dirmngr`.

Atualização

```bash
sudo apt update
sudo apt install gh
```

## Git — Como manter seu Fork Atualizado
```bash
# Liste os remotes do seu repositório
git remote -v

# Adicione o repositório original com o nome de upstream
git remote add upstream URL/SSH do repositório

# Liste novamente os remotes para ver se está correto
git remote -v

# Baixe os commits do repositório original, eles serão armazenados em uma branch local upstream/master
git fetch upstream

# Mude para a branch master
git checkout master

# Faça o merge das alterações do upstream/master no seu local master branch. Isso irá sincronizar as alterações do repositório original com o seu fork sem perder as alterações
git merge upstream/master
```

## Git — Fluxo
```bash
# Baixe os commits do repositório original, eles serão armazenados em uma branch local upstream/master
git fetch upstream master

# Mude para a branch master
git checkout master

# Faça o merge das alterações do upstream/master no seu local master branch. Isso irá sincronizar as alterações do repositório original com o seu fork sem perder as alterações
git merge upstream/master

# Sincronizar repositório
git pull upstream master

# Cria uma nova branch
git checkout -b name-branch

# Adiciona os arquivos modificados
git add -A

# Define mensagem do commit
git commit -m "Mensagem do commit"

# Enviar solicitação
git push --set-upstream origin name-branch
# git push origin name-branch
```

Caso seja solicitado para juntar os commits

```bash
# No lugar do 0 coloque o número de commits
git rebase -i HEAD~0
```

Para efetuar o squash, apenas edite a linha, alterando a palavra `pick` por `squash`:
_Caso tenha mais commits, você irá repetir o mesmo para os commits no qual você deseja fazer squash._

**Ao salvar a mensagem do commit, se você tentar dar push novamente para o seu fork, isso não irá funcionar e você receberá um erro.
O que acontece é que nós fizemos um rebase do branch e sua estrutura já não é mais a mesma do branch remoto em seu fork.
Neste caso, você deve forçar o push com a flag `-f`:**

```bash
git push -f origin name-branch
```

Pronto, nosso rebase com squash foi enviado com sucesso!

### Atualizando branch com novas alterações enquanto você trabalha em sua funcionalidade
Muitas vezes (a maioria das vezes), um projeto tem vários contribuidores que trabalham em várias funcionalidades diferentes.
É preciso então manter sua branch atualizada com a versão mais recente do repositório oficial. Fazemos isso através de rebase.
Suponha que você está trabalhando atualmente no branch feature/new-readme e percebeu que existem atualizações no branch master do repositório oficial, é bem simples de resolver basta executar:

```bash
git rebase -i upstream/master
```

### Atualizando seu repositório com as alterações mais recentes do repositório principal
Esta é a última etapa de um longo ciclo de contribuições. Ao ter seu pull request aceito, ou ao perceber que mais contribuições foram feitas no repositório original, é preciso que você mantenha o seu repositório de Fork e também seu repositório local, para que você sempre tenha features baseadas na versão mais recente do branch master do repositório original.
E é aí que finalmente nós utilizamos do recurso de url remota do git, neste caso definimos `origin` e `upstream`.
Para pegar as alterações mais recentes, certifique-se que localmente você está no branch master e execute o comando:

```bash
git pull upstream master
```

Pronto! Agora você tem o seu repositório local atualizado com a versão mais recente do repositório original.
Agora é a hora de atualizar o seu repositório Fork, executando o comando:

```bash
git push origin master
```

### Reverter um merge
Assumindo que o merge não gerou nenhum commit (já que há conflitos). Na raiz do seu repositório, digite
```bash
git reset
```

Isso irá remover todas as mudanças que estão staged, colocando-as de volta na lista de modified.

Em seguida, reverta todas as modificações
```bash
git reset HEAD --hard
```

Isso irá reverter todas as modificações nos arquivos modificados. Note que se você tinha alguma outra modificação, ela também será perdida.
Se o merge adicionou arquivos novos no repositório, então você pode "limpá-los" através do `git clean`. Novamente da raiz do repositório
```bash
git clean -xdf
```

## Comandos úteis!
```bash
#Para corrigir a mensagem de um commit usamos o comando:
git commit -m "Nova mensagem que vai substituir a anterior" --amend
```

```bash
#O git cherry pick é um comando poderoso do Git que permite ao usuário selecionar commits específicos para trazer ao branch desejado.
git cherry-pick ID_DO_COMMIT
```

**Observação**
Como sempre, cuidado quando usar o git clean já que ele pode apagar arquivos que você gostaria de ter. Você pode usar a opção n em vez de f para listar os arquivos que serão apagados.

## Node

### Instalar qualquer versão do nodejs + npm
[https://www.digitalocean.com/community/tutorials/how-to-install-node-js-on-ubuntu-20-04-pt](https://www.digitalocean.com/community/tutorials/how-to-install-node-js-on-ubuntu-20-04-pt)

### Instalar versão 14
[https://github.com/nodesource/distributions/blob/master/README.md](https://github.com/nodesource/distributions/blob/master/README.md)

### Atualizar para versão 14

```bash
sudo apt-get update

# Adiciona repositorio
curl -sL https://deb.nodesource.com/setup_14.x | sudo bash -

# Faz a instalação
sudo apt install -y nodejs

node -v
# ~v.14.17.5
```

### Extensões que você possa precisar instalar
```bash sudo apt install -y build-essential gcc make libpng-dev```

## NPM

### Instalação
```bash
sudo apt install npm
```

### Verificar versão
```bash
npm -v
```

### Atualizar
```bash
npm install -g npm@latest
```

## Valet (Linux)

### Instalação do Valet
Acesse: [https://cpriego.github.io/valet-linux/faq.html](https://cpriego.github.io/valet-linux/faq.html)

### Ativar SSL
```bash
# Acesse o diretorio do projeto e rode:
valet secure

# Para verificar se foi ativado:
valet links

#+---------------+-----+--------------------+--------------------------+
#| Site          | SSL | URL                    | Path                 |
#+---------------+-----+--------------------+--------------------------+
#| project.x     |  X  | https://project.x.test | /home/user/project.x |
#+---------------+-----+--------------------+--------------------------+
```

### Importar Certificado Google Chrome
```bash
# Acesse o gerenciador de certificados
Settings -> Security -> Manager Certifcate -> Authorities -> Import LaravelValetCASelfSigned

Configurações -> Segurança -> Gerenciar Certificados -> Autoridades -> Importar LaravelValetCASelfSigned

# LaravelValetCASelfSigned é um lugar no seu $HOME/.valet/CA
# Então, se você estiver no Chrome, basta habilitar este parâmetro, acesse:
chrome://flags/#allow-insecure-localhost

# Se você não estiver no Chrome, deve ter um parâmetro como este para encontrar
allow-insecure-localhost
```

## MailHog

### Instalação e configuração do MailHog
[https://github.com/mailhog/MailHog](https://github.com/mailhog/MailHog)

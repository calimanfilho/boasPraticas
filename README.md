# Boas Práticas no Linux
Segue abaixo uma série de boas práticas que foram aprendidas ao longo do meu caminho profissional.

## Instalação de Softwares no Linux

O empacotamento de software é essencial nas distribuições Linux. As distros Debian adotam os pacotes DEB com o gerenciador APT, enquanto as distribuições RPM utilizam pacotes RPM, que podem ser instalados por diversas ferramentas.

É importante destacar que os formatos DEB e RPM não são compatíveis entre si. A conversão entre eles é possível, por meio de ferramentas como o "alien", mas essa abordagem não garante resultados perfeitos. Em geral, é recomendável utilizar os pacotes disponíveis nos repositórios da distribuição. Alguns tipos de pacotes, como os ".txz" e ".tbz2" do Slackware, são específicos de certas distribuições.

Um exemplo notável é o Gentoo, que compila pacotes por meio de scripts especiais chamados "ebuilds". No entanto, essa abordagem demanda mais conhecimento e tempo por parte do usuário.

Também pode ser instalados arquivos compactados no formato .tar.gz no Linux, e envolve alguns passos essenciais garantir uma instalação adequada, o primeiro deles é a descompactação e extração do conteúdo do arquivo compactado com o comando:

```bash
tar -xzvf arquivo.tar.gz
```

É recomendável instalar o software em um diretório apropriado, como `/opt`, criando uma pasta com o nome do desenvolvedor e colocando a pasta descompactada dentro.

Antes de prosseguir, verifique as dependências do *software*. O arquivo README ou o site do projeto podem listar as bibliotecas ou pacotes necessários para que o software funcione corretamente.

Muitos softwares em formato .tar.gz precisam ser compilados antes da instalação. Isso é geralmente feito executando os comandos `./configure`, `make` e `make install` no diretório extraído. No entanto, as etapas exatas podem variar de acordo com o software.

Lembre-se de que os *softwares* instalados manualmente não serão gerenciados pelo sistema de gerenciamento de pacotes da distribuição. Isso significa que se necessário atualizar o *software*, ele deverá ser desinstalado (opcional) manualmente para que a nova versão seja instalada.

Caso seja necessário poderá ser configurado as variáveis de ambiente, para isso basta abrir o arquivo de perfil do *shell*, que pode ser `~/.bashrc` ou `~/.zshrc`, para que seja adicionadas as seguintes linhas ao final do arquivo (exemplo do Java):

```bash
export JAVA_HOME=/caminho/para/o/diretorio/do/java
export PATH=$PATH:$JAVA_HOME/bin
```
Os dois comandos acima tem as seguintes funções, o JAVA_HOME é uma variável de ambiente que aponta para o diretório raiz da instalação do Java. Isso permite que o sistema e outros programas saibam onde encontrar os arquivos relacionados ao Java. O PATH é uma variável de ambiente que contém uma lista de diretórios onde o sistema procura por programas executáveis quando é digitado um comando no terminal, esse comando expande o valor atual da variável PATH, adicionando $JAVA_HOME/bin, assim permitindo que seja executado os comandos do Java diretamente do terminal, sem ter que especificar o caminho completo para os executáveis.

Para aplicar imediatamente as mudanças no ambiente de usuário (altere o comando para o perfil correto do *shell*), execute:

```bash
source ~/.zshrc
```

Para verificar se a configuração foi bem-sucedida, execute:

```bash
java -version
```

Lembre-se de que a configuração das variáveis de ambiente é específica para o usuário. Se for desejado que as configurações sejam globais, também precisará configurá-las para o usuário root.

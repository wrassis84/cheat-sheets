**```systemctl --version```** - Exibe a versão instalada do `systemd`.

**```systemctl -p UnitPath show```** - Exibe os diretórios onde o `systemd` busca as configurações, observando a precedência.

**```pkg-config systemd --variable=systemdsystemunitdir```** - Exibe o diretório de unidades do sistema (`/usr/lib/systemd/system`). Evite fazer alterações neste diretório.

**```pkg-config systemd --variable=systemdsystemconfdir```** - Exibe o diretório de configurações do sistema (`/etc/systemd/system`). Faça neste diretório suas alterações e personalizações.

**```systemctl start <application>.service ou systemctl start <application>```** - Inicia um serviço `systemd` (executa as instruções do arquivo de unidade do serviço).

**```systemctl stop <application>.service```** - Pára um serviço `systemd`, que esteja em execução.

**```systemctl reload <application>.service```** - Recarrega os arquivos de configuração de uma aplicação (sem reiniciar), desde que a aplicação em questão suporte.

**```systemctl reload-or-restart <application>.service```** - Recarrega os arquivos de configuração ou reinicia o serviço, se a aplicação tiver essa necessidade.

**```systemctl try-restart <application>.service```** - Para reiniciar uma aplicação que esteja em execução. Caso contrário, não faz nada.

**```systemctl enable <application>.service```** - Para sempre iniciar um serviço na inicialização do sistema. Isso criará um link simbólico a partir da cópia do arquivo de serviço do sistema (geralmente em `/lib/systemd/system` ou `/etc/systemd/system`) para a localização em disco onde o `systemd` procura por arquivos de inicialização automática (geralmente `etc/systemd/system/<some_target>.target.wants`)

**```systemctl disable <application>.service```** - Para desativar um serviço na inicialização do sistema. Isso irá remover o link simbólico que indica que o serviço deve ser iniciado automaticamente.

**```systemctl status <application>.service```** - Para mostrar o estado do serviço, a hierarquia de cgroup e as primeiras linhas de registro.

**```systemctl is-active <application>.service```** - Para verificar se uma unidade está ativa (em execução). Isso irá retornar o estado da unidade atual, que geralmente é active ou inactive. O código de saída será "0" se for ativo.

**```systemctl is-enabled <application>.service```** - Para verificar se uma unidade está habilitada. Isso irá mostrar se o serviço está enabled ou disabled e irá definir novamente o código de saída como "0" ou "1", dependendo da resposta para a pergunta do comando.

**```systemctl is-failed <application>.service```** - Para verificar se a unidade está em um estado de falha e indica se houve um problema ao iniciar a unidade em questão. Isso irá retornar active se a unidade estiver executando corretamente ou failed caso um erro tenha ocorrido. Se a unidade tiver sido intencionalmente interrompida, ela pode retornar unknown ou inactive. Um status de saída "0" indica que uma falha ocorreu, enquanto um status de saída de "1" indica qualquer outro status.

**```systemctl list-units --state=failed ou systemctl --state=failed```** - Para listar todos os serviços do `systemd` que falharam em iniciar. Uma unit é cada recurso que o `systemd` sabe como operar e gerenciar. As units são similares aos services e jobs dos demais sistemas de init. Um unit-file é um arquivo de configuração com as definições de uma unit.

**```systemctl list-units --all --state=failed ou systemctl --all --state=failed```** - Para listar todos os serviços do `systemd` que falharam em iniciar e também as units que foram carregadas mas estão inativas.

**```systemctl list-units ou systemctl```** - Para listar todas as unidades ativas (por padrão) das quais o `systemd` tem conhecimento. O resultado possui as seguintes colunas:
- UNIT: o nome da unidade de `systemd`;
- LOAD: se a configuração da unidade foi analisada pelo `systemd`. A configuração de unidades carregadas é mantida na memória;
- ACTIVE: um estado resumido que diz se a unidade está ativa. Essa é geralmente uma maneira bastante simples de dizer se a unidade foi iniciada com sucesso ou não;
- SUB: esse é um estado de nível mais baixo que indica informações mais detalhadas sobre a unidade. Isso muitas vezes varia dependendo do tipo de unidade, estado e do método em si com o qual a unidade é executada;
- DESCRIPTION: uma breve descrição textual do que a unidade é ou faz.

**```systemctl list-sockets```** - Para listar todas as unidades do tipo socket.

**```systemctl list-timers```** - Para listar todas as unidades do tipo timer.

**```systemctl list-units --all```** - Isso irá mostrar qualquer unidade que o `systemd` carregou ou tentou carregar, independentemente do seu estado atual no sistema. Algumas unidades tornam-se inativas após serem executadas, e algumas unidades que o `systemd` tentou carregar podem não ter sido encontradas em disco.

**```systemctl list-units --all --state=inactive```** - Para ver apenas unidades inativas.

**```systemctl list-units --type=service```** - Para ver apenas unidades de serviço ativas. `Type` pode assumir: `service`, `mount`, `target`, `path`, `socket`, `swap`, `timer`, `slice`, `automont`.

**```systemctl list-unit-files```** - Para ver todos os arquivos de unidade disponíveis nos caminhos do `systemd`, incluindo aquelas que o `systemd` não tentou carregar.

**```systemctl cat atd.service```** - Para ver o arquivo de unidade de um serviço.

**```systemctl list-dependencies sshd.service```** - Para listar as dependências de uma unidade de serviço.

**```systemctl show sshd.service```** - Para ver as propriedades de baixo nível de uma unidade. As propriedades usam o formato `key=value`.

**```systemctl show sshd.service -p Conflicts```** -  Para exibir uma única propriedade utilize o sinalizador `-p`.

**```sudo systemctl mask nginx.service```** - Para "mascarar" uma unidade tornando-a absolutamente não iniciável, ligando ao `/dev/null`.

**```sudo systemctl unmask nginx.service```** - Para "desmascarar" uma unidade, retornando-a ao estado anterior, podendo ser iniciada ou habilitada.

**```sudo systemctl edit nginx.service```** - Para editar parcialmente um arquivo de unidade, mesclando estas alterações com as configurações originais da unidade.

**```sudo systemctl edit --full nginx.service```** - Para editar integralmente um arquivo de unidade.

**```sudo systemctl daemon-reload```** - Para recarregar o `systemd`.

**```systemctl get-default```** - Para exibir o `target` padrão.

**```sudo systemctl set-default graphical.target```** - Para definir o `target` padrão.

**```systemctl list-unit-files --type=target```** - Para listar os `targets` disponíveis no seu sistema.

**```systemctl list-units --type=target```** - Para listar todos os `targets` ativos.

**```systemctl list-dependencies multi-user.target```** - Para listar todas as dependências de um `target`.

**```sudo systemctl isolate multi-user.target```** - Para alterar, em runtime o `target` atual para o `target` selecionado (multi-user).

**```sudo systemctl rescue```** - Para colocar o sistema em modo monousuário (modo de resgate).

**```sudo systemctl halt```** - Para parar o sistema. O halt instrui o hardware a parar todas as funções de CPU, mas sem desligar.

**```sudo systemctl poweroff```** - Para iniciar um desligamento completo do sistema.

**```sudo systemctl reboot ou sudo reboot```** - Para reiniciar o sistema.

**```pkg-config systemd --variable=systemdsystemunitdir```** - Lista o diretório onde estão armazenadas as unidades do sistema.

**```pkg-config systemd --variable=systemdsystemconfdir```** - Lista o diretório onde estão armazenadas as configurações do sistema.

**```/usr/lib/systemd/system```** - Diretório de unidades do sistema (configurado globalmente). Podem ser alterados durante um upgrade do sistema.

**```/etc/systemd/system```** - Diretório de configuração do sistema (definições locais personalizadas). Não são afetados por upgrades do sistema.

**```systemd-cgls```** - Lista os `cgroups`.

**```journalctl _SYSTEMD_UNIT=sshd.service```** - Exibe os logs da unidade `sshd.service`.

**```systemctl list-jobs```** - Os jobs (solicitações para ativar, reativar e reiniciar no `systemd`), são mudanças de estados das unidades.

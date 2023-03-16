O `tune2fs` é uma ferramenta que permite visualizar e modificar vários parâmetros
nos _sistemas de arquivos_ do tipo **EXT2**, **EXT3** ou mesmo **EXT4**.
Também podemos converter um _sistema de arquivos_ **EXT2** para **EXT3**, bem como
**EXT3** para **EXT4**.

**```sudo tune2fs -l /dev/sda1```** - Exibe os parâmetros atuais do _sistema de arquivos_.

**```sudo tune2fs -L rootfs /dev/sda1```** - Atribui a _label_ "rootfs" ao dispositivo `/dev/sda1`.

**```sudo tune2fs -l /dev/sda3 | grep -i "mount count"```** - Exibe os parâmetros _mount count_ e _maximum mount count_ que definem, respectivamente, quantas vezes o _sistema de arquivos_ foi montado e quantas montagens até o _sistema de arquivos_ ser checado com o utilitário `e2fsck`.

**```sudo tune2fs -c 30 /dev/sda3```** - Define o _maximum count_ do dispositivo `/dev/sda3` para 30.

**```sudo tune2fs -C 100 /dev/sda3```** - Define o _mount count_ do dispositivo `/dev/sda3` para 100.

**```sudo tune2fs -l /dev/sda5 | grep interval```** - Exibe o intervalo de checagem de um _sistema de arquivos_.

**```sudo tune2fs -i 2w /dev/sda4```** - Define o intervalo de checagem de um _sistema de arquivos_ para 2 semanas (weeks). O intervalo pode ser definido em dias: `d`, semanas: `w` ou meses: `m`.

**```sudo tune2fs -c -1 /dev/sda5 && tune2fs -i -1 /dev/sda5```** - Define _maximum count_ e _check interval_ para `-1`, o que desabilita a checagem do _sistema de arquivos_ no _boot_ do sistema.

**```sudo tune2fs -M mount_dir /dev/sda5```** - Define o último diretório montado para o _sistema de arquivos_ `/dev/sda5`.

**```sudo tune2fs -T now /dev/sda5```** - Define a data da última checagem do _sistema de arquivos_ `/dev/sda5` para o momento atual. `-T` aceita o formato de tempo "YYYYMMDD[HH[MM[SS]]]".

**```sudo tune2fs -e continue /dev/sda5```** - Define o comportamento do _kernel_ ao encontrar erros no _sistema de arquivos_: _continue_ continua a execução normalmente; _remount-ro_ remonta o _sistema de arquivos_ como _somente leitura_ e _panic_ causa um _kernel panic_.

**```sudo tune2fs -j /dev/sda5```** - Adiciona o recurso de _journaling_ a um _sistema de arquivos_ **EXT2**, convertendo-o para o tipo **EXT3**. Importante fazer _backup_ dos dados antes de executar esta conversão.

**```sudo tune2fs -U UUID /dev/sda5```** - Altera o **UUID** de um _sistema de arquivos_: O parâmetro `-U` pode assumir: _clear_ para apagar o **UUID**; _random_ para gerar um novo **UUID** e _time_ para gerar um **UUID** baseado em tempo. O **UUID** só pode ser alterado com o _sistema de arquivos_ desmontado.

**```sudo tune2fs -O extents,uninit_bg,dir_index /dev/sda5```** - Adiciona as configurações indicadas (extents,uninit_bg,dir_index) a um _sistema de arquivos_ do tipo **EXT3**, convertendo-o para o tipo **EXT4**. Importante fazer o _backup_ dos dados para evitar perdas e corrupção de dados.

**```sudo tune2fs -O ^extents,^uninit_bg,^dir_index /dev/sda5```** - Remove as configurações indicadas (extents,uninit_bg,dir_index) de um _sistema de arquivos_. Importante fazer o _backup_ dos dados para evitar perdas e corrupção de dados.
Adaptado de: [15 tune2fs command examples in Linux [Cheat Sheet]](https://www.golinuxcloud.com/tune2fs-command-in-linux/).
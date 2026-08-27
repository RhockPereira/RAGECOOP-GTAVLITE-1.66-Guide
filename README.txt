RAGECOOP no GTA V 1.66 / Build 1.0.2845.0
Guia de compatibilidade e instalação
======================================

IMPORTANTE
----------

Este guia documenta uma configuração que foi testada com sucesso em uma instalação
otimizada do GTA V baseada na versão 1.66 / build 1.0.2845.0.

O objetivo deste repositório é apenas documentar compatibilidade, instalação e
solução de problemas.

Este projeto NÃO distribui:
- GTA V;
- arquivos .rpf ou outros arquivos proprietários da Rockstar Games;
- GTA5.exe;
- cracks;
- bypass de Rockstar Games Launcher / Social Club;
- cópias modificadas ou "Lite" do jogo;
- arquivos proprietários de terceiros sem autorização.

Use sua própria instalação legítima do GTA V e obtenha as dependências pelos
projetos/fontes oficiais.

Este guia não é afiliado, patrocinado ou endossado pela Rockstar Games,
Take-Two Interactive, RAGECOOP, ScriptHookV, ScriptHookVDotNet ou Hamachi.


CONFIGURAÇÃO TESTADA
--------------------

Jogo:
- GTA V Legacy
- Versão/base: 1.66
- Build detectada pelo ScriptHookV: VER_1_0_2845_0

RAGECOOP:
- RAGECOOP 1.5.4.7 (release estável)

ScriptHookVDotNet:
- 3.6.0

Outros requisitos:
- ScriptHookV
- .NET Framework 4.8
- Lidgren.Network.dll
- Uma solução de rede virtual para jogar pela Internet, como Hamachi

Observação:
Nesta configuração específica, o ScriptHookVDotNet 3.7.x causou incompatibilidade
com o RAGECOOP 1.5.4.7. O erro observado foi:

System.MissingMethodException:
Método não encontrado:
'Byte* SHVDN.NativeMemory.FindPattern(System.String, System.String)'

A substituição do ScriptHookVDotNet 3.7.x pelo 3.6.0 resolveu essa etapa.


LINKS OFICIAIS
--------------

RAGECOOP:
https://github.com/RAGECOOP/RAGECOOP-V

Releases do RAGECOOP:
https://github.com/RAGECOOP/RAGECOOP-V/releases

ScriptHookV:
https://www.dev-c.com/gtav/scripthookv/

ScriptHookVDotNet:
https://github.com/scripthookvdotnet/scripthookvdotnet

Release 3.6.0 do ScriptHookVDotNet:
https://github.com/scripthookvdotnet/scripthookvdotnet/releases/tag/v3.6.0

Recursos oficiais do RAGECOOP, incluindo Lidgren.Network.dll:
https://github.com/RAGECOOP/GTAV-RESOURCES


PARTE 1 - INSTALAÇÃO DO CLIENTE
-------------------------------

Esta parte deve ser feita NOS DOIS COMPUTADORES.

Ou seja:

HOST:
- instala o cliente.

SEGUNDO JOGADOR:
- também instala o cliente.

O RageCoop Server Windows NÃO deve ser instalado nos dois computadores.
Ele será explicado separadamente mais abaixo.


1. SCRIPTHOOKV
--------------

Baixe o ScriptHookV pela fonte oficial.

Copie para a pasta raiz do GTA V, onde está o GTA5.exe:

dinput8.dll
ScriptHookV.dll

Opcional para teste:

NativeTrainer.asi

Exemplo:

GTA V\
  GTA5.exe
  dinput8.dll
  ScriptHookV.dll
  NativeTrainer.asi


TESTE DO SCRIPTHOOKV
--------------------

Abra o GTA V.

Se o Native Trainer abrir e funcionar, o ScriptHookV provavelmente está
carregando corretamente.

Depois de fechar o jogo, verifique o arquivo:

ScriptHookV.log

Na configuração testada, foi detectado:

INIT: Success, game version is VER_1_0_2845_0

Isso confirmou que o executável era reconhecido corretamente como build 2845.


2. SCRIPTHOOKVDOTNET 3.6.0
---------------------------

IMPORTANTE:

Para esta configuração testada, utilize o ScriptHookVDotNet 3.6.0.

Não misture arquivos de versões diferentes.

Se você já possui outra versão instalada, remova/mova para backup os arquivos
antigos antes de instalar a 3.6.0.

Copie para a raiz do GTA V:

ScriptHookVDotNet.asi
ScriptHookVDotNet2.dll
ScriptHookVDotNet3.dll
ScriptHookVDotNet.ini

O .ini não é obrigatório para o funcionamento básico, mas é recomendado manter
o arquivo correspondente à mesma versão.

Os arquivos XML de documentação que podem acompanhar o download não são
necessários para jogar.


ESTRUTURA ESPERADA
------------------

GTA V\
  GTA5.exe
  dinput8.dll
  ScriptHookV.dll
  ScriptHookVDotNet.asi
  ScriptHookVDotNet2.dll
  ScriptHookVDotNet3.dll
  ScriptHookVDotNet.ini
  scripts\


TESTE DO SCRIPTHOOKVDOTNET
--------------------------

Abra o GTA V.

Pressione F4.

Em notebook, dependendo da configuração das teclas de função, pode ser
necessário usar:

Fn + F4

O console do ScriptHookVDotNet deve aparecer.

Ele deve identificar o Community Script Hook V .NET.

Se o console abrir normalmente, esta camada está funcionando.


3. RAGECOOP CLIENT 1.5.4.7
---------------------------

Baixe na página oficial de releases:

RAGECOOP 1.5.4.7

Baixe:

RageCoop Client.zip

NÃO baixe a Nightly para esta configuração.

Extraia o conteúdo do pacote diretamente dentro de:

GTA V\scripts\

Evite criar acidentalmente uma pasta extra como:

GTA V\scripts\RageCoop.Client.zip\...

Os arquivos do cliente precisam ficar na estrutura esperada pelo mod.


4. LIDGREN.NETWORK.DLL
----------------------

Durante nosso teste, o RAGECOOP carregava parcialmente, mas o log mostrava:

System.IO.FileNotFoundException:
Não foi possível carregar arquivo ou assembly
'Lidgren.Network'

O pacote utilizado continha Lidgren.Network.XML, mas a DLL necessária não estava
presente na pasta scripts.

A correção foi obter:

Lidgren.Network.dll

do repositório oficial:

https://github.com/RAGECOOP/GTAV-RESOURCES

Coloque:

Lidgren.Network.dll

diretamente em:

GTA V\scripts\

Exemplo:

GTA V\
  scripts\
    RageCoop.Client.dll
    RageCoop.Core.dll
    Lidgren.Network.dll
    ...


Não baixe DLLs de sites aleatórios.

Prefira baixar/clonar o repositório oficial GTAV-RESOURCES e extrair o arquivo
a partir dele.


5. TESTE DO RAGECOOP
--------------------

Abra o GTA V.

Quando o RAGECOOP carregar corretamente, deverá aparecer uma mensagem semelhante a:

RAGECOOP
Welcome!
Press F9 to open the menu.

Pressione:

F9

ou, em alguns notebooks:

Fn + F9

Se o menu abrir, o cliente está carregando corretamente.


ERROS QUE ENCONTRAMOS
=====================

ERRO 1 - F9 NÃO ABRIA / RAGECOOP ERA ABORTADO
---------------------------------------------

No ScriptHookVDotNet.log apareceu:

System.TypeInitializationException

causado por:

System.MissingMethodException:
Método não encontrado:
'Byte* SHVDN.NativeMemory.FindPattern(System.String, System.String)'

Configuração que apresentava o problema:

- RAGECOOP 1.5.4.7
- ScriptHookVDotNet 3.7.x

Solução utilizada:

Substituir todos os arquivos do ScriptHookVDotNet 3.7.x pelos arquivos da
versão 3.6.0.

Não misture, por exemplo:

ScriptHookVDotNet.asi 3.6.0
com
ScriptHookVDotNet3.dll 3.7.x

Todos devem vir do mesmo pacote.


ERRO 2 - LIDGREN.NETWORK AUSENTE
--------------------------------

O log apresentou:

System.IO.FileNotFoundException:
'Lidgren.Network, Version=2012.1.7.0 ...'

Solução:

Adicionar Lidgren.Network.dll em:

GTA V\scripts\

usando o arquivo obtido pelo repositório oficial:

https://github.com/RAGECOOP/GTAV-RESOURCES


DIAGNÓSTICO
-----------

Se alguma coisa não funcionar, verifique primeiro:

ScriptHookV.log

e:

ScriptHookVDotNet.log

Também verifique os logs criados pelo RAGECOOP dentro da pasta scripts/RageCoop,
caso existam.

Uma ordem simples de diagnóstico:

1. GTA V abre sem mods?
2. Native Trainer funciona?
3. F4 abre o console do ScriptHookVDotNet?
4. Aparece "RAGECOOP Welcome"?
5. F9 abre o menu do RAGECOOP?
6. O servidor local aceita conexão?


PARTE 2 - SERVIDOR
==================

ATENÇÃO - SOMENTE O HOST
------------------------

!!! MUITO IMPORTANTE !!!

SOMENTE O JOGADOR QUE SERÁ O HOST PRECISA BAIXAR E EXECUTAR:

RageCoop Server Windows

O segundo jogador NÃO precisa baixar o RageCoop Server Windows.

Resumo:

HOST:
- GTA V
- ScriptHookV
- ScriptHookVDotNet 3.6.0
- RAGECOOP Client
- Lidgren.Network.dll
- Hamachi ou solução de rede equivalente
- RageCoop Server Windows

SEGUNDO JOGADOR:
- GTA V
- ScriptHookV
- ScriptHookVDotNet 3.6.0
- RAGECOOP Client
- Lidgren.Network.dll
- Hamachi ou solução de rede equivalente

SEGUNDO JOGADOR NÃO PRECISA:
- RageCoop Server Windows


COMO INSTALAR O SERVIDOR
------------------------

Na release 1.5.4.7 do RAGECOOP, baixe:

RageCoop Server Windows

Extraia em uma pasta SEPARADA.

NÃO coloque o servidor dentro da pasta do GTA V.

Exemplo:

Desktop\
  RageCoop Server\
    RageCoop.Server.exe
    ...

Execute:

RageCoop.Server.exe

Na primeira execução, o Windows Firewall pode perguntar se deseja permitir o
programa na rede.

O host deverá permitir a comunicação necessária para o servidor.


TESTE LOCAL
-----------

Antes de tentar jogar pela Internet, o host pode testar o próprio servidor.

1. Abra RageCoop.Server.exe.
2. Deixe a janela do servidor aberta.
3. Abra GTA V.
4. Pressione F9.
5. Conecte-se a:

127.0.0.1:4499

Se conectar, o servidor está funcionando localmente.


PORTA
-----

A porta padrão utilizada nesta configuração é:

4499/UDP

O formato do endereço usado pelo RAGECOOP é:

IP:PORTA

Exemplo local:

127.0.0.1:4499


PARTE 3 - JOGAR COM HAMACHI
===========================

O Hamachi foi a solução utilizada neste teste.

Os dois jogadores devem:

1. Ter o Hamachi instalado.
2. Estar conectados à mesma rede do Hamachi.
3. Aparecer como online um para o outro.
4. Ter o RAGECOOP Client funcionando.


HOST
----

O host deve:

1. Abrir o Hamachi.
2. Abrir RageCoop.Server.exe.
3. Manter o servidor aberto.
4. Abrir o GTA V normalmente.


SEGUNDO JOGADOR
---------------

O segundo jogador:

1. Abre o Hamachi.
2. Abre o GTA V.
3. Pressiona F9.
4. Digita o IPv4 do Hamachi DO HOST seguido de :4499.

Formato:

IP_DO_HOST:4499

Exemplo fictício:

25.41.14.30:4499

Não copie esse IP de exemplo.
Use o IPv4 real exibido pelo Hamachi no computador do host.


IMPORTANTE SOBRE O SERVIDOR
---------------------------

O RageCoop Server Windows precisa permanecer aberto enquanto vocês estiverem
jogando.

Se o host fechar o servidor, os clientes perderão a conexão.

O segundo jogador não deve iniciar outro servidor para simplesmente entrar na
sessão do host.


CHECKLIST RÁPIDO
================

NO HOST:

[ ] GTA V build 1.0.2845.0
[ ] ScriptHookV funcionando
[ ] ScriptHookVDotNet 3.6.0
[ ] pasta scripts criada
[ ] RAGECOOP Client 1.5.4.7 instalado
[ ] Lidgren.Network.dll em scripts
[ ] F9 abre o RAGECOOP
[ ] Hamachi conectado
[ ] RageCoop.Server.exe aberto
[ ] 127.0.0.1:4499 conecta localmente


NO SEGUNDO JOGADOR:

[ ] ScriptHookV funcionando
[ ] ScriptHookVDotNet 3.6.0
[ ] RAGECOOP Client 1.5.4.7
[ ] Lidgren.Network.dll em scripts
[ ] F9 abre o RAGECOOP
[ ] Hamachi conectado à mesma rede
[ ] conecta usando IP_DO_HOST:4499


O QUE NÃO FAZER
===============

- Não distribuir o GTA V neste repositório.
- Não distribuir cracks.
- Não distribuir GTA5.exe.
- Não distribuir arquivos .rpf da Rockstar.
- Não hospedar uma cópia do "GTA V Lite".
- Não misturar versões diferentes do ScriptHookVDotNet.
- Não instalar o RageCoop Server Windows dentro da pasta do GTA.
- Não fazer o segundo jogador baixar o Server sem necessidade.
- Não baixar DLLs de sites aleatórios.


OBSERVAÇÃO SOBRE OUTRAS BUILDS
==============================

Este guia documenta especificamente a configuração que foi testada em:

GTA V 1.66 / build 1.0.2845.0

Não existe garantia de que a mesma combinação funcione em builds mais novas.

O próprio ScriptHookVDotNet informa que a versão estável 3.6.0 possui problemas
com GTA V 1.0.3258.0 ou superior. O RAGECOOP também recomenda sua versão Nightly
junto de SHVDN Nightly para essas builds mais recentes.

Portanto:

Build 2845:
- configuração deste guia.

Build 3258 ou superior:
- consulte as instruções atuais dos projetos oficiais.


STATUS DO TESTE
===============

Na configuração documentada neste arquivo, foi possível:

[OK] ScriptHookV detectar VER_1_0_2845_0
[OK] Abrir Native Trainer
[OK] Abrir console do ScriptHookVDotNet
[OK] Carregar RAGECOOP
[OK] Abrir o menu com F9
[OK] Iniciar RageCoop Server Windows
[OK] Conectar localmente usando 127.0.0.1:4499
[OK] Conectar dois computadores pela rede virtual usando IP_DO_HOST:4499


CRÉDITOS
========

Todo o crédito pelos projetos originais pertence aos respectivos autores e
contribuidores:

- RAGECOOP
- ScriptHookV / Alexander Blade
- ScriptHookVDotNet
- Lidgren Network e respectivos contribuidores

Este guia apenas documenta uma combinação de versões e procedimentos que foi
testada na prática.


LICENÇA DESTE GUIA
==================

Você pode escolher uma licença para o texto e scripts que forem criados por você
neste repositório, por exemplo MIT.

A licença escolhida para este guia NÃO concede direitos sobre GTA V ou sobre
arquivos de terceiros.

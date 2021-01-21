# Windows

## Listar atualizações do Windows - KBs
```bash
wmic qfe get hotfixid
```

## Usuário com perfil temporário
```
Abrir o "regedit"
Verificar a chave do usuario em questão no caminho abaixo:
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows
NT\CurrentVersion\ProfileList
Verificar tratativas, tirar o ".bak" da chave do
usuário que estava como TEMP.
Ou deletar a chave e renomear a pasta em:
"C:\Users\XXXXXX"
```

## Forçar a atualização de GPO
```bash
gpupdate /force /wait:no
```

## Criar Pendrive Bootável CMD
```bash
cmd
diskpart
list disk
# Ver qual o disco correto pegar o numero
select disc X
clean
create partition primary
select partition 1
format fs=ntfs quick
assign
active
exit
exit
```

## Executar

## Painel de Controle
- Opções Acessibilidade `control access.cpl`
- Adicionar Novo Hardware `control sysdm.cpl add new hardware`
- Adicionar/Remover Programas `control appwiz.cpl`
- Propriedades de Data/Hora `control timedate.cpl`
- Propriedades de Vídeo `control desk.cpl`
- FindFast `control findfast.cpl`
- Pasta Fontes `control fonts`
- Propriedades da Internet `control inetcpl.cpl`
- Propriedades do Joystick `control joy.cpl`
- Propriedades do Teclado `control main.cpl keyboard`
- Microsoft Exchange `control mlcfg32.cpl`
- Microsoft Mail Post Office `control wgpocpl.cpl`
- Propriedades do Modem `control modem.cpl`
- Propriedades do Mouse `control main.cpl`
- Propriedades de Multimídia `control mmsys.cpl`
- Propriedades da Rede `control netcpl.cpl ou ncpa.cpl`
- Propriedades de Senha `control password.cpl`
- Placa do PC `control main.cpl pc card (PCMCIA)`
- Gerenciamento de Energia (W95) `control main.cpl power`
- Gerenciamento de Energia (W98) `control powercfg.cpl`
- Pasta Impressoras `control printers`
- Configurações Regionais `control intl.cpl`
- Scanners e Câmeras `control sticpl.cpl`
- Propriedades de Som `control mmsys.cpl sounds`
- Propriedades do Sistema `control sysdm.cpl`


## Comandos no Executar
- Sobre o Windows (Ver a versão do Windows) = `winver`
- Atualizações automáticas = `wuaucpl.cpl`
- Adicionar ou remover programas = `appwiz.cpl`
- Administrador da origem de dados de ODBC = `odbccp32.cpl`
- Assistente de acessibilidade = `accwiz`
- Assistente de câmara ou scaner = `wiaacmgr`
- Assistente de configuração de rede = `netsetup.cpl`
- Assistente de cópia de segurança ou restauro = `ntbackup`
- Assistente de ligação ? Internet = `icwconn1` ou `inetwiz`
- Assistente de transferência de definições e de ficheiros = `migwiz`
- Assistente de transferência de ficheiros do Bluetooth = `fsquirt`
- Assistente para adicionar hardware = `hdwwiz.cpl`
- Calculadora= `calc`
- Centro de segurança do Windows = `wscui.cpl`
- Certificados = `certmgr.msc`
- Cliente Telnet = `telnet`
- Configuração de protocolo de Internet (apagar informações de DNS ) = `ipconfig /flushdns`
- Configuração de protocolo de Internet (Todas as conexões ) = `ipconfig /release`
- Configuração de protocolo de Internet (ver DNS ) = `ipconfig /displaydns`
- Configuração de protocolo de Internet (ver tudo) = `ipconfig /all`
- Configuração de protocolo de Internet (Modificar DHCP Class ID) = `ipconfig /setclassid`
- Configuração do IP = `ipconfig`
- Conjunto de politicas resultante (XP Prof) = `rsop.msc`
- Constas de utilizadores = `nusrmgr.cpl`
- Controladores de jogos = `joy.cpl`
- Definições da segurança local = `secpol.msc`
- Desfragmentador do disco = `dfrg.msc`
- Desliga o utilizador do Windows = `logoff`
- Editor de caractere privado = `eudcedit`
- Editor de configuração do sistema = `sysedit`
- Editor de registo = regedit / `regedit32`
- Encerramento do Windows = shutdown`
- Explorador do Windows = `explorer`
- Ferramenta de diagnóstico do Direct X = `dxdiag`
- Ferramenta de importação de livro de endereços = `wabmig`
- Ferramenta de remoção de software malicioso Microsoft Windows = `mrt`
- Ferramentas administrativas = control `admintools`
- Firewall do Windows = `firewall.cpl`
- Fontes = `fonts`
- Gestão de computadores = `compmgmt.msc`
- Gestão de discos = `diskmgmt.msc`
- Gestor de dispositivos = `devmgmt.msc`
- Gestor de objetos – pacote = `packager`
- Gestor de partições do disco = `diskpart`
- Gestor de tarefas do Windows = `taskmgr`
- Gestor de utilitários = `utilman`
- Gestor de verificador de controladores = `verifier`
- HyperTerminal = `hypertrm`
- Iexpress Wizard = `iexpress`
- Impressoras e faxes = `control printers`
- Infra-estrutura de gestão do Windows = `wmimgmt.msc`
- Iniciar Windows Update = `wupdmgr`
- Itens a sincronizar = `mobsync`
- Internet Explorer = `iexplore`
- Introdução do Windows XP = `tourstart`
- Jogo de cartas Copas = `mshearts`
- Jogo de cartas FreeCell = `freecell`
- Jogo de cartas Paciência Spider = `spider`
- Jogo Campo Minado = `winmine`
- Ligação ao ambiente de trabalho remoto = `mstsc`
- Ligações de rede = `ncpa.cpl` ou `control netconnections`
- Limpeza do disco = `cleanmgr`
- Linha de comandos = `cmd`
- Lista telefônica = `rasphone`
- Livro de endereços = `wab`
- Mapa de caracteres = `charmap`
- Marcador telefônico = `dialer`
- Microsoft Access (se instalado) = `msaccess`
- Microsoft Chat = `winchat`
- Microsoft Excel (se instalado) = `excel`
- Microsoft Frontpage (se instalado) = `frontpg`
- Microsoft Movie Maker = `moviemk`
- Microsoft Paint = `mspaint`
- Microsoft Powerpoint (se instalado) = `powerpnt`
- Microsoft Word (se instalado) = `winword`
- Nero (se instalado) = `nero`
- Netmeeting = `conf`
- Notepad = `notepad`
- Nview Desktop Manager (se instalado) = `nvtuicpl.cpl`
- Opções de acessibilidade = `access.cpl`
- Opções de pastas = `control folders`
- Opções regionais e de idioma = `intl.cpl`
- Outlook Express = `msimn`
- Painel de controle = `control`
- Painel de controle Direct X (se instalado) = `directx.cpl`
- Painel de controle Java (se instalado) = `jpicpl32.cpl`
- Paint = `pbrush`
- Partilhas DDE = `ddeshare`
- Pasta de impressoras = `printers`
- Pastas compartilhadas = `fsmgmt.msc`
- Pedidos do operador de armazenamento removível = `ntmsoprq.msc`
- Performance Monitor = `perfmon`
- Performance Monitor = `perfmon.msc`
- Phone and Modem Options = `telephon.cpl`
- Pinball para Windows = `pinball`
- Politica de grupo (XP Prof) = `gpedit.msc`
- Power Configuration = `powercfg.cpl`
- Procura rápida (quando ligada) = `findfast.cpl`
- Propriedade des visualização = `control color`
- Propriedades da internet = `inetcpl.cpl`
- Propriedades de data e hora = `timedate.cpl`
- Propriedades de senhas = `password.cpl`
- Propriedades de som e dispositivos de áudio = `mmsys.cpl`
- Propriedades de visualização = `control desktop/desk.cpl`
- Propriedades do rato = `main.cpl` ou `control mouse`
- Propriedades do sistema = `sysdm.cpl`
- Propriedades do teclado = `control keyboard`
- Protecção de base de dados do Windows = syskey`
- Protecção de ficheiros do Windows (analisar em cada arranque) `sfc /scanboot`
- Protecção de ficheiros do Windows (analisar no próximo arranque) = `sfc /scanonce`
- Protecção de ficheiros do Windows (analisar) = `sfc /scannow`
- Protecção de ficheiros do Windows (repor configuração de fábrica) = `sfc /revert`
- Quicktime (se instalado) = `QuickTime.cpl`
- Real Player (se instalado) = `realplay`
- Scanners e câmaras = `sticpl.cpl`
- Serviço de indexação = `ciadv.msc`
- Serviços = `services.msc`
- Serviços componentes = `dcomcnfg`
- Tarefas agendadas = `control schedtasks`
- Teclado de ecrã = `osk`
- Tipos de letra = `control fonts`
- Tweak UI (se instalado ) = `tweakui`
- Utilitário de configuração do sistema = `msconfig`
- Utilitário de rede do cliente de SQL Server = `cliconfg`
- Utilitário de verificação de ficheiros do sistema = `sfc`
- Utilitário de verificação do disco = `chkdsk`
- Utilitário Dr. Watson para o Windows = `drwtsn32`
- Utilizadores e grupos locais = `lusrmgr.msc`
- Verificação de assinatura do ficheiro = `sigverif`
- Visualizador da área de armazenamento = `clipbrd`
- Visualizador de aplicações de java (se instalado) = `javaws`
- Visualizador de eventos = `eventvwr.msc`
- Windows Magnifier = `magnify`
- Windows Media Player = `wmplayer`
- Wordpad = `write`

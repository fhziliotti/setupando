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

# GIT

## Instalação GIT Bash
```
https://git-for-windows.github.io/
Desmarca o Git GUI Here
Use Git from Git Bash only
Checkout as is..
```
```bash
git config --global user.name "Nome Completo"
git config --global user.email email@dominio.com

### Proxy
```bash
# Configurar proxy
git config --global http.proxy proxy.dominio:80
# Desativar proxy
git config --global --unset http.proxy
# Verificar configuração de proxy
git config --global --get http.proxy
```

## Comandos úteis
```bash
git clone URL
git add .
git commit -m "Um commit"
# Push
git push origin master
# Pull
git pull origin master
# Git status, verifica se tem alguma modificação
git status

# Esquecer Push dar Pull
git fetch --all
git reset --hard origin/master

# Enviar para repositório remoto
git pull origin master
```

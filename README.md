# classroom50
Classroom 50 configuration, manifests, workflows, and scores

# Tutorial WSL

Siga os passos a seguir para entregar as tarefas da disciplina usando o _Windows Subsystem for Linux_ (WSL). 

> A documentação completa está [disponível aqui](https://code.visualstudio.com/docs/remote/wsl-tutorial), mas alguns passos requerem permissão de administrador. 

## Extensão WSL no VS Code

Procure e instale a [extensão WSL para o VS Code](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-wsl). 

## Abrir um terminal WSL

No meu iniciar, digite `WSL` ou pressione ⊞+R para executar o mesmo comando. 

## Testando a ligação entre VS Code e WSL

Para verificar se as instalações estão corretas, abra um terminal WSL e digite `code .` na pasta desejada, o VS Code deve abrir. O sistema de arquivos do Windows é montado em `/mnt/c/`.

No VS Code, clique em **Terminal** e depois em **New Terminal** ou digite `Ctrl+Shift+'`. No terminal digite `uname` para verificar se se trata de um terminal **Linux**. 

```
root@CP-DK-214591:/mnt/c/Users/705990/Workspace/classroom50# uname
Linux
```

## Pacotes úteis para a disciplina

No terminal Linux, use o comando a seguir para instalar pacotes relevantes para a disciplina:

```
apt update
apt install gh iverilog gtkwave gcc-riscv64-linux-gnu gcc-riscv64-unknown-elf qemu-user-static
```

## Acessando os repositórios da disciplina

Os repositórios da disciplina são privados e ficam dentro da organização [DC-UFSCar no GitHub](https://github.com/DC-UFSCar). Cada estudante só tem acesso aos seus repositórios individuais e os de seu grupo. 

Siga os seguinte passos para se autenticar no GitHub e poder acessar os repositórios:

```
root@CP-DK-214591:~# gh auth login
? What account do you want to log into?  [Use arrows to move, type to filter]
> GitHub.com
  GitHub Enterprise Server
```

```
root@CP-DK-214591:~# gh auth login
? What account do you want to log into? GitHub.com
? What is your preferred protocol for Git operations on this host?  [Use arrows to move, type to filter]
  HTTPS
> SSH
```

```
root@CP-DK-214591:~# gh auth login
? What account do you want to log into? GitHub.com
? What is your preferred protocol for Git operations on this host? SSH
? Upload your SSH public key to your GitHub account?  [Use arrows to move, type to filter]
  /root/.ssh/id_ed25519.pub
> Skip
```

```
root@CP-DK-214591:~# gh auth login
? What account do you want to log into? GitHub.com
? What is your preferred protocol for Git operations on this host? SSH
? Upload your SSH public key to your GitHub account? Skip
? How would you like to authenticate GitHub CLI?  [Use arrows to move, type to filter]
> Login with a web browser
  Paste an authentication token
```

Copie o código gerado nesta etapa:

```
root@CP-DK-214591:~# gh auth login
? What account do you want to log into? GitHub.com
? What is your preferred protocol for Git operations on this host? SSH
? Upload your SSH public key to your GitHub account? Skip
? How would you like to authenticate GitHub CLI? Login with a web browser

! First copy your one-time code: XXXX-XXXX
Press Enter to open github.com in your browser...
```

Se o navegador não abrir sozinho, acesse a URL indicada para se logar: https://github.com/login/device, cole o código nela e clique em **Continue**, depois clique em **Authorize github**. 

Pronto! Agora você já terá acesso ao repositório via linha de comando e pode usar os comandos `clone`, `commit`, `push`, etc. normalmente. Use sempre a URL SSH `git@github.com:DC-UFSCar/SEU_REPO_AQUI.git`.
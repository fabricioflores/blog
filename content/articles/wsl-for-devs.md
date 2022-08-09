---
title: WSL for a developer environment
description: Configure WSL for a developer environment, to have your Linux shell in Windows!
img: https://fabricioflores.files.wordpress.com/2021/03/image.png
alt: WSL
---
### Brief story and why?

At the University, when I started programming, I used Linux environments to get work in all my developer environment. Then, since I started to work as a developer, always I've been using macOS, with all its virtues and defects.

But, in a previous project in my work, they decided to give me a PC to work with this stack:

- NodeJS in the backend
- Angular in the frontend

So, my first thought was back to the origins and install Ubuntu in that PC. Problems? Yes, drivers: graphic card and trackpad. I said: Ok, no problem. I will work on this. But, was my fault. I couldn't work in a weird resolution and with a trackpad that was deciding for me where to place.

So, the solution was clear: that PC will work fine only with Windows


### WSL

After doing research about the best way to have commands that I already use in macOS and Linux, I read that there is a Linux embedded in Windows, called <a href="https://docs.microsoft.com/en-us/windows/wsl/about">Windows Subsystem for Linux</a>. Basically, you can have a Linux bash without the limitations of virtualization, and the problems I had with drivers.

I´ve worked with CentOS and Ubuntu, but I decided to use the last one. So, let´s start

1. Enable WSL for Windows 10. You need to open PowerShell as admin and run

```
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
````

2. Go to<a href="https://aka.ms/wslstore"> Microsoft Store</a> and choose your favourite distro. As I said, I will use Ubuntu.

<img src="https://fabricioflores.files.wordpress.com/2021/03/image.png?w=1024" />

Click on Get and Install it.

3. After that, start Ubuntu. It will take a time to finish the installation, and the first time will ask you for a UNIX user and password.

<img src="https://fabricioflores.files.wordpress.com/2021/03/image-1.png?w=979"/>

And now you have Linux in your Windows PC!!!

<img src="https://fabricioflores.files.wordpress.com/2021/03/image-2.png?w=978" />

### GIT, NODE, Angular

After you have installed, you would like to test a local environment.

First of all, you need to setup your local git. So, run:

```
git config --global user.email "you@example.com"
git config --global user.name "Your Name"
```

For this example, I will install Node and create a sample project in Angular.

For Node, I usually use <a href="https://github.com/nvm-sh/nvm">NVM</a>. So:

```
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.37.2/install.sh | bash
```

If you are using the default bash, it will add the env vars directly. Otherwise, add

```
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] &amp;&amp; \. "$NVM_DIR/nvm.sh"  # This loads nvm
[ -s "$NVM_DIR/bash_completion" ] &amp;&amp; \. "$NVM_DIR/bash_completion"  # This loads nvm bash_completion
```

to your rc bash file. Close and re open your terminal.

I will use the latest LTS version

```
nvm install 14
```

<img src="https://fabricioflores.files.wordpress.com/2021/03/image-3.png?w=1024" />

And I will install Angular for a test project.

```
npm install -g @angular/cli
```

And create a new project

```
ng new test-app
```

Angular creates a project with all the things you would need to start. Go to the created folder and start the server

```
cd test-app
npm start
```

Go to your browser at go to `http://localhost:4200/` and you will see your app

<img src="https://fabricioflores.files.wordpress.com/2021/03/image-4.png?w=1024"/>

### VSCODE

Everything is fine, but in the real life you need to modify your code. So, VSCode will help us using the code in WSL and modifying in Windows.

First of all, download and install the Windows version of <a href="https://code.visualstudio.com/">VSCode</a>

Open a new terminal of WSL and go to the folder you would like to open in VSCODE, and type

```
code .
```

That will open Windows' VSCode with the content of your WSL folder.

You will see also a recommended install about WSL, please install it. Close VSCODE and open it again from the terminal. It will finish the installation and you will see that is connected and also is taking WSL git configuration.

You will see that hot reload works.

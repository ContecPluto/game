https://subicura.com/2017/11/22/mac-os-development-environment-setup.html#%EA%B7%B8%EB%9E%98%EC%84%9C](https://subicura.com/2017/11/22/mac-os-development-environment-setup.html



### xcode

```bash
$ xcode-select --install
$ sudo installer -pkg /Library/Developer/CommandLineTools/Packages/macOS_SDK_headers_for_macOS_10.14.pkg -target /
```



### homebrew

```bash
$ /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
$ brew doctor
$ echo 'export PATH="/usr/local/bin:$PATH"' >> ~/.zshrc
$ brew tap caskroom/cask
```



### iterm2

```bash
$ brew cask install iterm2
$ brew tap caskroom/fonts && brew cask install font-source-code-pro
```



### zsh

```bash
$ brew install zsh zsh-completions
```



### oh-my-zsh

```bash
$ sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
$ source ~/.zshrc
```

- plugin 01

  ```bash
  $ git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
  ```

  ```bash
  # ~/.zshrc
  plugins=( [plugins...] zsh-syntax-highlighting)
  ```

  ```bash
  $ source ~/.zshrc
  ```

- plugin 02

  ```bash
  $ git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
  ```

  ```bash
  # ~/.zshrc
  plugins=( [plugins...] zsh-autosuggestions)
  ```

  ```bash
  $ source ~/.zshrc
  ```



### git

```bash
$ brew install git git-lfs
$ git config --global user.name "Your Name Here"
$ git config --global user.email "your_email@youremail.com"
$ git config --global credential.helper osxkeychain
$ git config --global color.ui true
$ git config --global core.precomposeunicode true
$ git config --global core.quotepath false
$ ls -al ~/.ssh
$ ssh-keygen -t rsa -C "your_email@example.com"
$ eval "$(ssh-agent -s)"
```

```bash
# ~/.ssh/config
Host *
  AddKeysToAgent yes
  UseKeychain yes
  IdentityFile ~/.ssh/id_rsa
```

```bash
$ ssh-add -K ~/.ssh/id_rsa
$ pbcopy < ~/.ssh/id_rsa.pub
```

- gitignore_global

  ```bash
  # ~/.gitignore_global
  ...
  ```

  ```bash
  $ git config --global core.excludesfile ~/.gitignore_global
  ```

  

### pyenv

https://github.com/pyenv/pyenv

```bash
$ git clone https://github.com/pyenv/pyenv.git ~/.pyenv
$ echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.zshrc
$ echo 'export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.zshrc
$ echo -e 'if command -v pyenv 1>/dev/null 2>&1; then\n  eval "$(pyenv init -)"\nfi' >> ~/.zshrc
$ echo 'eval "$(pyenv init -)"' >> ~/.zshrc
$ source ~/.zshrc
$ pyenv install --list
$ pyenv install 3.7.3
$ pyenv global 3.7.3
$ pyenv rehash
$ pyenv versions
```

- pyenv-virtualenv

  ```bash
  $ git clone https://github.com/pyenv/pyenv-virtualenv.git $(pyenv root)/plugins/pyenv-virtualenv
  $ echo 'eval "$(pyenv virtualenv-init -)"' >> ~/.zshrc
  $ source ~/.zshrc
  ```

- command

  ```bash
  # 설치 가능한 목록 확인
  $ pyenv install --list
  
  # 파이썬 특정 버전 설치 및 삭제
  $ pyenv install 3.7.3
  $ pyenv uninstall 3.7.3
  
  # 현재 설치된 파이썬 버전 및 가상환경들 확인
  $ pyenv versions
  
  # 시스템 전역에 사용할 버전 선택 및 적용
  $ pyenv global 3.7.3
  $ pyenv rehash
  ```



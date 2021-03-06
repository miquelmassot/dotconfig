# Homebrew

Make sure Java is installed

    java --request

Make sure Xcode and Command Line Tools are installed

    ruby -e "$(curl -fsSkL raw.github.com/mxcl/homebrew/go)"
    brew install git tig ctags macvim rbenv ruby-build tmux s3cmd node scala gpg

# Ruby

List ruby versions available with `rbenv install -l`. Recommend installing the latest patch of 1.9.2 and 1.9.3.

# Get dotfiles

    mkdir -p ~/Documents/code && cd ~/Documents/code
    git clone git://github.com/bryanjswift/dotconfig.git
    git submodule init
    git submodule update

# bash_login

Sourcing the `bash_login` file as below can also be done in a `.profile` file
if `.bash_login` doesn't exist.

    echo "source \$HOME/Documents/code/dotconfig/config/bash_login" > ~/.bash_login

# vim

    ln -s $HOME/Documents/code/dotconfig/vim ~/.vim
    echo "source ~/.vim/vimrc" > ~/.vimrc
    echo "source ~/.vim/gvimrc" > ~/.gvimrc

# git

    echo "[include]" > ~/.gitconfig
    echo "  path = Documents/code/dotconfig/config/gitconfig" >> ~/.gitconfig
    cp ~/Documents/code/dotconfig/config/gitignore ~/.gitignore

# offlineimap and company

Make it possible to read mail locally and offline from the terminal (or
anything supporting Maildir). Open up the 'Keychain Access' app and add the
entries for IMAP and SMTP servers referenced in
[config/offlineimap/offlineimaprc](config/offlineimap/offlineimaprc) and
[config/msmtprc](config/msmtprc). IMAP entries have should have a 'where' of
`http://imap.domain.name`; SMTP entries should have a 'where' of
`smtp://smtp.domain.name`. See [Steve Losh's the Homely
Mutt](http://stevelosh.com/blog/2012/10/the-homely-mutt/), specifically the
section on [Retrieving
Passwords](http://stevelosh.com/blog/2012/10/the-homely-mutt/#retrieving-passwords)
for more information about seeting this up.

    brew install lynx msmtp mutt notmuch offlineimap openssl
    brew install keith/formulae/contacts-cli
    ln -s ~/Documents/code/dotconfig/config/mutt ~/.mutt
    ln -s ~/Documents/code/dotconfig/config/offlineimap ~/.offlineimap
    ln -s ~/Documents/code/dotconfig/config/msmtprc ~/.msmtprc
    ln -s ~/Documents/code/dotconfig/config/offlineimap/offlineimaprc ~/.offlineimaprc
    ln -s ~/Documents/code/dotconfig/certs/ca-bundle.crt /Volumes/Mail/ca-bundle.crt
    cp ~/Documents/code/dotconfig/config/notmuch-config ~/.notmuch-config

Make sure to edit ~/.notmuch-config for the correct `database.path` config value.

## Certificate Authority

[certs/ca-bundle.crt](certs/ca-bundle.crt) comes from
[curl.haxx.se][cabundle] and can be used as a certificate authority
trust file. The bundle is linked from the [curl project][curl]. The certs
are extracted fromt he Mozilla CA bundle and converted to PEM using
[mk-ca-bundle.pl][mkbundle] from the curl repository.

[cabundle]: https://curl.haxx.se/docs/caextract.html
[curl]: http://curl.haxx.se/docs/caextract.html
[mkbundle]: https://github.com/bagder/curl/blob/master/lib/mk-ca-bundle.pl

# gpg

If `gpg-agent` isn't installed and running then signing commits can get to be
quite cumbersome, particularly during `git rebase` executions. The gpg setup
and config files are cribbed from [yoshuawuyts][yoshuawuyts-gpg].

    brew install gnupg gpg-agent pinentry-mac
    mkdir ~/.gnupg
    cp config/gpg/gpg.conf config/gpg/gpg-agent.conf ~/.gnupg

[yoshuawuyts-gpg]: https://gist.github.com/yoshuawuyts/69f25b0384d41b46a126f9b42d1f9db2

# Link other dotfiles

    ln -s ~/Documents/code/dotconfig/config/rtorrent.rc ~/.rtorrent.rc
    ln -s ~/Documents/code/dotconfig/config/screenrc ~/.screenrc
    ln -s ~/Documents/code/dotconfig/config/tmux.conf ~/.tmux.conf
    ln -s ~/Documents/code/dotconfig/config/tigrc ~/.tigrc

# Get Applications from web

* [1Password](https://agilebits.com/downloads)
* [VirtualBox](https://www.virtualbox.org/wiki/Downloads)
* [Vagrant](http://downloads.vagrantup.com)
* [Transmit](http://panic.com/transmit)
* [Adobe Creative Suite](https://creative.adobe.com)
* [VMWare Fusion](http://vmware.com)

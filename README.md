# gitolite-cgit

My personal git server, [git.eda.gay](https://git.eda.gay), uses a 'vanilla' git server, and is rendered with [klaus](https://github.com/jonashaag/klaus). It uses some simple python scripts for configuration and managment - (see [git.eda.gay/git-scripts](https://git.eda.gay/git-scripts/)). This is fine for me, but is only really for one user. More complex projects, such as mediawiki, or even GNU, need to have their git server work with many users and SSH keys, with corrisponding permissions.

A solution is to use [gitolite](https://gitolite.com/gitolite/), a nice system for managing repositories and users and SSH keys. This system uses gitolite, in conjunction with [cgit](https://git.zx2c4.com/cgit/about/) to render to HTML, in a nice docker container container written by [heckyl](https://git.sr.ht/~heckyel/gitolite-cgit-docker), which adds a nice dark css theme.

Unfortunately, docker is wierd about passing through port 22 to containers, so instead we pass through port 23 and use a client configuration for easy management back to port 22.

This site can be accessed at [cgit.eda.gay](http://cgit.eda.gay).

## Client configuration

Set client config to redirect host port to 23 instead of 22:

`touch ~/.ssh/config && echo -e "Host cgit.eda.gay\n    User git\n    Port 23\n" >> ~/.ssh/config && chmod 600 ~/.ssh/config`

This redirects SSH connections to `cgit.eda.gay` to `git@cgit.eda.gay` on port 23, the correct port since docker is bad at passing through port 22.

Set client config to redirect host port to 23 instead of 22:

`touch ~/.ssh/config && echo -e "Host cgit.eda.gay\n    User git\n    Port 23\n" >> ~/.ssh/config && chmod 600 ~/.ssh/config`

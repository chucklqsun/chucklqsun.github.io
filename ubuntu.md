### install oh-my-zsh
```
0. sudo apt-get install zsh
1. curl -L https://github.com/robbyrussell/oh-my-zsh/raw/master/tools/install.sh | sh
2. chsh -s `which zsh`
3. sudo shutdown -r 0
```

### install caffee
1. in .zshrc, add below
```
export LD_LIBRARY_PATH="/usr/local/cuda-8.0/lib64"
```

2. hdf5 cannot find because you need to ln -s them
3. do not forget to use "make all -j8" when compiling

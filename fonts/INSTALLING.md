# Installation Tips

You can install all these fonts with ease using shell looping:
```shell
for d in `ls -C`; do
  cd $d
  makepkg
  sudo pacman --noconfirm -U ./*.zst
  cd ..
done
```
Note that the source checksums of Apple fonts (SF Pro, SF Mono and New York) 
often change. An insecure workaround is to pass `--skipchecksums` flag to 
`makepkg`. Be careful if you do that.

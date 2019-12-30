
```bash
cd Dockerfiles
docker build -f Dockerfile.archlinux -t controller.ubuntu .
cd ..
```

To enter the build environment.
```bash
docker run -it --rm -v "$(pwd):/controller" controller.ubuntu
```

Inside Docker:
```bash
pipenv install
pipenv shell
./ergodox.bash
```

Outside Docker:
```bash
dfu-util -D Keyboards/linux-gnu.ICED-L.gcc.ninja/kiibohd.dfu.bin 
dfu-util -D Keyboards/linux-gnu.ICED-R.gcc.ninja/kiibohd.dfu.bin 
```


## Docs:
file:///Users/ruben/Downloads/kll-spec-v0.5.7.1.pdf
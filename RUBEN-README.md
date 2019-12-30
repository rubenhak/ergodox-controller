## Preparing Environment

```bash
cd Dockerfiles
docker build -f Dockerfile.archlinux -t controller.ubuntu .
cd ..
```

To enter the build environment. Run from repo root.
```bash
docker run -it --rm -v "$(pwd):/controller" controller.ubuntu
```

Inside Docker:
```bash
cd Keyboards
pipenv install
pipenv shell
./ergodox.bash
```

Outside Docker:
```bash
dfu-util -D Keyboards/linux-gnu.ICED-L.gcc.ninja/kiibohd.dfu.bin 
dfu-util -D Keyboards/linux-gnu.ICED-R.gcc.ninja/kiibohd.dfu.bin 
```

## Editing Layout
Modify **Scan/Infinity_Ergodox/ruben**, **Keyboards/ergodox-l.bash** and **Keyboards/ergodox-r.bash**.

## Rendering LCD Images
Install once inside docker and pip env:
```bash
pip install Pillow
```

#### Default Logo
Edit **Scan/Devices/STLcd/bitmap2Struct.py**. Line 119. Modify **self.max_width = 128**.
```bash
python ../Scan/Devices/STLcd/bitmap2Struct.py -f ../Scan/Infinity_Ergodox/images/logo.bmp
```
Edit **Scan/Infinity_Ergodox/scancode_map.kll**. Line 215. Modify **STLcdDefaultImage**.

#### Layer Logos
Edit **Scan/Devices/STLcd/bitmap2Struct.py**. Line 119. Modify **self.max_width = 32**.
```bash
python ../Scan/Devices/STLcd/bitmap2Struct.py -f ../Scan/Infinity_Ergodox/images/1.bmp
```
Edit **Scan/Infinity_Ergodox/scancode_map.kll**. Line 281. Modify **STLcdNumber1**.

## KLL Spec
https://github.com/kiibohd/kll-spec

https://github.com/kiibohd/kll-spec/releases/latest
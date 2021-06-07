# luxafor-cli
python command line interface for luxafor on Linux

## Requirements
You need PyUSB installed
```sh
pip install pyusb
```

## Known/Possible issues

### Linux
- Sometimes first run doesn't work ; run it a second time.

## Install
With PyUSB you are suposed to be super user. To avoid to prompt sudo each time :
1. Create a luxafor.rules file in /etc/udev/rules.d/ :
```sh
sudo touch /etc/udev/rules.d/luxafor.rules
```

2. Add in luxafor.rules :
```
# Allow Luxafor USB control
SUBSYSTEM=="usb", ATTR{idVendor}=="04d8", ATTR{idProduct}=="f372" MODE="0664", OWNER="NAME"
```

3. Reload udev with
```sh
sudo udevadm control --reload
sudo udevadm trigger
```
4. Plug/Unplug/Re-plug the luxafor device

5. Add luxafor-light.py on your computer :
```sh
mkdir -p $HOME/bin
cp luxafor-light.py $HOME/bin/
```

## Usage
Control the colour with
```sh
python light.py green
```

### Examples :
Some aliases you could add in you dotfiles :
```sh
grep -i luxafor-light.py | cat ~/.aliases
alias l="python3 $HOME/bin/luxafor-light.py"
alias lg="python3 $HOME/ben/bin/luxafor-light.py green"
alias lr="python3 $HOME/bin/luxafor-light.py red"
alias lo="python3 $HOME/bin/luxafor-light.py off"
```

## Credits

Many thanks to :
- [xster](https://medium.com/xster-tech/using-luxafor-with-linux-53381093a40f)
- [vmitchell85](https://github.com/vmitchell85/luxafor-python/blob/master/readme.md)

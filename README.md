# ardupilot-cross-compile

## Using Release Artifacts

```bash
# run on raspberry pi with navio2
sudo mkdir -p /opt/ardupilot/custom
sudo cd /opt/ardupilot/custom

# extract archive
sudo wget https://github.com/maskinoshita/ardupilot-cross-compile/releases/download/20200525/navio2-ardupilot.zip
sudo unzip navio2-ardupilot.zip
sudo rm navio2-ardupilot.zip
sudo chmod +x ardu*

# install alternatives 
sudo update-alternatives --install /usr/bin/arducopter arducopter /opt/ardupilot/custom/arducopter 50
sudo update-alternatives --install /usr/bin/arducopter arducopter /opt/ardupilot/custom/arducopter-heli 50
sudo update-alternatives --install /usr/bin/arduplane arduplane /opt/ardupilot/custom/arduplane 50
sudo update-alternatives --install /usr/bin/ardurover ardurover /opt/ardupilot/custom/ardurover 50
sudo update-alternatives --install /usr/bin/ardusub ardusub /opt/ardupilot/custom/ardusub 50

# use emlidtool for setup
sudo emlidtool ardupilot

# change binary to custom by using set or config
sudo update-alternatives --set arducopter /opt/ardupilot/custom/arducopter
#sudo update-alternatives --config arducopter
#sudo update-alternatives --set arducopter /opt/ardupilot/custom/arducopter-heli
#sudo update-alternatives --set arduplane /opt/ardupilot/custom/arduplane
#sudo update-alternatives --set ardurover /opt/ardupilot/custom/ardurover
#sudo update-alternatives --set ardusub /opt/ardupilot/custom/ardusub
```

## Self build

```bash
# use python and ansible installed linux machine
git clone https://github.com/maskinoshita/ardupilot-cross-compile.git
cd ardupilot-cross-compile
ansible-playbook -i hosts.yml playbook.yml

# bulit binaries
ls /opt/dist/navio2-ardupilot.zip

# copy to raspberry pi with navio2
scp /opt/dist/navio2-ardupilot.zip pi@raspberypi:~

# run on raspberry with navio2
# ...
```
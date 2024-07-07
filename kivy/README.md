# Convert python code to Android apk 

This documentation will help you to build an apk file with buildozer.

## Requirement
- python3
- kivyMD
- builozer
- in your project root rename your python file to ```main.py``` , your python file which content your main code. 

## Installation

execute those commandes in your terminal line by line. It may be ask for root permission

```python
apt install python3-pip

pip install kivy

pip install buildozer

sudo apt update

apt install -y git zip unzip openjdk-17-jdk python3-pip autoconf libtool pkg-config zlib1g-dev libncurses5-dev libncursesw5-dev libtinfo5 cmake libffi-dev libssl-dev

pip install --upgrade Cython==0.29.33

export PATH=$PATH:~/.local/bin/
```

## Buildozer

Create ```buildozer.spec``` file

```
buildozer init
```

Customize the file ```buildozer.spec``` by open it into your favorite editor.

Basic config for ```buildozer.spec```


#### line 4
title = Makan Web

#### line 7
package.name = mkpackage

#### line 10
package.domain = mkpackage.test

#### line 16
you can add more other extension.

source.include_exts = py,png,jpg,kv,atlas 

#### line 25
file to exclude. You can uncomment the line and add more.

#source.exclude_dirs = tests, bin, venv

#### line 40
You add all package required by your project

requirements = python3,kivy,python-dotenv

#### line 50
uncomment the line to customize the icon

#icon.filename = %(source.dir)s/data/icon.png



## Generate apk file

After customization of your ```buildozer.spec```. When you are ready, run this command to generate apk file. It may be take a long time depend on your connection.


```
buildozer -v android debug
```

--------------------------
If you done without an error, you will find your apk file in the ```bin``` directory into your project root




# Other resources

- Install buildozer https://buildozer.readthedocs.io/en/latest/installation.html 
- Edit ```buildozer.spec``` https://buildozer.readthedocs.io/en/latest/specifications.html 
- Build apk https://kivy.org/doc/stable/guide/packaging-android.html



# tigro-fedora-kickstart
Some kickstarts to creare custom Live Images

# What changed?
1. Added Tigro copr repo: tigro/fedora45
2. Added Google Chrome, Microsoft Edge, OnlyOffice
3. Added openh264 to disk
4. Added new GNOME extensions: dash-to-panel, dash-to-dock, ddterm, clipboard-history, desktop-icons-ng, arcmenu
5. Added desktop style configurator from MSVSPhere
6. Added Yandex (disk, mail, calendar) support in Gnome Online Accounts
7. Sphere Image Writer (fork of Fedora Media Writer)
8. Added Multimedia and other

# Warning
To avoid high grade python developers languages errors set up `en_US.UTF-8` locale for host system:

```
$ localectl
System Locale: LANG=en_US.UTF-8
    VC Keymap: us
   X11 Layout: us
    X11 Model: pc105
$ locale
LANG=en_US.UTF-8
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=
```

# Prepare
```
sudo dnf copr enable tigro/fedora45

sudo dnf -y install lorax lorax-templates-generic anaconda anaconda-core \
    anaconda-gui anaconda-install-env-deps anaconda-live anaconda-tui \
    anaconda-webui anaconda-widgets kdump-anaconda-addon \
    libreport-anaconda livesys-scripts --refresh
```

# How to build
```
sudo livemedia-creator \
    --ks tigro-flat-fedora-live-workstation.ks \
    --resultdir ./fedora-workstation/ \
    --project="Fedora Tigro Workstation" \
    --make-iso --volid "Fedora 45 x86_64" \
    --iso-only \
    --iso-name Fedora-Tigro-Workstation-Live-45.$(date +%Y%m%d)-x86_64-1.1.x86_64.iso \
    --releasever=45 \
    --nomacboot \
    --extra-boot-args "rootfstype=auto ro rhgb rd.luks=0 rd.md=0" \
    --lorax-templates /usr/share/lorax/templates.d/99-generic/ \
    --no-virt
```

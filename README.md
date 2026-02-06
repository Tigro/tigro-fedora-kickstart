# tigro-fedora-kickstart
Some kickstarts to creare custom Live Images

# Prepare
```
sudo dnf copr enable tigro/fedora43

sudo dnf -y install lorax lorax-templates-generic anaconda anaconda-core \
    anaconda-gui anaconda-install-env-deps anaconda-live anaconda-tui \
    anaconda-user-help anaconda-webui anaconda-widgets kdump-anaconda-addon \
    libreport-anaconda livesys-scripts --refresh
```

# How to build
```
sudo livemedia-creator \
    --ks tigro-flat-fedora-live-workstation.ks \
    --resultdir ./fedora-workstation/ \
    --project="Fedora Tigro Workstation" \
    --make-iso --volid "Fedora 43 x86_64" \
    --iso-only \
    --iso-name Fedora-Tigro-Workstation-Live-43.20260205-x86_64-1.1.x86_64.iso \
    --releasever=43 \
    --nomacboot \
    --extra-boot-args "rootfstype=auto ro rhgb rd.luks=0 rd.md=0" \
    --lorax-templates /usr/share/lorax/templates.d/99-generic/ \
    --no-virt
```

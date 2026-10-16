# 🚀 lexerBSD

Welcome to **lexerBSD**! This is my custom daily-driver operating system built on top of **FreeBSD 15.1**. 

Linux is cool, but I wanted to build something fast, clean, and customized exactly the way I like it for coding and messing around. If you are tired of systemd bloat and want a super lightweight workstation, this is it.

---

## 🔥 What's Inside?

*   **FreeBSD 15.1 Base:** Rock-solid stability, insane networking, and no weird background telemetry.
*   **Custom XFCE Desktop:** Super fast, looks clean, and won't eat up your RAM like GNOME or Electron apps do.
*   **Drivers Pre-baked:** Graphics drivers (`drm-kmod`) are already loaded so AMD, Intel, and Radeon GPUs actually work right out of the box.
*   **ZFS File System:** Native OpenZFS because losing data because of a crash sucks.
*   **Dev Essentials:** Automatically ships with `git`, `nano`, and custom terminal configs.

---

## 🏗️ How the Magic Happens

The files in this repo act as a "skeleton" overlay. The build script grabs raw FreeBSD, dumps these configs on top, sandboxes into it to download the desktop environment, and spits out a bootable disc.

```text
/tmp/myos/
├── iso/
│   ├── etc/
│   │   ├── motd              # The custom "hello" message when you open a terminal
│   │   └── rc.conf           # Tells the OS to boot the desktop instead of a blank screen
│   └── usr/share/skel/
│       └── dot.xinitrc       # Bootstraps the XFCE desktop environment
└── packages.txt              # The shopping list of apps baked into the ISO
```

---

## 🛠️ Build it Yourself

If you have a FreeBSD machine (or a VM) and want to spin your own ISO of this, it's pretty simple:

### 1. Grab the compiler tools
```bash
pkg install -y git cdrkit-genisoimage
```

### 2. Run the build script
Make sure your files match the folder tree above, then fire up the compiler:
```bash
sh /tmp/myos/build_lexerbsd.sh
```

Go grab a coffee. The script will sandbox, download all 700+ desktop packages, compress the filesystem, and leave a shiny new `**lexerBSD.iso**` waiting for you in `/tmp/myos/`.

---

## 👥 Contribs & Breaking Things

This is mostly a passion project, but if you want to audit my messy config files, optimize something, or submit a pull request to make it better, go for it! Open an issue or hit me with a PR.

## 📄 License
Standard **BSD 2-Clause License**. Do whatever you want with it, just don't blame me if it blows up your virtual machine.


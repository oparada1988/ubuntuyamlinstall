# ⚙️ Ubuntu Autoinstall YAML Editor

A zero-dependency, single-file browser-based editor for creating and editing [Ubuntu Autoinstall](https://ubuntu.com/server/docs/install/autoinstall) (`autoinstall.yaml`) configuration files — no server, no install, no build step required.

![Ubuntu](https://img.shields.io/badge/Ubuntu-20.04%20%7C%2022.04%20%7C%2024.04-E95420?style=flat-square&logo=ubuntu&logoColor=white)
![HTML](https://img.shields.io/badge/HTML-Single%20File-58a6ff?style=flat-square&logo=html5&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-3fb950?style=flat-square)

---

## ✨ Features

- **8 configuration sections** covering all major autoinstall directives
- **Live YAML preview** with syntax highlighting as you type
- **Raw Edit tab** for direct YAML manipulation
- **Load existing files** via drag-and-drop or file picker
- **Download** the finished `autoinstall.yaml` or copy it to clipboard
- Fully **offline capable** — just open the HTML file in any modern browser
- No dependencies, no npm, no build tools

---

## 🖥️ Screenshot

> _A dark-themed three-panel layout: section navigator → form editor → live YAML preview_

---

## 🚀 Usage

### Option A — Open directly
```bash
# Clone the repo
git clone https://github.com/your-username/ubuntu-autoinstall-editor.git

# Open in browser
open ubuntu-yaml-editor.html          # macOS
xdg-open ubuntu-yaml-editor.html      # Linux
start ubuntu-yaml-editor.html         # Windows
```

### Option B — Serve locally
```bash
python3 -m http.server 8080
# then visit http://localhost:8080/ubuntu-yaml-editor.html
```

### Option C — GitHub Pages
Fork this repo and enable **GitHub Pages** on the `main` branch. The editor will be live at:
```
https://your-username.github.io/ubuntu-autoinstall-editor/ubuntu-yaml-editor.html
```

---

## 📋 Configuration Sections

| Section | Directives Covered |
|---|---|
| **Identity** | `hostname`, `timezone`, Ubuntu version |
| **Locale & Keyboard** | `locale`, `keyboard.layout`, `variant`, `toggle` |
| **Network** | `network` (netplan), DHCP4 / static IP, gateway, DNS |
| **Storage** | `storage.layout` (LVM, ZFS, direct, custom), disk, wipe, swap |
| **Users & SSH** | `user-data.users`, `ssh` (install, password auth, authorized keys) |
| **Packages** | `packages`, `snaps`, `package_update`, `package_upgrade` |
| **Commands** | `early-commands`, `late-commands` |
| **Misc** | `shutdown`, `apt` mirror, `source`, custom YAML block |

---

## 📦 Loading an Existing File

Drag and drop any existing `autoinstall.yaml` onto the **drop zone** in the Identity section, or click it to browse. The editor will parse and populate the form fields automatically. You can also switch to the **Raw Edit** tab for full manual control.

---

## 🗂️ Output Format

The generated file follows the [Ubuntu Autoinstall reference](https://ubuntu.com/server/docs/install/autoinstall-reference) schema and starts with the required `#cloud-config` header:

```yaml
#cloud-config
autoinstall:
  version: 1
  hostname: ubuntu-server
  locale: en_US.UTF-8
  keyboard:
    layout: us
  storage:
    layout:
      name: lvm
  ssh:
    install-server: true
  ...
```

---

## 🔧 Deploying the Generated File

Place `autoinstall.yaml` on a web server or USB drive accessible during Ubuntu installation. When booting the Ubuntu installer, pass the autoinstall URL on the kernel command line:

```
autoinstall ds=nocloud-net;s=http://your-server/
```

Or for local USB-based installs, place it alongside a `meta-data` file (can be empty) in the root of a FAT32 partition labeled `CIDATA`.

---

## 🤝 Contributing
If someone wants to be a developer on this project. Join in.


Pull requests are welcome. For larger changes, please open an issue first to discuss what you'd like to change.

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/my-feature`)
3. Commit your changes (`git commit -m 'Add my feature'`)
4. Push to the branch (`git push origin feature/my-feature`)
5. Open a Pull Request

---

## 📄 License

MIT — see [LICENSE](LICENSE) for details.

---

## 💛 Support

If you find this tool useful, consider supporting the project:

👉 **[Support this project - Visit this Ad-Link](https://onandasmilee.com?j4PmO=1248945)** ← _(add your link here)_

---

## 🔗 Resources

- [Ubuntu Autoinstall Documentation](https://ubuntu.com/server/docs/install/autoinstall)
- [Autoinstall Reference](https://ubuntu.com/server/docs/install/autoinstall-reference)
- [Netplan Documentation](https://netplan.io/reference)
- [Cloud-init Docs](https://cloudinit.readthedocs.io/)

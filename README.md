# Coding Mode Launcher (Windows)

Coding Mode Launcher is a lightweight **Windows HTA (HTML Application)** that helps you start your entire development environment with a single click.

It provides a small interactive GUI with **checkboxes** to choose which applications to open, all **pre-checked by default**, making it fast and flexible for daily coding workflows.

---

## ✨ Features

- ✅ One-click launcher for your coding environment
- ✅ Interactive GUI with checkboxes (no command-line input)
- ✅ All apps are pre-selected by default
- ✅ Supports **Desktop apps** and **Microsoft Store (UWP) apps**
- ✅ Clean, small window size
- ✅ Custom styling (CSS, background image, icons)
- ✅ Automatically closes after launching apps

---

## 🧰 Supported Applications (Examples)

You can easily configure it to launch:
- Laragon
- Visual Studio Code
- Command Prompt / Terminal (auto `cd` to project folder)
- HeidiSQL
- Web Browser (Chrome, Edge, etc.)
- Microsoft Store apps:
  - WhatsApp
  - Spotify
  - Mozilla Thunderbird
  - Any other UWP app

---

## 🚀 How It Works

This launcher uses:

* **HTA (HTML Application)** for the UI
* **VBScript** for launching applications
* **explorer.exe shell:appsFolder\<AppID>** for Microsoft Store apps

When you click **Launch**, the script:

1. Checks which applications are selected
2. Launches each selected application
3. Automatically closes the launcher window

---

## 🛠️ How to Use

### 1. Download or Clone

```bash
git clone https://github.com/arhakim/coding-mode-launcher.git
```

---

### 2. Edit Application Paths

Open `index.hta` and update paths according to your system.

#### Desktop Applications Example

```vbscript
WshShell.Run """C:\laragon\laragon.exe""", 1, False
```

```vbscript
WshShell.Run """C:\Program Files\HeidiSQL\heidisql.exe""", 1, False
```

---

### 3. Launching Microsoft Store Apps (UWP)

Microsoft Store apps do **not** have a direct `.exe` path.
You must use their **AppID**.

#### Find AppID using PowerShell

```powershell
Get-StartApps | Where-Object {$_.Name -like "*Spotify*"}
```

Example output:

```text
Spotify   SpotifyAB.SpotifyMusic_zpdnekdrzrea0!Spotify
```

#### Use it in the script

```vbscript
WshShell.Run "explorer.exe shell:appsFolder\SpotifyAB.SpotifyMusic_zpdnekdrzrea0!Spotify", 1, False
```

---

### 4. Run the Launcher

Double-click:

```text
index.hta
```

> ⚠️ Windows may show a security warning for HTA files.
> Click **More info → Run anyway**.

---

## 🎨 Customization

### Change Window Size

```vbscript
window.resizeTo 450, 400
```

### Center Window

```vbscript
window.moveTo (screen.availWidth-450)/2, (screen.availHeight-400)/2
```

### Change Background Image

```css
background-image: url("C:\path\to\background.jpg");
```

### Add / Remove Applications

* Add a checkbox in HTML
* Add a matching `If ... Then WshShell.Run` block in VBScript

---

## 🧠 Why HTA?

HTA allows:

* Native Windows execution
* HTML + CSS styling
* VBScript automation
* No extra dependencies
* No visible CMD windows

Perfect for small productivity tools.

---

## 📜 License

MIT License
Free to use, modify, and distribute.

---

## 🤝 Contributions

Pull requests are welcome.
Feel free to improve UI, add features, or optimize scripts.

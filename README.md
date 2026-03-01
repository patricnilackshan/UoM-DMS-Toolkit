<div align="center">

# 🎓 UoM DMS Toolkit

*Data-free downloads, uploads & sharing for UoM students*

**Torrents · YouTube · M3U8 · Direct Links**

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/patricnilackshan/UoM_DMS_Toolkit/blob/main/UoM_DMS_Toolkit.ipynb)
&nbsp;
[![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-Workflow-2088FF?logo=githubactions&logoColor=white)](../../actions/workflows/dms.yml)

<img src="https://visitor-badge.laobi.icu/badge?page_id=patricnilackshan.UoM_DMS_Toolkit" align="right"/>

</div>

---

## Features

| | Feature |
|---|---|
| 📥 | Download from direct links, YouTube, M3U8 streams, and Magnet/Torrent links |
| 📤 | Upload files directly to your UoM DMS account via WebDAV |
| 🔗 | Share uploaded files and get a public DMS link instantly |
| 📋 | View all shares in your DMS account |
| 🗑️ | Delete shares by Share ID |
| 🖴 | Mount DMS as a local drive on Windows & Linux |
| ⚙️ | GitHub Actions workflow — download & upload without opening a browser |

---

## Usage

### 🗒️ Google Colab Notebook

The easiest way to use the toolkit. No setup required.

1. Open the notebook in [Google Colab](https://colab.research.google.com/github/patricnilackshan/UoM_DMS_Toolkit/blob/main/UoM_DMS_Toolkit.ipynb)
2. Run the **Sign in** cell — enter your DMS username & password (dependencies install automatically)
3. Run **Download**, **Upload**, **Share** cells in order

### ⚙️ GitHub Actions Workflow

Download any file and upload it to DMS directly from GitHub — no Colab needed.

1. Go to **Actions** → **Download and Upload to DMS** → **Run workflow**
2. Fill in your DMS username, password, and the download link
3. The workflow will download the file, zip it if multiple files are produced, upload to DMS, and print the shareable link

**Supported link types:**

| Link | Handler |
|---|---|
| `magnet:?xt=urn:btih:...` | libtorrent |
| `*.m3u8` | ffmpeg |
| `youtube.com` / `youtu.be` | yt-dlp |
| Any HTTP/HTTPS URL | requests |

---

## Mount DMS as a Local Drive

**Windows 🪟** — Run in Command Prompt:
```
net use Z: https://dms.uom.lk/remote.php/webdav/ /user:<userName> <userPassword>
```

**Linux 🐧** — Enter in File Manager → *Connect to Server*:
```
davs://dms.uom.lk/remote.php/webdav/
```

---

<div align="center">

© **Patric Nilackshan** · [pnilackshan@gmail.com](mailto:pnilackshan@gmail.com)

</div>

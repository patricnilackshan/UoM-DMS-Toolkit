# Nextcloud / DMS API Reference

> Variables are written inside angle brackets `< >`

---

## 📥 Download File

```bash
curl -L -O -J <downloadLink>
```

---

## 📺 Download M3U8 Stream to MP4

```bash
ffmpeg -threads 8 -i <downloadLink> -c copy <fileName>
```

---

## 🌐 Download YouTube Video

```bash
yt-dlp -f "bestvideo+bestaudio/best" --merge-output-format mp4 -o "%(title)s.%(ext)s" <youtubeLink>
```

---

## 🧲 Download Torrent / Magnet Link

```bash
aria2c --seed-time=0 <magnetLink>
```

---

## 📤 Upload File to DMS

```bash
curl -u <userName>:<userPassword> -T <fileName> "https://dms.uom.lk/remote.php/webdav/"
```

---

## 🔗 Share File from DMS

```bash
curl -u <userName>:<userPassword> \
  -X POST \
  -d "path=/<fileName>&shareType=3&permissions=1" \
  -H "OCS-APIRequest: true" \
  "https://dms.uom.lk/ocs/v2.php/apps/files_sharing/api/v1/shares?format=json"
```

---

## 📋 Get All Shares

```bash
curl -u <userName>:<userPassword> \
  -X GET \
  -H "OCS-APIRequest: true" \
  "https://dms.uom.lk/ocs/v2.php/apps/files_sharing/api/v1/shares?format=json"
```

---

## 🗑️ Delete a Share

```bash
curl -u <userName>:<userPassword> \
  -X DELETE \
  -H "OCS-APIRequest: true" \
  "https://dms.uom.lk/ocs/v2.php/apps/files_sharing/api/v1/shares/<share_ID>"
```

---

## 🖴 Mount DMS as a Local Drive

**Windows 🪟** — Run in Command Prompt:
```
net use Z: https://dms.uom.lk/remote.php/webdav/ /user:<userName> <userPassword>
```

**Linux 🐧** — Enter in File Manager → *Connect to Server*:
```
davs://dms.uom.lk/remote.php/webdav/
```

# 🚀 Republic Network v0.2.1 Update Guide

This guide is for **Republic Network** validators who have installed their nodes manually (without Cosmovisor) and need to upgrade to the v0.2.1 version quickly and safely.

---

## 🛠 Step-by-Step Upgrade Instructions

### 1. Stop the Node Service
Ensure a clean environment by stopping the active service:
```bash
sudo systemctl stop republicd
```

2. Download and Verify the New Binary
Move to your binary directory and download the v0.2.1 release:
```bash
cd /usr/local/bin
sudo wget -O republicd_v0.2.1 [https://github.com/RepublicAI/networks/releases/download/v0.2.1/republicd-linux-amd64](https://github.com/RepublicAI/networks/releases/download/v0.2.1/republicd-linux-amd64)
```

# SHA256 Checksum Verification ✅
```bash
echo "d10991b623fa62ee0f3c42ad15abbaa246f89d73a82736fad090e607b7cc4b8f  republicd_v0.2.1" | sha256sum -c
```
Note: You should see republicd_v0.2.1: OK as output.

3. Deploy and Restart
Grant execution permissions, backup your old binary and activate the new version:
```bash
sudo chmod +x republicd_v0.2.1
sudo mv republicd republicd_backup_$(date +%F)
sudo mv republicd_v0.2.1 republicd
```
# Reload configuration and fire up the node
```bash
sudo systemctl daemon-reload
sudo systemctl restart republicd
```
📊 Status Check
Monitor your node to ensure blocks are being finalized:
```bash
sudo journalctl -u republicd -f -o cat
```
(Pro Tip:In version v0.2.1 the republicd version command might return an empty string.As long as you see finalized block or committed state in your logs your node is healthy and up to date)


Twitter : https://x.com/GunahkarCasper

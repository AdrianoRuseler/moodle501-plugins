Here is the one-liner to add to your server's update script:
```bash
curl -s https://api.github.com/repos/AdrianoRuseler/moodle501-plugins/releases/latest \
| grep "browser_download_url" \
| grep "tar.xz" \
| cut -d : -f 2,3 \
| tr -d \" \
| wget -qi - -O plugins-update.tar.xz
```


## Integrated "Update & Deploy" Script

```bash
#!/bin/bash
set -e

# 1. Download the highly compressed archive
echo "📥 Fetching latest .tar.xz release..."
# (Insert the curl command above here)

# 2. Extract specifically using XZ
echo "📦 Decompressing plugins..."
mkdir -p /tmp/moodle_update
tar -xJf plugins-update.tar.xz -C /tmp/moodle_update/

# 3. Apply updates to the live Moodle directory
echo "📂 Syncing files to /var/www/html..."
sudo rsync -av --delete /tmp/moodle_update/moodle/ /var/www/html/

# 4. Moodle CLI Tasks
echo "🆙 Upgrading Database..."
docker exec -u www-data moodle-cron php /var/www/html/admin/cli/upgrade.php --non-interactive --allow-unstable

echo "🧹 Clearing Cache..."
docker exec -u www-data moodle-cron php /var/www/html/admin/cli/purge_caches.php

# 5. Cleanup
rm -rf /tmp/moodle_update plugins-update.tar.xz
echo "✅ Site updated successfully!"
```

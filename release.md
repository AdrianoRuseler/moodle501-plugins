Here is the one-liner to add to your server's update script:
```bash
curl -s https://api.github.com/repos/AdrianoRuseler/moodle501-plugins/releases/latest \
| grep "browser_download_url" \
| cut -d : -f 2,3 \
| tr -d \" \
| wget -qi - -O plugins-update.zip
```


## Integrated "Update & Deploy" Script

```bash
#!/bin/bash
set -e

# 1. Download latest build
echo "📥 Downloading latest plugin build..."
curl -s https://api.github.com/repos/AdrianoRuseler/moodle501-plugins/releases/latest \
| grep "browser_download_url" \
| cut -d : -f 2,3 \
| tr -d \" \
| wget -qi - -O plugins-update.zip

# 2. Extract and Sync
echo "📂 Unzipping and updating files..."
unzip -o plugins-update.zip -d /tmp/moodle_update
# Use rsync to merge the 'moodle' folder into your live site
sudo rsync -av /tmp/moodle_update/moodle/ /var/www/html/

# 3. Moodle Housekeeping
echo "🆙 Running Moodle Database Upgrade..."
docker exec -u www-data moodle-cron php /var/www/html/admin/cli/upgrade.php --non-interactive --allow-unstable

echo "🧹 Purging Cache..."
docker exec -u www-data moodle-cron php /var/www/html/admin/cli/purge_caches.php

# 4. Cleanup
rm -rf /tmp/moodle_update plugins-update.zip
echo "✅ Update to version $(date +%Y%m%d) successful!"
```

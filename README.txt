LibreTime 4.5.0 + Icecast 2.5.0 + Liquidsoap 2.0.7

Contents
- libretime_4.5.0+icecast2.5.0+liquidsoap2.0.7-0local1_amd64.deb
- libretime_4.5.0+icecast2.5.0+liquidsoap2.0.7-0local1_amd64.buildinfo
- libretime_4.5.0+icecast2.5.0+liquidsoap2.0.7-0local1_amd64.changes

What this package includes
- LibreTime 4.5.0
- Liquidsoap 2.0.7+git@0ed7ed45 bundled in the package
- Icecast 2.5.0 bundled in the package

Test status
- The package was rebuilt locally in WSL Ubuntu.
- It was installed and tested over SSH on Ubuntu 20.04.6 LTS server
- Package install worked.
- libretime-install worked.
- Database migration worked.
- libretime.target started.
- Icecast, API, Liquidsoap, Playout, and Worker services were all running.

Target system
- Ubuntu 20.04.x amd64

Installation
1. Copy the .deb file to the Ubuntu 20.04 server.
2. Install the package with apt:
wget https://download1655.mediafire.com/5ysib5b0xq6goXRw8PkN2pRDRUV6V2pTs_gEHbUDcWgezbCIHsMRNJ5cwfHv8TKjhvZxE1hFpGjCXrXhHtV_pGGrM4c3bFLQ7bVEy4GMVvwV0zEsE00Yl4skY6M25jK06yF7I47sHJG64URCMgQ9LGPHdcLRfY_WV0ELTxOWzaFI/xcq0z02sexib524/libretime_4.5.0%2Bicecast2.5.0%2Bliquidsoap2.0.7-0local1_amd64.deb

   sudo apt install ./libretime_4.5.0+icecast2.5.0+liquidsoap2.0.7-0local1_amd64.deb
(find the download link below)

3. Run the installer.

   Important:
   The tested default nginx config listens on port 8080, so pass the public URL with :8080 unless you have already changed the web port.

   sudo libretime-install http://YOUR_SERVER_IP_OR_HOSTNAME:8080

4. Run database migrations:

   sudo -u libretime libretime-api migrate

5. Start LibreTime:

   sudo systemctl start libretime.target

6. Check services:

   sudo systemctl status icecast2
   sudo systemctl status libretime-api
   sudo systemctl status libretime-liquidsoap
   sudo systemctl status libretime-playout
   sudo systemctl status libretime-worker

7. Open LibreTime in your browser:

   http://YOUR_SERVER_IP_OR_HOSTNAME:8080

Quick verification commands
- Liquidsoap version:

  /usr/bin/liquidsoap --check 'print(liquidsoap.version) shutdown()'

  Expected output:
  2.0.7+git@0ed7ed45

- Icecast version:

  /usr/local/bin/icecast -v

  Expected output:
  Icecast 2.5.0

Notes
- The package bundles custom Icecast and Liquidsoap binaries.
- The package was tested on Ubuntu 20.04, not on newer Ubuntu releases.
- If you want LibreTime on port 80 instead of 8080, adjust the nginx site after install.
- The .buildinfo and .changes files are included for release/build metadata. End users normally only need the .deb.
While I'm working on the Github fork I have the .deb file publicly available on mediafire here: https://www.mediafire.com/folder/xaimkir95lcd3/Libretime-4.5.0-Icecast-2.5.0-Liquidsoap-2.0.7

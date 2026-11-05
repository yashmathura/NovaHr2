NOVAHR — CAMERA / GPS ATTENDANCE FIX
===================================

Files changed:
- templates/attendance.html
  * Loads the face-api library from the project's existing local static/vendor/face-api.js file.
  * Adds a cache-busting version query to the attendance scripts.
  * Includes a separate Check location button.
- templates/static/js/face-attendance.js
  * Initializes safely whether the script runs before or after DOMContentLoaded.
  * Shows explicit script, camera, GPS, and face-model errors in the page.
  * Handles camera and GPS permission errors with actionable messages.
  * Avoids silently leaving the buttons/status in their initial state.

Install:
1. Back up your existing project folder.
2. Extract this ZIP over your existing project, keeping the same folder structure.
3. Stop the Django server with Ctrl+C, then restart it using your normal command (for example: python manage.py runserver).
4. Open http://127.0.0.1:8000/attendance/ and hard-refresh with Ctrl+Shift+R.
5. Click Start camera and allow Camera permission. Click Check location and allow Location permission.

Important:
- The site must be opened through http://127.0.0.1:8000/ or HTTPS, not by double-clicking an HTML file.
- Face recognition model weight files are still fetched from jsDelivr. An internet/network policy that blocks jsDelivr will show a model-download error even if the camera opens. The local face-api JavaScript library itself is bundled in this project.
- GPS depends on browser permission and the device's location services. On desktop, location accuracy can be coarse or unavailable.
- Verify the employee face profile is enrolled before attempting attendance.
- This package was syntax-checked; it could not be tested against your local database, browser permissions, camera hardware, or network from this environment.

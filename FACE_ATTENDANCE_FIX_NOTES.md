# NovaHR face attendance fixes

## Changes
- Fixed the attendance JavaScript initialization callback so automatic camera startup and button listeners are registered without a syntax error.
- Admin/HR face enrollment now requires a blink challenge before the face is captured and saved.
- Employee check-in/check-out now requires a blink challenge before face matching and GPS capture.
- Employee manual `WEB` attendance POSTs are blocked; employees must use the live face attendance flow.
- Face enrollment is restricted to Admin/HR accounts.
- Added clearer liveness error messages and a server-side requirement for the liveness field.

## Apply
1. Back up your current project and database.
2. Extract this ZIP into a new folder, or replace the matching files in your existing project.
3. Keep your existing `.env`, database and local settings; do not overwrite them with any sample values.
4. Activate your virtual environment, install requirements if needed, then run `python manage.py check` and `python manage.py runserver`.
5. Hard-refresh the browser (Ctrl+Shift+R). As Admin/HR, open Employees > Capture face, allow camera, then click Capture & save profile and blink when prompted.
6. As an employee, open Attendance, start the camera, and blink once when asked before check-in/out.

## Security limitation
Blink detection helps reject a still photo in the normal browser workflow, but it is not certified anti-spoofing and is not secure against a prerecorded video, browser/devtools manipulation, or direct API requests. For production payroll attendance, use a server-verified liveness/anti-spoof SDK or managed device kiosk, enforce a server-side geofence, and audit manual overrides. A browser-supplied liveness flag alone is not proof of liveness.

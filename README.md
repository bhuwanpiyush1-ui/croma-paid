# gv_chek_api_fix

## Device license system

The app creates a persistent browser Device ID and checks it through `/api/license`.
The balance-check endpoint also enforces the same allowlist, so bypassing the
lock screen does not grant API access.

1. Open the deployed app once and copy the Device ID shown on the lock screen.
2. Add it to `private/licenses.json`:

   ```json
   {
     "devices": [
       "PASTE_DEVICE_ID_HERE"
     ]
   }
   ```

3. Redeploy. Removing a device ID revokes access on the next license check.

If browser storage is cleared, the app creates a new Device ID that must be
approved again.
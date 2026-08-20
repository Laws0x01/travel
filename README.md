# The Brandon Beach Index

A password-protected, single-page comparison of beach resorts — all-inclusive and
room-only — across Mexico, Central America, the Caribbean, the Bahamas, Hawaii, and
the US Gulf, Florida, and California coasts. Rated by real traveler reviews, with
prices, amenities, and flight times from DFW.

The published site is just `index.html`: a password page containing the full report
**encrypted with AES-256-GCM**. The password decrypts it in the browser (WebCrypto,
PBKDF2-SHA256 at 600k iterations). Without the password, neither the site nor this
repository exposes any readable content. There is no recovery — if the password is
lost, re-encrypt with a new one.

## Updating the site (from the local `build/` folder, which is not committed)

1. Edit data in `build/data/*.json` (one file per region) or the page in `build/template.html`.
2. Rebuild the report and CSV export:

   ```
   python3 build/merge.py
   ```

3. Re-encrypt into `index.html`:

   ```
   node build/encrypt.js
   ```

   Reads the password from `build/.password` (gitignored, one line). Pass the
   password as an argument instead to set or change it: `node build/encrypt.js '<new password>'`
   (then update `build/.password` to match).

4. Commit and push `index.html`.

`build/resorts.csv` is the spreadsheet export of the full table.

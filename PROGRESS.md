# BusTrack HRIS — Progress

Last updated: 2026-11-19

## Current status
- Step 1: Requirements and route decision — complete.
- Step 2: React/Vite scaffold, Supabase schema draft and initial responsive UI — partial.
- Step 3: Sign-in, role-aware workspace, shift clock-in/out and GPS pings — implemented in code; not build-tested or verified against live Supabase.
- Step 4 onward: incomplete.

## Recently implemented
- Staff sign-in and profile role loading.
- Driver/conductor bus and route selection; inspector route selection.
- GPS captured at shift start/end and watched during active shift.
- Admin operations map, active shifts, staff profile list, shift records.
- Admin bus registration, bus assignment, secure Edge Function call for creating non-admin staff.
- Attendance date-range report and CSV export.
- Payroll settings, semi-monthly payroll period helper and payroll generation from completed shifts.
- Responsive interface.

## Not yet verified or complete
- No successful `npm install` / `npm run build` has been confirmed.
- Migration has not been applied to the intended Supabase project.
- Edge Function `admin-create-user` has not been deployed or tested.
- RLS/security policies require a thorough review before production.
- Passenger-facing live map exists in `src/Passenger.jsx`; it uses the original OpenStreetMap street layer. Live data integration still needs browser verification.
- PITX ↔ MOA route geometry and stop coordinates remain unverified; do not present estimated ETA as verified.
- No Netlify deployment has been verified.

## Next actions
1. Build/test the frontend and fix compile/runtime issues.
2. Confirm the intended Supabase project before applying the migration.
3. Review and harden RLS and add the secure admin Edge Function.
4. Verify passenger map, Supabase public bus-location view, and route geometry.
5. Configure deployment environment variables and deploy.


## Latest update — Step 6: Set Passenger Map to Default
- Status: done (GitHub source updated).
- Files changed: `src/Passenger.jsx`, `src/styles.css`, `PROGRESS.md`.
- Decisions: Passenger map now uses only the Default OpenStreetMap street layer; removed Satellite/Terrain switching controls. Existing live bus markers, GPS refresh, and complaint form remain unchanged.
- Open issues: Live Netlify page could not be inspected through the available page viewer; build and deployment status are unverified.


## Latest update — Step 7: Match Passenger Map to Reference Style
- Status: done (GitHub source updated; production deployment not yet verified).
- Files changed: `src/Passenger.jsx`, `PROGRESS.md`.
- Decisions: Replaced the plain OpenStreetMap raster layer with CARTO Voyager tiles for a more Google Maps-like street presentation with clearer road and place labels. Set the no-bus fallback map center to the Naic/Ternate area ([14.32, 120.78]); active bus GPS still controls the map view through FitBuses.
- Open issues: Confirm the CARTO tiles load in the deployed browser and visually compare with the supplied reference. Netlify deployment/build not yet verified.

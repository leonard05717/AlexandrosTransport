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
- Passenger-facing live map exists in `src/Passenger.jsx`; map-layer selector now supports Default (initial), Satellite, and Terrain. Live data integration and map-layer rendering still need browser verification.
- PITX ↔ MOA route geometry and stop coordinates remain unverified; do not present estimated ETA as verified.
- No Netlify deployment has been verified.

## Next actions
1. Build/test the frontend and fix compile/runtime issues.
2. Confirm the intended Supabase project before applying the migration.
3. Review and harden RLS and add the secure admin Edge Function.
4. Verify passenger map layers, Supabase public bus-location view, and route geometry.
5. Configure deployment environment variables and deploy.


## Latest update — Step 5: Passenger map layers
- Status: done (code updated; browser/build verification pending).
- Files changed: `src/Passenger.jsx`, `src/styles.css`, `PROGRESS.md`.
- Decisions: Default street map is selected on page load; Satellite and Terrain are selectable. Existing bus markers, GPS refresh, and complaint form are preserved. Terrain uses Esri World Topographic Map; Satellite uses Esri World Imagery; Default uses OpenStreetMap.
- Open issues: Verify all three layers render in the deployed browser and confirm provider usage/attribution requirements for production traffic.

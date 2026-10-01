TRÄNINGSAPPEN PWA v5

V5 bygger om grunden från en ren Bulgaren-app till en träningsplattform.

Nyheter:
- Ny programöversikt som startsida.
- Bulgaren ligger som valbart träningsprogram.
- Ingen "kommer snart"-text eller tomma programkort.
- Global översikt: antal pass, total volym, träningsdagar senaste 30 dagarna och senaste pass.
- Enkel kalenderöversikt över senaste 28 dagarna.
- Ny generell datamodell under nyckeln trainingAppDataV5.
- Automatisk migrering av befintlig Bulgaren-data från v4.
- Bulgaren behåller sin historik, statistik, progression, pågående pass och inställningar.
- Första grunden för egna program: namn + valfria set med reps och procent.
- Struktur för att senare kunna lägga till fler program utan att bygga om kärnan igen.
- Fortsatt backup/export och lokal lagring.

GitHub Pages:
Ersätt de befintliga filerna med filerna i denna version. Samma Pages-adress kan användas.

V5.1:
- Nytt fullt fungerande program: Triceps 5×10.
- 5 set × 10 reps med fast arbetsvikt.
- Egen progression: klarar du 5/5 höjs vikten med programmets inställda ökning.
- Egen vilotid, viktökning och viktavrundning.
- Separat Triceps-historik, statistik och milstolpar.
- Pågående Triceps-pass kan lämnas, återupptas och avbrytas.
- Global startsida summerar både Bulgaren och Triceps 5×10.
- Backup/export omfattar nu hela v5-datamodellen.


V6 – Supabase backup
- Lokal lagring är kvar.
- Automatisk anonym inloggning.
- Bulgaren och Triceps-historik säkerhetskopieras till Supabase.
- Programstatus och inställningar säkerhetskopieras.
- Synkstatus och manuell Synka nu-knapp.
- Automatisk synk när internet återkommer.
- Google-koppling och återställning till ny enhet kommer i nästa steg.


V6 Bulgaren-only
- Endast Bulgaren visas och används.
- Triceps synkas inte längre.
- Eventuell gammal Triceps-data raderas inte automatiskt, för säkerhets skull.

V6.1 Bulgaren
- Sparar och låser molnidentiteten lokalt.
- Om Supabase-sessionen försvinner skapas INTE automatiskt en ny anonym användare.
  Detta förhindrar att samma historik laddas upp under flera user_id.
- Om molnidentiteten oväntat ändras stoppas synkningen.
- Ny knapp "Kontrollera backup" läser tillbaka aktuell användares Bulgaren-pass
  utan att skriva över lokal data.
- Gamla dubbletter i Supabase raderas inte automatiskt.

RECOVERY BUILD
- Restores persistent localStorage key trainingAppDataV5.
- Restores internal persisted schema version 5.
- Visible app version remains v6.1.
- Does not delete or reset local data.
- Do NOT clear browser/site data before testing this build.

V6.2 Bulgaren
- Internal localStorage key remains trainingAppDataV5 for backward compatibility.
- Existing workout UUID is used as Supabase client_id when present.
- Added safe "Återställ från molnet": merges by workout UUID and never deletes local history.
- Current max is conservatively recalculated from newest successful restored workout.
- Old cross-user duplicates in Supabase are left untouched for now.

V6.3 Bulgaren
- Adds Google identity linking using Supabase auth.linkIdentity().
- Redirect URL: https://ollelund.github.io/bulgaren/
- Verifies that the user ID after OAuth is the same user ID that initiated linking.
- Keeps internal localStorage schema/key at V5 for compatibility.
- Does not delete or migrate workout history during Google linking.

V6.4 Bulgaren
- Adds "Logga in med Google / återställ data" for a fresh browser/device.
- Uses Supabase signInWithOAuth for Google login.
- After successful login, downloads the signed-in user's Bulgaren sessions and merges them locally by UUID.
- Never deletes local workout history during restore.
- Recalculates current max from the newest successful restored workout.
- Keeps trainingAppDataV5 localStorage compatibility.

V6.4.1
- UX patch only for successful Google/cloud restore.
- Persists a one-time restore-success message across the automatic reload.
- Shows restored workout count and current max after reload.
- Does not change training data schema, Supabase tables, UUID merge logic, or trainingAppDataV5 storage key.

V6.5
- Account panel shows linked Google email when available.
- Clear Molnbackup Aktiv status and last backup timestamp.
- Local-device-only sign-out using Supabase signOut({scope:'local'}).
- Local workout data is retained on sign-out.
- Existing Google link, cloud restore, UUID merge and trainingAppDataV5 schema remain unchanged.

V6.6
- First-run welcome/auth screen.
- "Fortsätt med Google" uses normal OAuth sign-in: new Google identity creates a permanent user; existing Google identity signs into the existing user.
- Existing permanent Google sessions skip welcome and automatically merge Bulgaren cloud history locally.
- "Fortsätt utan konto" explicitly creates an anonymous Supabase user.
- Anonymous users can later use "Länka till Google" in Settings.
- Google/permanent users do not see the link button; they see local-device logout.
- Signing out returns to welcome without deleting local workout data.
- trainingAppDataV5, workout UUID merge, tables and workout model are unchanged.

V6.6.1
- Fix: initCloud no longer auto-creates an anonymous user when there is no session.
- First-run welcome screen now controls account creation.
- "Fortsätt utan konto" is the only first-run path that calls signInAnonymously().
- Existing valid sessions still bypass the welcome screen.
- trainingAppDataV5 and workout/cloud data model unchanged.

V6.7
- Workout-first Bulgaren home: current max, next goal, start button, progress summary and latest session.
- 8-segment workout progress indicator (green passed, red failed, blue current/next).
- Rest screen prioritizes NEXT SET weight/reps and plate loading plan so the bar can be changed during rest.
- Dedicated workout result screen with 8-set result indicator, new/retained max, volume, date and set details.
- Existing account/auth, cloud model, UUID logic and trainingAppDataV5 storage key are unchanged.

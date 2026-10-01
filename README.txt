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

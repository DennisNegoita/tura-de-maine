# Tura de mâine · paletizare UR20

Aplicație web pentru telefon (PWA) în care clientul își numără gălețile un minut, află dacă o celulă de paletizare UR20 i se potrivește, își vede „tura de mâine” într-o animație construită pe cifrele lui și primește un raport pe care îl poate trimite mai departe.

Prototip pentru AI-Powered Business Challenge 2026 (studiul de caz Tech-Con, paletizare cu UR20). Toate datele sunt fictive.

**Link public:** https://dennisnegoita.github.io/tura-de-maine/
**Mod prezentare:** https://dennisnegoita.github.io/tura-de-maine/#prezentare
**Panou Tech-Con:** https://dennisnegoita.github.io/tura-de-maine/#panou
**Bandă de test pentru cameră** (deschide pe laptop, filmează cu telefonul): https://dennisnegoita.github.io/tura-de-maine/#banda

## Pași scurți pentru testare (2 minute)

1. Deschide linkul pe telefon.
2. **Caz normal, rapid:** apasă „Vezi un exemplu” → „Vezi tura ta de mâine” (animația durează ~30 s) → „Vezi raportul complet” → „Cere evaluare Tech-Con”.
3. **Caz normal, cu măsurare:** „Numără gălețile acum” → START → atinge cercul la fiecare găleată (sau „Știu deja cifra” și scrie, de exemplu, 7) → 3 întrebări → „Vezi rezultatul”.
4. **Caz cu date greșite:**
   - La măsurare, apasă START și oprește-te după o singură atingere. Apare mesajul că măsurătoarea e prea scurtă.
   - La „Știu deja cifra”, scrie 120. Apare mesajul că valoarea nu e realistă.
   - La detalii, alege „Altă greutate” fără să scrii nimic sau, la „Mai multe detalii”, scrie 20 de ore pe tură. Câmpurile se marchează cu roșu.
   - Scrie 25 kg. Verdictul devine „Nepotrivit pentru UR20”.
5. **Link de raport:** în raport, „Copiază linkul”, apoi deschide-l într-o altă fereastră. Aplicația se deschide direct cu aceleași date.
6. **Numărare cu camera:** la măsurare, alege „📷 Cu camera” → „Pornește camera”. Trece cu mâna sau cu un obiect prin fața camerei, peste linia roșie. Contorul crește la fiecare trecere. Dacă refuzi accesul la cameră, aplicația explică ce să faci și propune atingerea.
7. **Panoul Tech-Con:** după ce trimiți o cerere, „Vezi cum o primește Tech-Con”, sau din subsol „Panou Tech-Con (demo)”, sau direct `…/#panou`. Cererile sunt ordonate după scor (A, B, C), iar calculatorul „De la buget la țintă” arată câte cereri relevante sunt necesare pentru 17 celule.
8. **Mod prezentare:** din subsol „▶ Mod prezentare” sau direct `…/#prezentare`. Aplicația trece singură prin tot fluxul în ~1 minut. O atingere oriunde o oprește.

## Ce mai are

- **Imagine cu rezultatul:** în raport, butonul „Imagine cu rezultatul” creează o imagine în stil Tech-Con, gata de trimis pe WhatsApp.
- **Instalare:** pe telefon apare „Instalează pe telefon”. Aplicația se pune pe ecranul principal și merge și fără internet în hală.
- **Cod QR pe calculator:** pe ecran mare, prima pagină arată un cod QR care deschide aplicația pe telefon.

## Ce calculează

| Calcul | Sursa |
|---|---|
| Ritmul robotului: 8,6 găleți/min (5 kg) și 7,4 (13 kg), interpolat între ele | Testele aplicației de referință Tech-Con (fapte) |
| Găleți pe palet: 100 × 5 kg sau 44 × 13 kg | Aplicația de referință (fapte) |
| Tone ridicate pe om și pe tură | Datele introduse de utilizator |
| Indice de ridicare NIOSH (ecuația revizuită) | Ipoteze declarate în aplicație („Cum am calculat?”) |
| Câte celule sunt necesare, rezerva de ritm | Comparația linie vs. ritmul testat |
| Volum suplimentar (doar dacă paletizarea frânează linia) | Ritmul posibil declarat de utilizator |
| Ore eliberate și valoarea lor (opțional) | Costul orar introdus de utilizator; 3 min pe schimbare de palet; 250 de zile pe an |

Nu promite garanții și nu calculează recuperarea investiției. Faptele din aplicația de referință sunt separate de estimări.

## Rulare locală

```bash
python3 -m http.server 5173
```

Apoi deschide http://localhost:5173. E un singur `index.html`, fără build. Singura dependență externă e generatorul de cod QR (cdnjs), încărcat doar pe calculator. Camera merge doar pe https sau pe localhost.

## Publicare

Orice hosting static merge: GitHub Pages, Netlify sau Vercel. Se urcă tot folderul ca atare.

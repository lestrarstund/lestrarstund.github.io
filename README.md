# Lestrarstund

Gagnvirkt lestrarapp á íslensku fyrir börn. Appið er vefapp (PWA) sem virkar án nettengingar og er sett upp á spjaldtölvu eða síma með „Bæta á heimaskjá“.

## Skrár

| Skrá | Hlutverk |
|---|---|
| `index.html` | Allt appið: útlit, sögur, myndir og virkni í einni skrá |
| `sw.js` | Service worker sem geymir appið svo það virki án nets |
| `manifest.webmanifest` | Nafn, litir og tákn appsins á heimaskjá |
| `firestore.rules` | Aðgangsreglur fyrir gagnagrunninn í Firebase |
| `PERSONUVERND.md`, `SKILMALAR.md` | Drög að persónuverndarstefnu og notkunarskilmálum (sömu textar eru í appinu) |
| `icon-*.png`, `apple-touch-icon.png` | Tákn appsins |

## Keyra á eigin tölvu

Opnaðu `index.html` beint í vafra, eða keyrðu lítinn vefþjón í möppunni (þarf fyrir offline-virknina og Firebase):

```
npx serve .
```

## Útgáfa

Tengdu þetta repo við Netlify. Þá fer ný útgáfa sjálfkrafa í loftið í hvert sinn sem breyting er sett inn á `main`.

Þegar `index.html` breytist þarf að hækka útgáfunúmerið sem sést neðst á velkomnaskjánum og í stillingum (leitaðu að „útgáfa 42“ í `index.html`) og útgáfunúmerið efst í `sw.js` (t.d. `lestrarstund-v42` → `lestrarstund-v43`), annars getur tækið haldið áfram að sýna gömlu útgáfuna.

Firebase er þegar tengt í þessari útgáfu (verkefnið `lestrarstund`).

## Aðgangar foreldra (Firebase)

Appið virkar án aðgangs. Þá eru öll gögn aðeins á tækinu, eins og áður. Til að foreldrar geti stofnað aðgang og samstillt á milli tækja þarf að tengja Firebase:

1. Farðu á [console.firebase.google.com](https://console.firebase.google.com) og stofnaðu nýtt verkefni (t.d. `lestrarstund`). Slökktu á Google Analytics, appið notar það ekki.
2. **Authentication** → *Get started* → *Sign-in method*: kveiktu á **Email/Password** og **Google**.
3. **Authentication** → *Settings* → *Authorized domains*: bættu við léninu sem appið er á, t.d. `lestrarstund.github.io`, og eigin léni ef það er til.
4. **Firestore Database** → *Create database* → *Production mode*. Veldu staðsetningu í Evrópu, t.d. `europe-west1` (Belgía). Þetta er ekki hægt að breyta seinna.
5. **Firestore Database** → *Rules*: afritaðu innihald `firestore.rules` yfir það sem er þar og ýttu á *Publish*.
6. **Project settings** (tannhjólið) → *Your apps* → veldu vefapp (`</>`), gefðu því nafn og afritaðu `firebaseConfig`.
7. Opnaðu `index.html`, leitaðu að `const FB_CONFIG=null;` og settu stillingarnar inn í staðinn, t.d.:

   ```js
   const FB_CONFIG={apiKey:"…",authDomain:"lestrarstund.firebaseapp.com",projectId:"lestrarstund",appId:"…"};
   ```

   Þessar stillingar eru ekki leyndarmál. Aðgangsreglurnar í skrefi 5 eru það sem verndar gögnin.
8. Hækkaðu útgáfunúmerið í `sw.js` og settu breytinguna inn.

### Hvernig gögnin eru geymd

- `users/{uid}` vísar á fjölskyldu foreldrisins.
- `families/{fid}` geymir lista af foreldrum (`members`).
- `families/{fid}/parts/{hluti}` geymir gögnin: `shared` (krukka, jóladagatal, PIN sem hash), `ubooks`, `made` og eitt skjal fyrir hvern lesanda (`p_p7`, `p_p9`, `p_u…`). Þannig getur hvert barn lesið á sínu tæki án þess að tækin skrifi yfir gögn hvors annars.
- `invites/{kóði}` geymir boðskóða sem gilda í 7 daga.
- Upptökur barnanna eru aldrei sendar í skýið. Þær eru aðeins í IndexedDB á tækinu.

Appið hleður Firebase-forritasöfnunum (útgáfa 13.1.0) frá `www.gstatic.com` aðeins ef `FB_CONFIG` er stillt.

## Lykilorð foreldra

Foreldrar velja sitt eigið fjögurra stafa lykilorð. Það er geymt sem hash og samstillt á milli tækja. Eftir 5 rangar tilraunir læsist það tímabundið. Á eldri tækjum sem hafa ekki valið lykilorð gildir sjálfgefna lykilorðið þar til því er breytt í *Stillingar → Aðgangur*.

## Áður en appið er opnað almenningi

- Fylla út allt í [HORNKLOFUM] í `PERSONUVERND.md`, `SKILMALAR.md` og sama texta í `index.html` (leitaðu að `const LEGAL=`).
- Láta lögfræðing lesa textana yfir.
- Prófa nýskráningu, innskráningu á öðru tæki, boðskóða og eyðingu aðgangs með prufuaðgöngum.

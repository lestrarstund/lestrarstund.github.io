# Persónuverndarstefna – Lestrarstund

Síðast uppfært: [DAGSETNING]

Lestrarstund er lestrarapp fyrir börn. Við söfnum eins litlum upplýsingum og hægt er: aðeins því sem þarf til að appið virki og lestur barnanna geymist á milli tækja. Engar auglýsingar eru í appinu og við seljum aldrei upplýsingar.

### 1. Ábyrgðaraðili

[NAFN ÁBYRGÐARAÐILA], kt. [KENNITALA], [HEIMILISFANG], ber ábyrgð á vinnslu persónuupplýsinga í Lestrarstund. Fyrirspurnir um persónuvernd sendist á [NETFANG].

### 2. Hverjir nota appið

Aðeins foreldrar og forráðamenn, 18 ára og eldri, geta stofnað aðgang. Foreldri bætir börnum sínum við sem lesendum. Börn skrá sig aldrei inn, gefa aldrei upp netfang og geta ekki haft samskipti við aðra notendur.

### 3. Hvaða upplýsingar við vinnum

**Um foreldri (eiganda aðgangs)**

- Netfang og lykilorð. Lykilorðið er geymt dulkóðað (hash) hjá Firebase Authentication og við sjáum það aldrei.
- Ef innskráning er með Google: nafn, netfang og auðkenni frá Google.
- Fjögurra stafa PIN-númer foreldra, geymt sem hash (aldrei í læsilegu formi).
- Stillingar, til dæmis lestrarmarkmið og umbun.

**Um hvert barn (lesanda)**

- Fornafn eða gælunafn. Við mælum með að nota aðeins fornafn eða gælunafn.
- Aldur eða aldursbil, erfiðleikastig og valin persóna. Persónan er annaðhvort teiknuð persóna úr appinu eða eigin karakter sem barnið setur saman úr teiknuðum hlutum (til dæmis hárgreiðslu, litum og fötum). Hvorugt er mynd af barninu.
- Lestrarsaga: hvaða sögur eru lesnar, mínútur, stjörnur, svör við spurningum í lok sagna og áætlaður leshraði.
- Heimalestur sem foreldri skráir: dagsetning, mínútur og bókarheiti ef það er skráð.

**Radd- og hljóðupptökur**

Ef barnið les upphátt og tekur sig upp eru upptökurnar eingöngu vistaðar á tækinu sjálfu. Þær eru aldrei sendar til okkar eða í skýið.

**Prófílmynd á tækinu**

Foreldri getur valið mynd úr myndasafni tækisins sem prófílmynd fyrir barn, í foreldrasvæðinu sem er læst með PIN-númeri. Myndin er minnkuð og vistuð eingöngu á tækinu sjálfu. Hún er aldrei send til okkar eða í skýið, samstillist ekki á milli tækja og er ekki hluti af öryggisafriti. Á öðrum tækjum birtist valin persóna í staðinn. Foreldri getur fjarlægt myndina hvenær sem er í foreldrasvæðinu.

**Tæknilegar upplýsingar**

- IP-tala og upplýsingar um tæki og vafra, sem Firebase og Netlify skrá við innskráningu og þegar appið er sótt. Þetta er gert í öryggisskyni og til að koma í veg fyrir misnotkun.
- Appið vistar gögn í staðbundinni geymslu tækisins (localStorage) svo það virki án nettengingar. Við notum ekki vafrakökur til rakningar og engar vefgreiningar.

### 4. Tilgangur og heimild

| Tilgangur | Upplýsingar | Heimild |
| --- | --- | --- |
| Stofna og reka aðgang foreldris | Netfang, lykilorð, PIN | Samningur við foreldri (b-liður 1. mgr. 6. gr. GDPR) |
| Halda utan um lestur barna og samstilla á milli tækja | Upplýsingar um börn og lestrarsaga | Samþykki foreldris (a-liður 1. mgr. 6. gr. GDPR) |
| Öryggi, varnir gegn misnotkun og bilanaleit | Tæknilegar upplýsingar | Lögmætir hagsmunir (f-liður 1. mgr. 6. gr. GDPR) |
| Svara fyrirspurnum og senda nauðsynlegar tilkynningar um aðganginn | Netfang | Samningur við foreldri |

Við notum upplýsingarnar ekki í markaðsskyni, til persónusniðinna auglýsinga eða til að byggja upp persónusnið af börnum. Leshraði og stjörnur eru aðeins sýnd foreldrinu og barninu sjálfu.

### 5. Börn og samþykki foreldra

Lestrarstund er ætluð börnum en þjónustan er boðin foreldrum. Foreldri veitir samþykki fyrir vinnslu upplýsinga um barnið þegar það bætir barninu við sem lesanda. Þetta er í samræmi við 8. gr. GDPR og 10. gr. laga nr. 90/2018 um persónuvernd og vinnslu persónuupplýsinga. Samkvæmt þeim þarf samþykki foreldris fyrir börn yngri en 13 ára. Foreldri getur afturkallað samþykkið hvenær sem er með því að eyða lesanda eða öllum aðganginum.

### 6. Vinnsluaðilar og hýsing

Við notum eftirfarandi þjónustuaðila sem vinna upplýsingar fyrir okkar hönd samkvæmt vinnslusamningi:

| Vinnsluaðili | Hlutverk | Staðsetning gagna |
| --- | --- | --- |
| Google (Firebase Authentication) | Innskráning foreldra | Bandaríkin |
| Google (Cloud Firestore) | Geymsla lestrargagna og stillinga | [GAGNASVÆÐI, t.d. europe-west1 í Belgíu] |
| Netlify | Hýsing á sjálfu appinu (forritsskrár) | Dreift net netþjóna, þar á meðal í Bandaríkjunum |

### 7. Flutningur út fyrir EES

Firebase Authentication er eingöngu rekið í gagnaverum í Bandaríkjunum. Google LLC er vottað samkvæmt gagnaverndarramma ESB og Bandaríkjanna (EU-U.S. Data Privacy Framework) og flutningur byggir auk þess á stöðluðum samningsákvæðum framkvæmdastjórnar ESB. Lestrargögnin sjálf eru geymd í Firestore innan Evrópu.

### 8. Hve lengi við geymum upplýsingar

- Á meðan aðgangurinn er virkur.
- Þegar foreldri eyðir lesanda eða aðgangi er gögnunum eytt strax úr gagnagrunninum. Afrit hjá Google eyðast innan [30] daga.
- Ef aðgangur hefur ekki verið notaður í [24] mánuði sendum við tölvupóst og eyðum honum [30] dögum síðar ef ekkert svar berst.
- Gögn sem aðeins eru á tækinu (til dæmis upptökur og prófílmyndir) eyðast þegar appinu eða gögnum vafrans er eytt. Prófílmynd eyðist líka þegar lesanda er eytt.

### 9. Réttindi þín

Þú átt rétt á að:

- fá aðgang að upplýsingunum og fá afrit af þeim. Í appinu er hnappurinn „Sækja öryggisafrit“ sem sækir öll gögn í einni skrá.
- fá rangar upplýsingar leiðréttar. Flestu getur þú breytt sjálf(ur) í stillingum.
- fá upplýsingum eytt („Eyða aðgangi“ í stillingum).
- flytja gögnin annað (sama öryggisafrit).
- andmæla vinnslu og afturkalla samþykki hvenær sem er.

Sendu beiðni á [NETFANG] og við svörum innan mánaðar. Ef þú telur að vinnslan brjóti gegn lögum getur þú kvartað til Persónuverndar ([www.personuvernd.is](https://www.personuvernd.is)).

### 10. Öryggi

- Öll samskipti við netþjóna eru dulkóðuð (HTTPS/TLS).
- Aðgangsreglur í gagnagrunninum tryggja að hvert foreldri sjái aðeins eigin gögn.
- PIN-númer foreldra er geymt sem hash. Eftir fimm rangar tilraunir læsist það tímabundið.
- PIN-númerið er þægindalás á tækinu. Ekki nota sama númer og á greiðslukorti eða síma.

Ef upp kemur öryggisbrestur sem varðar þínar upplýsingar látum við þig og Persónuvernd vita eins og lög gera ráð fyrir.

### 11. Breytingar

Ef við breytum stefnunni með þeim hætti að það skipti máli látum við vita í appinu eða með tölvupósti áður en breytingin tekur gildi.

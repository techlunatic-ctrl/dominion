# Kanuni ya Majina — Uandishi wa Swa wa Dominion

Swa haina eneo la majina (namespace) wala neno muhimu la faragha ya
faili (`static`). Kila jina la kazi la ngazi ya juu ni la ulimwengu
mzima wa programu — kazi mbili zenye jina moja kwenye moduli tofauti
ni mgongano, hata kama hazihusiani. Kwa hiyo kila moduli ya Dominion
ina kiambishi chake cha lazima, tangu kazi ya kwanza.

## Ramani ya viambishi (moduli za C → kiambishi cha Swa)

| Moduli ya C (`src/core/`) | Kiambishi cha Swa |
|---|---|
| `politics/`     | `siasa_`        |
| `technology/`   | `teknolojia_`   |
| `diplomacy/`    | `diplomasia_`   |
| `economy/`      | `uchumi_`       |
| `governance/`   | `utawala_`      |
| `culture/`      | `utamaduni_`    |
| `military/`     | `jeshi_`        |
| `population/`   | `idadi_ya_watu_`|
| `ai/`           | `akili_bandia_` |
| `events/`       | `matukio_`      |
| `environment/`  | `mazingira_`    |
| `world/`        | `dunia_`        |
| `simulation_engine/` | `injini_`  |

## Kiambishi maalum kwa faili za `src/core/` (ngazi ya juu, si saraka ndogo)

Baadhi ya faili za `src/core/` ziko ngazi ya juu (si ndani ya saraka
ndogo ya moduli) na zinahitaji viambishi vyao maalum, tofauti na
ramani ya juu (ambayo ni kwa saraka ndogo pekee):

| Faili ya C (`src/core/*.c`) | Kiambishi cha Swa | Muhimu |
|---|---|---|
| `role.c` | `jukumu_` | |
| `character.c` | `mhusika_` | |
| `knowledge_system.c` | `maarifa_` | |
| `constitution.c` | `taifa_katiba_` | TOFAUTI na `utawala_katiba_` (governance/legal/constitution.c) -- majina mawili ya faili ya C yanayofanana lakini mifumo tofauti kabisa (ruhusa za vitendo vya mchezaji dhidi ya matawi/taasisi za serikali) |
| `faction.c` | `taifa_kianzio_` | TOFAUTI na `siasa_kikundi_` (politics/faction_system.c, imezuiwa na #182(b)) -- hii ni aina za awali za taifa (archetypes), si miungano ya kisiasa |
| `npc_engine.c` | `wakala_` | |
| `time_engine.c` | `injini_saa_` | Sehemu YA SAA KUU pekee imetafsiriwa (mwaka/siku/zamu) -- mfumo wa kalenda nyingi/enzi umeachwa, angalia maelezo kwenye `swa/moduli/injini/saa_kuu.swa` |
| `profile.c` | `wasifu_` | Ilitumia SDL3 moja kwa moja kwa faili (SDL_CreateDirectory/SDL_IOFromFile/SDL_EnumerateDirectory) -- imeandikwa upya kwa syscalls ghafi (mkdir=83, getdents64=217) badala ya kutumia SDL3 au faili.swa pekee (ambayo haina uundaji/uorodheshaji wa saraka) -- angalia `swa/moduli/wasifu/wasifu.swa` |

## Viambishi vidogo vya `governance/` (saraka ndogo nyingi, kila moja `utawala_<kiambishi_kidogo>_`)

`governance/` ina saraka ndogo nyingi zenye faili nyingi za kibinafsi
— kila faili ina kiambishi kidogo chake chini ya `utawala_` (si
`utawala_` peke yake, ambayo ingegongana kila mahali):

| Faili ya C | Faili ya Swa | Kiambishi kidogo |
|---|---|---|
| `branches/council.c` | `branches/baraza.swa` | `utawala_baraza_` |
| `branches/executive.c` | `branches/mtendaji.swa` | `utawala_mtendaji_` |
| `branches/judiciary.c` | `branches/mahakama.swa` | `utawala_mahakama_` |
| `branches/religious_body.c` | `branches/kidini.swa` | `utawala_kidini_` |
| `branches/legislative.c` | `branches/bunge.swa` | `utawala_bunge_` |
| `institutions/civil_service.c` | `institutions/utumishi.swa` | `utawala_utumishi_` |
| `institutions/ministry.c` | `institutions/wizara.swa` | `utawala_wizara_` |
| `institutions/institution.c` | `institutions/taasisi.swa` | `utawala_taasisi_` |
| `legal/constitution.c` | `legal/katiba.swa` | `utawala_katiba_` |
| `legal/legal_status.c` | `legal/hadhi_kisheria.swa` | `utawala_hadhi_kisheria_` |
| `legal/rights.c` | `legal/haki.swa` | `utawala_haki_` |
| `political/corruption.c` | `political/rushwa.swa` | `utawala_rushwa_` |
| `political/political_violence.c` | `political/vurugu.swa` | `utawala_vurugu_` |
| `territorial/subdivision.c` | `territorial/mgawanyo.swa` | `utawala_mgawanyo_` |
| `custom_governance.c` | `desturi.swa` | `utawala_desturi_` |
| `evolution/governance_evolution.c` | `maendeleo.swa` | `utawala_` (kazi za jumla) |
| `political/elections.c` | `political/uchaguzi.swa` | `utawala_uchaguzi_` |
| `interaction/notebook.c` | `interaction/daftari.swa` | `utawala_daftari_` |
| `interaction/interaction.c` | `interaction/mwingiliano.swa` | `utawala_mwingiliano_` |
| `interaction/conversation.c` | `interaction/mazungumzo.swa` | `utawala_mazungumzo_` |
| `metrics/societal_metrics.c` | `metrics/vipimo.swa` | `utawala_vipimo_` |

Bado hazijaandikwa: `government.c` (hub kuu — sasa mifumo YOTE 6
inayohitajika ipo, ubaki kazi ya kuunganisha, si kazi mpya).

Msingi wa pamoja (`include/common.h`) hauna kiambishi cha moduli —
unatumia `civ_` (kutoka jina la asili la mradi, "Civilization
simulation") kwa sababu kila faili litahusisha hili, na hakuna hatari
ya mgongano na moduli mahususi.

## Kanuni

1. Kila jina la kazi/muundo/kigezo cha ulimwengu LAZIMA lianze na
   kiambishi cha moduli lake. Hakuna ubaguzi, hata kwa kazi ndogo za
   ndani zinazoonekana salama.
2. Kiambishi kinafuatwa na `_` kisha jina la kazi kwa Kiswahili,
   kwa mtindo wa `chini_chini` (snake_case), sawa na maktaba za Swa
   zilizopo (`orodha_ongeza`, `ramani_weka`).
3. Migogoro ya majina kati ya moduli mbili (mfano: `siasa_` na
   `utawala_` zote zikihitaji kazi ya "chagua_kiongozi") ni ishara
   kuwa kazi hiyo inapaswa kuhamishwa kwenye msingi wa pamoja
   (`swa/msingi/`), si kuachwa kwenye moduli zote mbili kwa majina
   tofauti kidogo.

## Onyesho/kifaa (rendering/windowing) -- eneo JIPYA, si tafsiri ya `src/core/`

Safu ya uchoraji/onyesho na ingizo (kibodi/kipanya) SI tafsiri ya
faili yoyote ya C iliyopo (SDL3 ilitumika hapo, imeondolewa kabisa --
angalia sheria ya mradi: hakuna utegemezi wa lugha/maktaba nyingine
yoyote). Ni safu mpya kabisa inayozungumza moja kwa moja na kernel ya
Linux kupitia DRM/KMS (`/dev/dri/cardN`) na evdev (`/dev/input/eventN`)
kwa ioctl/syscalls ghafi -- HAKUNA X11, HAKUNA Wayland, HAKUNA
compositor ya mtu wa kati.

| Saraka | Kiambishi | Wajibu |
|---|---|---|
| `swa/moduli/onyesho/` | `onyesho_` | DRM/KMS: kufungua kifaa, kupata rasilimali/connector/modi, kuunda na kuramanisha dumb buffer, ADDFB/SETCRTC |
| `swa/moduli/onyesho/` (mchoro.swa) | `mchoro_` | Vitendo vya uchoraji 2D juu ya framebuffer YOYOTE (fill-rect, mstari, blit) -- havitegemei DRM moja kwa moja, vinafanya kazi juu ya bafa yoyote ya XRGB8888 |
| `swa/moduli/onyesho/` (baiti_ghafi.swa) | `weka_`/`pata_`/`anwani` | Kusoma/kuandika u16/u32/u64 (little-endian) kwenye bafa ya N8* kwa offset halisi -- msingi wa kuwakilisha miundo ya ioctl ya kernel bila kutegemea mpangilio wa `muundo` ya Swa (angalia maoni ya faili kwa sababu kamili) |
| `swa/moduli/kifaa/` | `kifaa_` | Kusoma matukio ghafi ya kibodi/kipanya kutoka `/dev/input/eventN` (`struct input_event`) |

Hali ya sasa (2026-09-11): mfululizo mzima wa DRM/KMS umejaribiwa
dhidi ya kifaa HALISI (`/dev/dri/card1`, amdgpu) -- kufungua,
GETRESOURCES, GETCONNECTOR (connector ya ndani ya eDP imegunduliwa,
kimeungwa=1, modi bora 2560x1440), GETENCODER->CRTC, na CREATE_DUMB
(pitch/ukubwa sahihi kabisa) VYOTE vinafanya kazi na thamani HALISI
zilizothibitishwa. Hatua ya mmap ya dumb buffer (na kwa hiyo SETCRTC)
inakataliwa na EACCES kwa sababu compositor ya Wayland inayoendesha
kikao hiki tayari ni "DRM master" wa onyesho -- hii ni TABIA SAHIHI
ya kernel (kifaa kimoja, bwana mmoja kwa wakati mmoja), SI kasoro ya
msimbo. Vitendo vya uchoraji (`mchoro.swa`) vimethibitishwa kikamilifu
dhidi ya bafa ya synthetic. Kusoma ingizo (`kifaa/ingizo.swa`)
kumethibitishwa dhidi ya kifaa halisi cha kibodi (`/dev/input/event3`)
-- kufungua, kusoma bila kuzuia, na EAGAIN vimefanya kazi; tukio
halisi la kubonyeza kitufe halikujaribiwa moja kwa moja (hakuna
mtu wa kubonyeza wakati wa jaribio la kiotomatiki).

## Nidhamu ya "callee kabla ya caller" -- SI LAZIMA TENA

`gharama/kagua-mpangilio.py` (kigunduzi cha wito wa mbele hatarishi,
kilichoandikwa mwanzoni mwa mradi huu kama ulinzi dhidi ya
lugha-swa/swa#180) kimeondolewa. #180 imerekebishwa upstream (2026-09-11,
PR #212 -- usajili wa pitio la pili la saini za kazi zote KABLA ya
kukagua miili yoyote). Msimbo uliopo tayari unaofuata nidhamu ya
"panga kazi kwa mpangilio wa callee kabla ya caller" HAUHITAJI kupangwa
upya -- ni sahihi kama ulivyo -- lakini msimbo MPYA hauhitaji tena
kufuata nidhamu hiyo kwa mkono: mkusanyaji sasa unakataa kwa sauti
wito wa mbele wenye idadi mbaya ya hoja, wakati wowote wa kukusanya.

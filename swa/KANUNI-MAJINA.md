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
| `subunits/`     | (faili moja, kiambishi chake maalum -- angalia chini) |
| `abstracts/`    | (faili moja, kiambishi chake maalum -- angalia chini) |
| `data/`         | (faili moja, kiambishi chake maalum -- angalia chini) |

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
| `subunits/subunit.c` | `kitengo_chini_` | Saraka `subunits/` ina faili MOJA tu -- haikuhitaji jedwali lake la kiambishi-kidogo (tofauti na `governance/`). Vitengo vidogo vya kiutawala (mkoa/kanda/jiji/wilaya), kugawanyika/kuungana -- angalia `swa/moduli/subunits/kitengo_chini.swa` |
| `abstracts/soft_metrics.c` | `vipimo_laini_` | Vipimo "laini" vya taifa (furaha, uhalali, fahari) -- angalia `swa/moduli/abstracts/vipimo_laini.swa` |
| `data/history_db.c` | `historia_db_` | Journal ya matukio ya kihistoria (event-sourced), ikiwemo uhifadhi/upakiaji wa faili halisi -- angalia `swa/moduli/data/historia_db.swa` kwa maelezo kamili ya tofauti za umbizo la faili kutoka kwa C |

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

## Uthibitisho dhidi ya Awamu D (lugha-swa/swa#279) -- 2026-09-27

lugha-swa/swa#279 ("Awamu D") iliondoa kabisa uungwaji mkono wa
herufi kubwa za aina za msingi (N32/N64/D64/B1/W0 n.k. hazitambuliwi
tena KABISA) kwenye stage1, ikimaliza mradi wa uhamiaji wa herufi
ndogo ulioanza na lugha-swa/swa#225. Kabla ya #279 kuungana
(2026-09-26), tayari commit 271ce40 (2026-09-12, PR #1 ya hazina hii)
ilikuwa imehamisha faili zote 111 za .swa za mradi huu kwenda herufi
ndogo -- kwa hiyo hazina hii ilikuwa TAYARI salama dhidi ya #279 kabla
haijaungana.

Uthibitisho uliofanywa baada ya #279 kuungana (dhidi ya stage1 mpya
kabisa iliyojengwa kutoka lugha-swa/swa main ya 2026-09-26, mnyororo
kamili mbegu->msuluhishi->stage1, si binary ya zamani):

- Grep ya `swa/` yote: HAKUNA `\bN8\b`..`\bW64\b` (herufi kubwa)
  kwenye msimbo halisi -- tukio pekee lililopatikana ni maandishi ya
  KANUNI-MAJINA.md yenyewe (mfano wa maelezo, si msimbo).
- Ukaguzi wa migongano ya jina la kigezo dhidi ya aina mpya za herufi
  ndogo (familia zote 19: n8/n16/n32/n64, a8/a16/a32/a64, d32/d64,
  b1/b8/b16/b32/b64, w0/w8/w16/w32/w64): vigezo viwili tu
  vilivyopatikana vikigongana kwa jina --
  `swa/msingi/maktaba/bin_soma.swa` na
  `swa/moduli/onyesho/jaribio_mchoro.swa`, vyote viwili vina kigezo
  cha ndani kiitwacho `b1`. Vimethibitishwa TARAJIWA (havihitaji
  kubadilishwa jina): hazitumiki ndani ya muktadha wa aina (`ukubwa(x)`
  / `tenga(x...)` / tamko la aina), na kuendesha kwa mkono kunathibitisha
  thamani sahihi (bin_soma: v16=513, v32=67305985; jaribio_mchoro.swa:
  PASS) dhidi ya stage1 mpya.
- `swa/moduli/mchezo.swa` na `swa/moduli/dunia/taifa.swa`
  (sehemu mbili nzito zilizotajwa) zinakusanya bila hitilafu yoyote
  dhidi ya stage1 mpya.
- Programu ya majaribio iliyoendesha `mchezo_unda()`, mizunguko 5 ya
  `idadi_ya_watu_sasisha`, mizunguko 5 ya `uchumi_mkuu_sasisha`, na
  `dunia_taifa_mfumo_dai_maeneo_yote` (ikiwemo kudai kipande kimoja
  cha ardhi HALISI kwenye ramani) ilitoa matokeo YANAYOFANANA KABISA
  (diff tupu, herufi kwa herufi) kati ya stage1 iliyojengwa KABLA ya
  #279 (commit d3bb984, inayounga mkono herufi zote mbili) na stage1
  iliyojengwa BAADA ya #279 (herufi ndogo pekee).

### Mdudu ULIOKUWEPO TAYARI uliogunduliwa (nje ya wigo wa uhamiaji huu)

`utawala_serikali_unda()` (`swa/moduli/utawala/serikali.swa`)
inaporomoka (SIGSEGV) pale `tenga(ukubwa(UtawalaSerikali))`
inaporudisha kielekezi cha 0 (NULL) -- ijapokuwa `mmap()` yenyewe
inafaulu (imethibitishwa kwa `strace`). Hii HAITOKEI ikiwa
`serikali.swa` inakusanywa peke yake (kitengo kidogo cha ukusanyaji);
INATOKEA TU wakati imekusanywa kama sehemu ya graph NZIMA ya
`mchezo.swa` (miundo 215+ ya `husisha` inayofuatana). Imethibitishwa
kutokea SAWA KABISA (mahali pamoja, tabia moja) dhidi ya stage1 ya
KABLA na BAADA ya #279 -- kwa hiyo SI athari ya uhamiaji wa herufi
ndogo wala ya #279 yenyewe, ni mdudu wa kina zaidi (labda kikomo
kingine cha jedwali la ndani la mkusanyaji, kinachofanana na
#189/#192/#197 zilizotangulia, lakini kwa kiwango kikubwa zaidi cha
miundo) unaostahili uchunguzi tofauti, WA NJE ya kazi hii. Kwa sasa
`mchezo_anzisha()` kamili (inayoita `utawala_serikali_unda`) haiwezi
kuendeshwa kikamilifu ikiwa imekusanywa pamoja na graph nzima ya
mchezo.swa -- programu za majaribio zilizotumika hapo juu ziliepuka
njia hii kwa makusudi kwa kuunda mifumo moja moja moja kwa moja.

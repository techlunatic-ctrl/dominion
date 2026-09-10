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

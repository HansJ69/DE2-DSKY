# DE2-DSKY

**8. Apollo DSKY console maquette**: maketa ovládacího rozhraní DSKY z kosmické lodi Apollo.

## O DSKY

**DSKY** (Display and Keyboard) bylo uživatelské rozhraní palubního počítače **Apollo Guidance Computer (AGC)**, vyvinutého v MIT Instrumentation Laboratory. Prostřednictvím DSKY komunikovali astronauti s počítačem během letů na Měsíc.

### Co DSKY umožňovalo

- zadávat příkazy a data do počítače,
- kontrolovat stav lodi,
- počítat korekce dráhy,
- řídit motory,
- provádět astronomickou navigaci.

### Systém VERB a NOUN

Místo textového nebo grafického rozhraní se používal jednoduchý dvojslovný systém:

- **VERB** (sloveso) určuje, *jakou akci* provést,
- **NOUN** (podstatné jméno) určuje, *čeho se akce týká*.

Příklad: `VERB 16 NOUN 36` znamená "průběžně zobrazuj čas počítače".

### Displej a kontrolky

Údaje se zobrazovaly na elektroluminiscenčním displeji, který ukazoval číselné hodnoty ve třech řádcích (registry R1, R2, R3) a kódy programu, VERB a NOUN. Součástí panelu byla také sada stavových kontrolek, například:

- `COMP ACTY` (počítač právě pracuje),
- `PROG` (chyba programu),
- `OPR ERR` (chyba obsluhy),
- `GIMBAL LOCK` (blokace kardanového závěsu).

## O projektu

Cílem projektu je co nejvěrněji napodobit rozhraní **DSKY** z Apolla. Maketa je postavená na **Raspberry Pi Pico** a **vlastní desce plošných spojů (PCB)**.

### Funkce

- Zadávání příkazů systémem **VERB / NOUN** stejně jako v Apolu.
- Několik původních kombinací VERB a NOUN, například zobrazení času.
- Čtení dat z **GPS** a **IMU** přes vlastní VERB/NOUN kódy.
- Vlastní příkazy nad rámec originálu.

### Autentičnost

- **Klávesnice:** mechanické spínače pro odpovídající hmat a zvuk tlačítek.
- **Displej:** místo hotových displejů jsou segmenty tvořeny jednotlivými LED diodami, nad kterými je tvarovaný difuzér. Ten světlo rozptýlí a vytvoří tvar sedmisegmentové číslice. Barva a vzhled se tak co nejvíc blíží původnímu elektroluminiscenčnímu displeji.
- **Kontrolky:** stavové indikátory (původně žárovičky v oknech kontrolek) jsou na panelu ve stejném uspořádání jako na originále.

### Multiplexování

Aby se ušetřily piny Pica, je většina periferií řízena **multiplexně**:

- **Klávesnice** je zapojena jako maticová (řádky a sloupce).
- **LED segmenty displeje** jsou ovládány multiplexem, kdy se jednotlivé číslice rychle střídají.
- **Kontrolky** jsou ve vlastní multiplexní matici.

## Schéma



## Hardware

- Raspberry Pi Pico
- [doplnit: LED diody segmentů a jejich barva]
- [doplnit: obvody pro multiplex / budiče]
- [doplnit: mechanické spínače]
- [doplnit: GPS a IMU modul]
- [doplnit: žárovičky nebo LED pro kontrolky]

## Software

- Jazyk / platforma: [doplnit]
- Knihovny: [doplnit]
- [doplnit: jak se nahrává firmware]

## Fotky / ukázka

-

## Zdroje a inspirace

- https://github.com/rrainey/DSKY-digital-indicator-replica/tree/master
- https://github.com/Apollo-Replica/DSKY/tree/main
- https://github.com/ManoDaSilva/AGC_DSKY_Replica

## Tým

|Jméno|GitHub|Role|
|-------|--------|------|
| Adam Šimůnek | [@adamsim10](https://github.com/adamsim10) | - |
| Jan Pikner | [@HansJ69](https://github.com/HansJ69) | - |
| Jan Mareš | [@Error-30](https://github.com/Error-30) | - |

## Struktura repozitáře

```
DE2-DSKY/
├── docs/                # dokumentace, schémata, datasheety
│   ├── datasheets/      # PDF součástek
│   └── verb-noun.md     # tabulka implementovaných VERB/NOUN
├── pictures/            
├── pcb/                 # projekt desky (KiCad)
│   └── gerbers/         # soubory pro výrobu
├── models/              # 3D modely
├── src/                 # firmware pro Pico
├── LICENSE
└── README.md
```

## Stav projektu

- [ ] Návrh schématu (PCB)
- [ ] Výběr součástek
- [ ] Návrh PCB
- [ ] BOM
- [ ] Schema zapojení (přibližné)
- [ ] Blokové schéma
- [ ] Dokumentace a fotky

## Licence

Projekt je šířen pod licencí GPL-3.0, viz soubor [LICENSE](LICENSE).

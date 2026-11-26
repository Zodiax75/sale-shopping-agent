# Požadavky na funkčnost

> Živý dokument, spravuje ho Architekt. Stav: **sběr požadavků** (první návrh, čeká na Martinovy odpovědi).
> Označení: **[?]** = otevřená otázka, **[N]** = návrh architekta, **[P]** = potvrzeno Martinem.

## 1. Cíl

[P] Agent hlídá slevové akce a upozorňuje na výhodné nákupy věcí, které Martin potřebuje.

## 2. Co hlídat

- [?] Jaké kategorie zboží? (potraviny a drogerie z letáků, elektronika, sport, oblečení…)
- [?] Konkrétní položky („Nutella 750 g“) nebo obecné („káva zrnková“)?
- [N] Ke každé položce: název, případně cílová / maximální cena, jednotka (Kč/kg), priorita.
- [?] Opakované nákupy (spotřební zboží) vs. jednorázové (např. nové sluchátka)?

## 3. Odkud brát slevy

- [?] Které obchody / weby? (letákové portály, e-shopy, srovnávače cen…)
- [N] Preferovat oficiální API nebo veřejné feedy; scraping jen tam, kde to podmínky webu dovolí.

## 4. Co je „výhodný nákup“

- [N] Cena pod Martinem zadaným limitem.
- [N] Cena výrazně pod obvyklou cenou (podle historie cen v databázi).
- [?] Jiná kritéria? (jen určité obchody, minimální sleva v %…)

## 5. Upozornění

- [?] Jakým kanálem? (e-mail, Telegram, Discord, notifikace v telefonu, denní souhrn…)
- [?] Jak často? (hned při nálezu, denní/týdenní souhrn)

## 6. Provoz

- [?] Kde poběží (vlastní počítač, NAS, server, cloud)?
- [?] Jak často kontrolovat zdroje?
- [?] Jak se bude seznam přání zadávat (soubor, příkazová řádka, chat, webové rozhraní)?

## 7. Role AI (Ollama)

- [N] Párování nabídek s položkami (různé názvy téhož zboží), vytažení ceny a gramáže z textu, krátké shrnutí nabídek.
- [?] Má agent umět i něco „chytřejšího“, např. navrhovat, co se vyplatí nakoupit do zásoby?

## 8. Mimo rozsah (zatím)

- Automatický nákup / objednávání.

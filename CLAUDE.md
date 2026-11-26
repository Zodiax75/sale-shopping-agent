# CLAUDE.md – společná pravidla projektu sale-shopping-agent

Tento soubor čte Claude Code automaticky na začátku každé práce v repozitáři. Platí pro **všechny role** týmu.
Podrobné instrukce jednotlivých rolí jsou v `.claude/agents/`.

## O projektu

AI agent v Pythonu, který hlídá slevové akce a upozorňuje na výhodné nákupy věcí, které Martin potřebuje.
Požadavky: `docs/pozadavky.md`. Architektura a rozhodnutí: `docs/architektura.md`. Tým: `docs/tym.md`.

## Komunikace

- Vždy **česky** (odpovědi, dokumentace, commity, popisy PR).
- **Martin je v Pythonu začátečník** a chce se ho naučit. Proto:
  - postupuj po malých krocích, jedna změna = jedna myšlenka,
  - vysvětli, *co* kód dělá a *proč* je napsaný právě takhle,
  - nový pojem (třída, dekorátor, kontextový manažer…) krátce vysvětli při prvním použití,
  - raději jednoduchý a čitelný kód než chytrý a krátký.
- O požadavcích a o změně cíle rozhoduje **Martin**. Když si nejsi jistý, zeptej se, nedomýšlej.

## Prostředí a nástroje

- Python **3.13**, prostředí spravuje **uv**:
  - `uv sync` – nainstaluje závislosti podle `uv.lock`
  - `uv add <balíček>` / `uv add --dev <balíček>` – přidá závislost (nikdy `pip install`)
  - `uv run <příkaz>` – spustí příkaz ve virtuálním prostředí (např. `uv run sale-shopping-agent`)
- Kód je v `src/sale_shopping_agent/` (tzv. src layout), testy budou v `tests/`.
- **Databáze:** PostgreSQL i SQLite. SQL piš tak, aby fungovalo v obou, pokud architektura neurčí jinak. Rozdíly dokumentuj.
- **Lokální model přes Ollama:** používá se pro **jednoduché a dobře ohraničené úlohy** (např. vytažení ceny a gramáže z textu, párování názvů zboží, krátká shrnutí). Nepoužívá se tam, kde je potřeba návrh, složitá logika nebo práce s více soubory.

## Git a GitHub

- Repozitář: `Zodiax75/sale-shopping-agent`, hlavní větev `main`.
- **Do `main` se nepushuje přímo.** Každá změna jde přes vlastní větev a pull request, který schvaluje Martin.
- Commity: krátký český popis v rozkazovacím způsobu („Přidej načítání konfigurace“), jedna logická změna na commit.
- **Nikdy do Gitu** nedávej hesla, API klíče ani přístupové údaje k databázi. Patří do `.env` (je v `.gitignore`); vzor bez tajných hodnot do `.env.example`.

## Kvalita

- Nový kód má mít unit testy (píše je role Tester, mentor s ní spolupracuje).
- Před PR musí projít testy: `uv run pytest` (až bude pytest přidaný).
- Když změna mění chování nebo návrh, aktualizuj dokumentaci v `docs/` ve stejném PR (nebo dej vědět Architektovi).

## Role a předávání práce

| Role | Soubor | Kdy |
|------|--------|-----|
| Architekt | `.claude/agents/architekt.md` | požadavky, návrh, dokumentace |
| Python mentor | `.claude/agents/python-mentor.md` | psaní kódu s Martinem |
| Databázový specialista | `.claude/agents/databazovy-specialista.md` | datový model, SQL, migrace |
| Tester | `.claude/agents/tester.md` | unit testy, spouštění, vyhodnocení |
| Reviewer | `.claude/agents/reviewer.md` | nezávislá kontrola po dokončení větší ucelené části |

Běžný tok práce: **Architekt** (požadavek + návrh) → **DB specialista** (datový model, je-li potřeba) → **Python mentor** (kód s Martinem) → **Tester** (testy) → po dokončení ucelené části **Reviewer**.
Každá role dělá jen svou práci; co patří jiné roli, předá jí s jasným popisem (co, proč, odkaz na požadavek).

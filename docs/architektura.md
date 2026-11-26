# Architektura (první náčrt)

> Tento dokument je zatím hrubý náčrt. Upřesní se, až budou sebrané požadavky v [pozadavky.md](pozadavky.md).

## Dané technologie

- **Python 3.13**, prostředí přes **uv**
- **SQLite** a **PostgreSQL** (otevřená otázka: kdy které, viz níže)
- **Lokální LLM přes Ollama** pro jednoduché úlohy (např. rozpoznání, zda nabídka odpovídá hledané položce, vytažení ceny z textu)
- **Git + GitHub**

## Předpokládané části systému

```
 [Zdroje slev] ──> [Sběrač] ──> [Databáze] <── [Seznam věcí, které potřebuju]
                                   │
                                   v
                           [Vyhodnocení: je to výhodné?]  (pravidla + Ollama)
                                   │
                                   v
                              [Upozornění]
```

1. **Seznam přání (watchlist)** – co hlídám, maximální cena, preferovaný obchod…
2. **Sběrač (scraper/API)** – stahuje akce ze zdrojů.
3. **Databáze** – položky, nabídky, historie cen.
4. **Vyhodnocení** – porovná nabídky se seznamem přání a s historií cen.
5. **Upozornění** – pošle zprávu zvoleným kanálem.
6. **Plánovač** – spouští sběr pravidelně.

## Otevřené otázky

- Role SQLite vs. PostgreSQL: např. SQLite pro vývoj a testy, PostgreSQL pro „ostrý“ provoz? Nebo SQLite lokálně a PostgreSQL na serveru?
- Kde agent poběží (vlastní PC, NAS, server)? Ovlivní to plánovač i databázi.
- Který model v Ollama a na jakém hardwaru.

## Záznam rozhodnutí

| Datum | Rozhodnutí |
|-------|-----------|
| 2026-11-26 | Python + uv, Git na GitHubu, src layout (`src/sale_shopping_agent`). |
| 2026-11-26 | Databáze: PostgreSQL i SQLite; lokální model přes Ollama pro jednoduché úlohy. |

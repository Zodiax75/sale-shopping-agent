# Sale Shopping Agent (Nákupní agent)

AI agent v Pythonu, který hlídá slevové akce a upozorňuje na výhodné nákupy věcí, které opravdu potřebuju.

> Stav: **kostra projektu**. Zatím umí jen pozdravit. Požadavky se teprve sbírají, viz [docs/pozadavky.md](docs/pozadavky.md).

## Co potřebuješ

- [uv](https://docs.astral.sh/uv/) – správce Pythonu, virtuálního prostředí a balíčků (nahrazuje `pip`, `venv` apod.)
- Git
- Později: [Ollama](https://ollama.com/) s lokálním modelem, PostgreSQL (SQLite je součástí Pythonu)

## Jak projekt spustit

```bash
git clone https://github.com/Zodiax75/sale-shopping-agent.git
cd sale-shopping-agent
uv sync              # vytvoří .venv a nainstaluje závislosti podle uv.lock
uv run sale-shopping-agent # spustí program
```

`uv` si sám stáhne správnou verzi Pythonu podle souboru `.python-version`.

## Struktura projektu

```
sale-shopping-agent/
├── pyproject.toml        # popis projektu a jeho závislostí
├── uv.lock               # přesné verze závislostí (needitovat ručně, spravuje uv)
├── .python-version       # verze Pythonu pro projekt
├── .gitignore            # co se nemá dostat do Gitu (.venv, hesla, databáze…)
├── src/sale_shopping_agent/    # zdrojový kód agenta
└── docs/                 # dokumentace (tým, požadavky, architektura)
```

## Dokumentace

- [docs/tym.md](docs/tym.md) – role v týmu a jak spolupracujeme
- [docs/pozadavky.md](docs/pozadavky.md) – požadavky na funkčnost (živý dokument)
- [docs/architektura.md](docs/architektura.md) – technický návrh a rozhodnutí

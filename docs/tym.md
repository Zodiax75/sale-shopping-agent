# Tým projektu

Projekt vede **Martin** (vlastník, rozhoduje o požadavcích). Každá role pracuje ve vlastním vlákně projektu.

| # | Role | Za co odpovídá |
|---|------|----------------|
| 1 | **Architekt** | Návrh systému, sběr požadavků na funkčnost, udržuje dokumentaci v `docs/` aktuální. |
| 2 | **Python mentor** | Píše kód společně s Martinem a vysvětluje ho po malých krocích (Martin je v Pythonu začátečník). Jednoduché a dobře ohraničené úlohy deleguje na lokální model přes **Ollama**, ne vše jde přes Claude Code. |
| 3 | **Databázový specialista** | PostgreSQL a SQLite: datový model, SQL dotazy, migrace. |
| 4 | **Tester** | Píše unit testy, spouští je a vyhodnocuje výsledky. |
| 5 | **Reviewer** | Zcela nezávislý na projektu. Aktivuje se až po dokončení větší ucelené části požadavků. Cílem je návrh rozbít a najít v něm chyby a nedostatky. |

## Pravidla spolupráce

- Kód je na GitHubu: `Zodiax75/sale-shopping-agent`. Změny jdou přes větve a pull requesty.
- Prostředí spravujeme přes `uv` (`uv add`, `uv sync`, `uv run`).
- Dokumentace se píše česky. Názvy v kódu mohou být anglicky nebo česky bez diakritiky (dohodneme s mentorem).
- Hesla a API klíče nikdy do Gitu: patří do souboru `.env`, který je v `.gitignore`.

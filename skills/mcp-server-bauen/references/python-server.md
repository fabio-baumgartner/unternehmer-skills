# Python-MCP-Server: Muster

Für Nutzer, die Python bevorzugen. Wenn Abruf möglich ist, zusätzlich die aktuelle SDK-README laden: `https://raw.githubusercontent.com/modelcontextprotocol/python-sdk/main/README.md`

## Projektstruktur

```
mcp-[dienstname]/
├── pyproject.toml       oder requirements.txt
├── README.md
└── server.py
```

Abhängigkeiten: `mcp` (das offizielle SDK, enthält FastMCP) und `httpx` für API-Aufrufe.

```
pip install "mcp[cli]" httpx
```

## Server-Grundgerüst (server.py)

```python
import os
import httpx
from mcp.server.fastmcp import FastMCP

mcp = FastMCP("dienstname")

API_KEY = os.environ.get("DIENST_API_KEY")
if not API_KEY:
    raise SystemExit("Fehler: Umgebungsvariable DIENST_API_KEY fehlt.")

BASE_URL = "https://api.dienst.de/v1"


@mcp.tool()
async def dienst_rechnungen_auflisten(status: str = "offen", limit: int = 20) -> str:
    """Listet Rechnungen aus [Dienst] auf.

    Nutze dies, um offene oder bezahlte Rechnungen zu finden, bevor du mit
    einer einzelnen Rechnung arbeitest.

    Args:
        status: Filter nach Status: "offen", "bezahlt" oder "alle".
        limit: Maximale Anzahl Ergebnisse (1 bis 100).
    """
    async with httpx.AsyncClient() as client:
        res = await client.get(
            f"{BASE_URL}/invoices",
            params={"status": status, "limit": limit},
            headers={"Authorization": f"Bearer {API_KEY}"},
        )
    if res.status_code != 200:
        return (
            f"Abruf fehlgeschlagen (HTTP {res.status_code}). "
            "Prüfe den API-Key und ob der Dienst erreichbar ist."
        )
    return res.text


if __name__ == "__main__":
    mcp.run(transport="stdio")
```

## Regeln

- **Der Docstring ist die Tool-Beschreibung.** Erster Satz: was das Tool tut. Zweiter: wann Claude es nutzen soll. Args-Abschnitt mit Beispielwerten.
- **Tool-Namen im Muster `dienst_objekt_verb`**, als Funktionsname.
- **Fehler als verständlicher Text zurückgeben**, mit konkretem nächsten Schritt, keine rohen Tracebacks.
- **Pagination und Limits** bei Listen-Tools, Antworten kompakt halten.
- **API-Key aus der Umgebung**, nie im Code, nie in Git.
- **Nichts auf stdout drucken** (kein `print` für Debug): stdout gehört dem Protokoll. Debug auf stderr oder ins Log.

## Testen

```bash
python -m py_compile server.py
npx @modelcontextprotocol/inspector python server.py
```

Im Inspector jedes Tool mit echten Werten aufrufen, mindestens einen Fehlerfall provozieren.

# TypeScript-MCP-Server: Muster

Das empfohlene Setup. Wenn Abruf möglich ist, zusätzlich die aktuelle SDK-README laden: `https://raw.githubusercontent.com/modelcontextprotocol/typescript-sdk/main/README.md`

## Projektstruktur

```
mcp-[dienstname]/
├── package.json
├── tsconfig.json
├── README.md            Kurzanleitung: was der Server kann, wie er installiert wird
└── src/
    ├── index.ts         Server-Start und Tool-Registrierung
    └── client.ts        API-Client des Zieldiensts (Auth, Fehlerbehandlung)
```

## package.json (Kern)

```json
{
  "name": "mcp-dienstname",
  "version": "1.0.0",
  "type": "module",
  "bin": { "mcp-dienstname": "./dist/index.js" },
  "scripts": {
    "build": "tsc",
    "start": "node dist/index.js"
  },
  "dependencies": {
    "@modelcontextprotocol/sdk": "latest",
    "zod": "^3.23.0"
  },
  "devDependencies": {
    "typescript": "^5.5.0",
    "@types/node": "^22.0.0"
  }
}
```

## Server-Grundgerüst (src/index.ts)

```typescript
import { McpServer } from "@modelcontextprotocol/sdk/server/mcp.js";
import { StdioServerTransport } from "@modelcontextprotocol/sdk/server/stdio.js";
import { z } from "zod";

const server = new McpServer({
  name: "dienstname",
  version: "1.0.0",
});

// API-Key aus der Umgebung, nie im Code
const API_KEY = process.env.DIENST_API_KEY;
if (!API_KEY) {
  console.error("Fehler: Umgebungsvariable DIENST_API_KEY fehlt.");
  process.exit(1);
}

server.registerTool(
  "dienst_rechnungen_auflisten",
  {
    title: "Rechnungen auflisten",
    description:
      "Listet Rechnungen aus [Dienst] auf. Nutze dies, um offene oder " +
      "bezahlte Rechnungen zu finden, bevor du mit einer einzelnen arbeitest.",
    inputSchema: {
      status: z
        .enum(["offen", "bezahlt", "alle"])
        .default("offen")
        .describe("Filter nach Status, z. B. 'offen'"),
      limit: z.number().int().min(1).max(100).default(20)
        .describe("Maximale Anzahl Ergebnisse"),
    },
  },
  async ({ status, limit }) => {
    const res = await fetch(
      `https://api.dienst.de/v1/invoices?status=${status}&limit=${limit}`,
      { headers: { Authorization: `Bearer ${API_KEY}` } }
    );
    if (!res.ok) {
      return {
        content: [{
          type: "text",
          text: `Abruf fehlgeschlagen (HTTP ${res.status}). ` +
            `Prüfe den API-Key und ob der Dienst erreichbar ist.`,
        }],
        isError: true,
      };
    }
    const data = await res.json();
    return {
      content: [{ type: "text", text: JSON.stringify(data, null, 2) }],
    };
  }
);

const transport = new StdioServerTransport();
await server.connect(transport);
```

## Regeln

- **Ein Tool pro Aktion**, Namen im Muster `dienst_objekt_verb`.
- **Jede Beschreibung sagt, WANN das Tool sinnvoll ist**, nicht nur was es tut. Claude wählt danach aus.
- **Fehler als hilfreicher Text mit `isError: true`**, mit konkretem nächsten Schritt.
- **Pagination**: bei Listen-Tools `limit` und einen Fortsetzungs-Parameter anbieten, große Antworten kürzen.
- **Logs auf stderr** (`console.error`), nie auf stdout: stdout gehört dem Protokoll.
- **Schreibende Tools** (`anlegen`, `ändern`, `löschen`): mit destructive/readOnly-Annotations kennzeichnen und im Tool-Text erwähnen, dass die Aktion Daten verändert.

## Bauen und Testen

```bash
npm install
npm run build
npx @modelcontextprotocol/inspector node dist/index.js
```

Im Inspector jedes Tool einmal mit echten Werten aufrufen. Erst wenn alle Tools liefern, weiter zur Installation.

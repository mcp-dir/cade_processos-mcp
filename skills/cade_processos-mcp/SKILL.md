---
name: cade_processos-mcp
description: Skill da REST API do CADE: Processos na MCP.AI: 1 endpoint em /api/cade_processos. CADE: Processos, consulta em fonte oficial. Hospedado pela plataforma, sem credenciais da plataforma, pague por consulta com crédito pré-pago. Autentique com workspace API key (sk_live) gerada em app.mcp.ai/settings/api-keys. Use quando o usuário pedir algo coberto pelos endpoints.
---

# CADE: Processos — REST API skill

Você tem acesso à **CADE: Processos** REST API na MCP.AI.

> CADE: Processos, consulta em fonte oficial. Hospedado pela plataforma, sem credenciais da plataforma, pague por consulta com crédito pré-pago.

## Base URL

```
https://api.mcp.ai/api/cade_processos
```

Todo endpoint é um **POST** na Base URL + o path abaixo. Os parâmetros vão no corpo JSON.

## Autenticação

Inclua em toda request:

```
Authorization: Bearer sk_live_...
Content-Type: application/json
```

> Gere sua chave em **https://app.mcp.ai/settings/api-keys** (workspace API key `sk_live_…`, não expira, revogável). Uma única chave serve pra todos os seus MCPs.

## Formato de resposta

```json
{ "ok": true, "tool": "<tool_id>", "result": <payload> }
```

## Exemplo cURL

```bash
curl -X POST https://api.mcp.ai/api/cade_processos/consultar \
  -H "Authorization: Bearer sk_live_..." \
  -H "Content-Type: application/json" \
  -d '{}'
```

## Reportar problemas

Se um endpoint retornar erro, vazio ou dado inesperado, reporte (não desista calado): **POST /api/cade_processos/report** com `{ "message": "...", "context"?: "...", "conversation"?: [...] }`. Isso notifica o time da MCP.AI.

## Endpoints (1)

#### `cade_processos_consultar`

CADE: Processos, consulta em fonte oficial. _(POST /api/cade_processos/consultar)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `processo` | string | Não | Parâmetro de consulta "processo". |
| `query` | string | Não | Parâmetro de consulta "query". |
| `interessado_remetente` | string | Não | Parâmetro de consulta "interessado_remetente". |
| `pagina` | string | Não | Parâmetro de consulta "pagina". |
| `tipo_pesquisa` | string | Não | Parâmetro de consulta "tipo_pesquisa". |

---

Este MCP também funciona via **conexão MCP** (Claude / Cursor) em `https://api.mcp.ai/p_cade_processos` — veja o [README](../../README.md). A skill acima é pra consumir a **REST API** direto (agente próprio / código).

# Parallel Search MCP

Give Fleet's built-in Agent pane web search and page fetching with
[Parallel Search MCP](https://docs.parallel.ai/integrations/mcp/search-mcp).
The free endpoint needs no Parallel account or API key, and anonymous search uses Fast mode.
It is intended for exploration and light use; rate limits apply.

## Connect

1. Open an Agent pane and select its **Settings** tab.
2. Find **MCP servers**, click **Add server**, and select **Paste JSON**.
3. Paste this configuration and click **Add server**:

   ```json
   {
     "mcpServers": {
       "parallel-search": {
         "url": "https://search.parallel.ai/mcp",
         "headers": {
           "User-Agent": "Fleet"
         }
       }
     }
   }
   ```

4. Wait for the server to connect. Expand **parallel-search** to see the
   `web_search` and `web_fetch` tools.

Fleet uses Streamable HTTP for this URL. No local MCP process or additional runtime is needed.
The server is available to every Agent pane; add it once.
Your coding model still uses its existing OpenRouter or local model configuration.

## Try it

In an Agent conversation, ask:

> Use the parallel-search MCP tools to find the current Electron security checklist.
> Fetch the relevant official documentation page and summarize three recommendations
> with source links.

The MCP tools are separate from Fleet's built-in web tools. Ask for
**parallel-search** explicitly when you want to use this server.
Parallel fetches public web pages remotely; use Fleet's local fetch for localhost
or private-network pages.

To stop using the server, turn off its toggle in **MCP servers**.
Expand the server to turn off individual tools, or use its menu to remove it.
If it does not connect, check the endpoint URL and use **Reconnect** in the server menu.
For higher limits and authentication options, see the
[Parallel Search MCP documentation](https://docs.parallel.ai/integrations/mcp/search-mcp).

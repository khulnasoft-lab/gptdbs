# Jina Web Reader Tool

A GPT-DB tool of [Jina AI Reader](https://github.com/jina-ai/reader).

## Usage

How to use it in GPT-DB?  First, install the tool:

```bash
gptdb app install jina-web-reader
```

It includes two tools:
- `jina_reader_web_search`: Search web pages using Jina AI Web Search(`s.jina.ai`) API.
- `jina_reader_web_crawler`: Crawl web pages using Jina AI Reader(`r.jina.ai`) API.


Then, create an APP in your GPT-DB web page.



![jina-web-reader-1.png](../../assets/img/resources/jina-web-reader-1.png)

Last, you can use the tool in the APP.

![jina-web-reader-2.png](../../assets/img/resources/jina-web-reader-2.png)


## Configuration

You can configure the tool by setting the environment variables.

### Common Configuration

- `GPTDB_TOOL_JINA_API_TOKEN={your_jina_api_token}`: The Jina AI API token. You can get it from [Jina AI](https://jina.ai/).

### `jina_reader_web_crawler`

- `GPTDB_TOOL_JINA_API_READER_URL=https://r.jina.ai`: The Jina AI Reader API URL. Default is `https://r.jina.ai`.
- `GPTDB_TOOL_JINA_API_READER_TIMEOUT=60`: The Jina AI Reader API timeout. Default is `60`(seconds).

### `jina_reader_web_search`

- `GPTDB_TOOL_JINA_API_SEARCH_URL=https://s.jina.ai`: The Jina AI Web Search API URL. Default is `https://s.jina.ai`.
- `GPTDB_TOOL_JINA_API_SEARCH_TIMEOUT=60`: The Jina AI Web Search API timeout. Default is `60`(seconds).
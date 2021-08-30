# Authentication

> To authorize, use this code:

```shell
# With shell, you can just pass the correct header with each request
curl "https://api.omniship.eu/api/<platform>/v1/<resource>"
  -H "Authorization: Bearer FkihCtzyXWvutSRUaaEupN8hvABcDefgHI6lJKvv"
  -H "Content-Type: application/json"
```

> Make sure to replace `FkihCtzyXWvutSRUaaEupN8hvABcDefgHI6lJKvv` with your API key.

OMNISHIP uses API keys to allow access to the API. You can create an API key within the <a href="https://app.omniship.eu/user/api-tokens" target="_blank">OMNISHIP application</a>.

In order to authenticate properly, please put <code>Authorization: Bearer &lt;API Access Token&gt;</code> in the request header. OMNISHIP expects for the API key to be included in every API requests to the server in a header that looks like the following:

`Authorization: Bearer FkihCtzyXWvutSRUaaEupN8hvABcDefgHI6lJKvv`

<aside class="notice">
You must replace <code><strong>FkihCtzyXWvutSRUaaEupN8hvABcDefgHI6lJKvv</strong></code> with your personal API key.
</aside>


# Module: <code>nintendo.dauth</code>
Provides a client for the [device authentication server](https://github.com/kinnay/nintendo/wiki/DAuth-Server).

<code>**class** DAuthError([NDASError](switch.md#ndaserror))</code><br>
<span class="docs">Raised when the `dauth` server returns an error code.</span>

<code>**class** [DAuthClient](#dauthclient)</code><br>
<span class="docs">The `dauth` client.</span>

## DAuthClient
`SCSI: int = 0x146C8AC7B8A0DB52`<br>
`ESHOP: int = 0x41F4A6491028E3C4`<br>
`BCAT: int = 0x67BF9945B45248C6`<br>
`SATA: int = 0x6AC5A6873FE5F68C`<br>
`ACCOUNT: int = 0x81333C548B2E876D`<br>
`NPNS: int = 0x83B72B05DC3278D7`<br>
`BAAS: int = 0x8F849B5D34778D8E`<br>
`BEACH: int = 0x93AF0ACB26258DE9`<br>
`DRAGONS: int = 0xD5B6CAC2C1514C56`<br>
`PCTL: int = 0xDC656EA03B63CF68`<br>
`PREPO: int = 0xDF51C436BC01C437`

<code>**def _\_init__**(keyset: [KeySet](switch.md#keyset))</code><br>
<span class="docs">Creates a new `dauth` client with the given keyset.</span>

<code>**def set_certificate**(cert: [TLSCertificate](https://anynet.readthedocs.io/en/latest/reference/tls/#tlscertificate), key: [TLSPrivateKey](https://anynet.readthedocs.io/en/latest/reference/tls/#tlsprivatekey)) -> None</code>
<span class="docs">Changes the client certificate of the current TLS context. The server rejects all requests without a valid client certificate.</span>

<code>**def set_context**(context: [TLSContext](https://anynet.readthedocs.io/en/latest/reference/tls/#tlscontext)) -> None</code><br>
<span class="docs">Changes the TLS context. By default, the server certificate is verified with `Nintendo CA - G3` and no client certificate is used.</span>

<code>**def set_platform_region**(region: int) -> None</code><br>
<span class="docs">Changes the platform region. This affects the `ist` parameter in the device authentication request. The default is `1`.</span>

<code>**def set_url**(url: str) -> None</code><br>
<span class="docs">Changes the server to which the HTTP requests are sent. The default is `dauth-lp1.ndas.srv.nintendo.net`.

<code>**def set_user_agent**(user_agent: str) -> None</code><br>
<span class="docs">Changes the user agent of the `dauth` client. The default depends on the latest system version.

<code>**def set_power_state**(state: str) -> None</code><br>
<span class="docs">Changes the content of the `X-Nintendo-PowerState` header. The default is `"FA"`.

<code>**def set_api_version**(version: int) -> None</code><br>
<span class="docs">Selects the DAuth API version. Currently, only `6` and `7` are supported. The default depends on the latest system version.</span>

<code>**def set_key_generation**(keygen: int) -> None</code><br>
<span class="docs">Changes the master key revision that's used for the challenge. The default depends on the latest system version.</span>

<code>**def set_system_digest**(digest: str) -> None</code><br>
<span class="docs">Changes the system version digest that's sent to the `dauth` server. The default depends on the latest system version.</span>

<code>**def set_system_version**(version: int) -> None</code></br>
<span class="docs">Updates the user agent, API version, system version digest and master key revision for the given system version. The system version should be given as a decimal integer. For example, `1002` is system version `10.0.2`. All system versions from `9.0.0` and later are supported.</span>

<code>**async def challenge**() -> dict</code><br>
<span class="docs">Requests a challenge from the `dauth` server.</span>

<code>**async def device_token**(client_id: int) -> dict</code><br>
<span class="docs">Requests a device token from the `dauth` server. The challenge is done automatically.</span>

<code>**async def edge_token**(client_id: int, vendor_id: str = "akamai") -> dict</code><br>
<span class="docs">Requests an edge token from the `dauth` server. The challenge is done automatically.</span>

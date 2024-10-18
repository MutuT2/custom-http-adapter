# custom-http-adapter
Requests module that contains and HTTPAdapter which will allow to use requests with additional features.


## what is this?
&emsp;&emsp; The purpose of this Python HTTP adapters is to allowPython programs to
interact with web servers over the HTTP protocol. HTTP (Hypertext Transfer Protocol) is
a protocol used to transfer data between web servers and clients, such as web browsers
or applications.<br />

&emsp;&emsp; Using a Python HTTP adapter can simplify the process of interacting with web
servers, as it abstracts away many of the low-level details of the HTTP protocol. This
allows developers to focus on the logic of their application rather than the intricacies of
sending and receiving HTTP/HTTPS requests and responses.


## Key Features Implemented:


1. **Custom Port Handling:** If a port is not specified, it defaults to port 80 for HTTP and 443 for HTTPS. If a port is provided, it modifies the URL accordingly.

2. **Custom Headers:** The adapter allows adding custom headers before sending the request.

3. **Query Parameters & Request Body:** The params argument is used for query parameters, and json for request bodies in POST/PUT requests.

4. **Authentication:** The add_auth method handles three types of authentication:

&emsp;&emsp;&emsp;&emsp;- **Basic Authentication:** via username and password.<br />
&emsp;&emsp;&emsp;&emsp;- **Bearer Token Authentication:** using a token.<br />
&emsp;&emsp;&emsp;&emsp;- **No Authentication:** if not provided.

5. **Retry Logic:** Using urllib3.util.retry.Retry, it automatically retries requests that fail due to network issues or specific status codes. It uses an exponential backoff for throttling or retry-after header handling.

6. **API Throttling:** If the response includes a Retry-After header (common in API rate limiting), it respects that delay. Otherwise, it uses exponential backoff for retries.

7. **SSL Verification:** SSL verification can be enabled or disabled through configuration. By default, it's disabled.

8. **Configurable Timeouts:** The timeout is configurable, with a default of 10 seconds.

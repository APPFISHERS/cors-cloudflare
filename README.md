# cloudflare-cors-anywhere
Cloudflare CORS proxy in a worker.

CLOUDFLARE-CORS-ANYWHERE

Source:
https://github.com/APPFISHERS/cors-cloudflare



Deploy workers:
https://workers.cloudflare.com/

Example:
```javascript
fetch('https://test.workername.workers.dev/?https://link', {
  method: 'post',
  headers: {
    'x-foo': 'bar',
    'x-bar': 'foo',
    'x-cors-headers': JSON.stringify({
      // allows to send forbidden headers
      // https://developer.mozilla.org/en-US/docs/Glossary/Forbidden_header_name
      'cookies': 'x=123'
    }) 
  }
}).then(res => {
  // allows to read all headers (even forbidden headers like set-cookies)
  const headers = JSON.parse(res.headers.get('cors-received-headers'))
  console.log(headers)
  return res.json()
}).then(console.log)
```

Note:

All received headers are also returned in "cors-received-headers" header.



To create your own is very easy, you just need to set up a cloudflare account and upload the worker code.  



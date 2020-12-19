# sagecell-node-client

## Overview

This is node module to integrate to SageCell server via JS.

## Example

```javascript
var client = new sagecell({
    onstatuschange: (status) => {
        console.log("status change", status);
        if (status == "connected") {
            client.sendCommand(null, "plot(x,x)");
        }
    },
    onmessage: (msg) => {
        console.log("msg", msg);
    },
    onerror: (from, err) => {
        console.log("err", from, err);
    },
    timeout: 30
});
client.connect();
```

Listening to responses can also be done using promises:
```javascript
client.sendCommand(null, "plot(x,x)").then((res) => {
    console.log("on message", res);
}).catch((err) => {
    console.log("on err", err);
});
```

## References

Sagecell: https://sagecell.sagemath.org/

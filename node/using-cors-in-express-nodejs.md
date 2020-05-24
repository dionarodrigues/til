# Using CORS in Express - NodeJS

__CORS is a node.js package for providing a [Connect/Express](http://expressjs.com/) middleware that can be used to enable CORS with various options.__

The easiest way to get [CORS](https://en.wikipedia.org/wiki/Cross-origin_resource_sharing) working in Express is by using the [cors npm module](https://www.npmjs.com/package/cors).

Cross-origin resource sharing (CORS) allows AJAX requests to skip the [Same-origin policy](https://developer.mozilla.org/en-US/docs/Web/Security/Same-origin_policy) and access resources from remote hosts.

## How to use

Adding the dependency and use it as middleware:

```
import express from 'express';
import cors from 'cors';

const app = express();

app.use(cors());

/* your regular routes go here */

```

Easy peasy, isn't it? 👌

### Restricting allowed hosts

If you want to restrict AJAX access to a single origin, you can use the origin option:

```
app.use(cors({
  origin: 'http://yourapp.com'
}))
```

More settings [here](https://www.npmjs.com/package/cors).
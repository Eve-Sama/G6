---
title: Layout with Web-Worker
order: 5
---

The layout algorithm costs a lot in large scale graph visualization. If you config the layout for a graph, the layout algorithm must be done before rendering. In some web applications, this process will block the page and the end users will not able to interact with other components of the page. To address this issue, G6 provids the Web-Worker for **General Graph**. You only need to assign `workerEnabled` to `true` when configuring the layout. For example:

```javascript
const graph = new G6.Graph({
  ...                      // Other configurations for graph
  layout: {                // Object, layout methods and its configurations
  	type: 'fruchterman',
    workerEnabled: true,   // enable Web-Worker
    // ...                 // other configurations for the layout
  }
});
```

Note:

- TreeGraph layouts do not support Web-Worker;
- Sub-Graph layout mechanism do not support Web-Worker;
- Worker will visit the latest online version of @antv/layout. If your application cannot reach the online resource, download and save the [layout script](https://unpkg.com/@antv/layout@latest/dist/layout.min.js), and put it on an address which is visitable for your application. And then config `workerScriptURL` with the address in `layout`.

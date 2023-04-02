## Implementation

## Challanges

### Get a Own URL (origin)
Can get implemented via highlevel domain like .dev.localhost.

### fs.watch 
gets implemented via listing for events as also regular crawling and updating the file entrys and call 

```ts
https.get({ method: 'OPTIONS' url: '/:hash' }); // => Allow: PUT || UPDATE PUT If Empty Update if exists.
https.get({ method: 'PUT' url: '/:hash', body: 'content' }); // => Allow: PUT got replyed by OPTION
```

## Optimisation
This algo works for most projects quite well even more well when node_modules is only 1x syned

To speed that up on large projects we would maybe use some custom methods like directly passing folder handels of the operating system.

## Efficent transport
they use localForage already maybe reuse that.

then store only data urls in case of text/* encodeURI() String in case of */ base64
```js
const base64_arraybuffer = async (response) => {
   
    const base64url = await new Promise((r) => {
        const reader = new FileReader()
        reader.onload = () => r(reader.result)
        reader.readAsDataURL(new Blob([await response.blob()],{ type: response.type }))
    })
    /* "data:application/octet-stream;base64,${data}" */
    return `data:application/octet-stream;base64, ${base64url.split(",", 2)[1]}`
}

// example use:
await base64_arraybuffer(new Uint8Array([1,2,3,100,200]))


fetch(new Blob([await (await (otherResponse.blob())).arrayBuffer()], { type: mimeType })).then(response=>response.text());
new Blob([new UInt8Array([]).buffer], { type: mimeType })
```


## API
Example mapping a serverSide API that implements a protocol like nodejs.

```ts
const largeCallback = async () {
  return import('/components/fs/fs.js').then(({ readdir }) => readdir).then
}

// `&callback=( ${encodeURI(`${largeCallback}`)} )`;

// using serverSideVariables [[app:app_id]]
document.body.appendChild(Object.assing(document.createElement('script'),{ src: "/api/fs.readdir.json?pathname="node_modules"&callback=import('/components/fs/fs.js').then(({ readdir }) => readdir).then" }))
```

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

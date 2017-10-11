## Angular meetup - Australia Post - 19th Sep 2017 

### Alex Burakevych - ES2017
#### ES2017
- String padding
- Object.getOwnPropertyDescriptors
- Trailing commas in function parametere lists and calls
- Async functions
- Object.values / Object.entries
- Shared memory and atomics (supporting concurrency, service workers)
- Lifting template literal resrictions


#### ES2018
- import()    -- can have conditions about import, eg, only if in IE
- Promise.prototype.finally
- global (instead of window.... for serverside)
- Asynchronous Iteration
- BigInt
- Class and Property Decorators
- Private methods and accessors. 
- Observables (probably not finalised)


https://github.com/tc39/ecma262

### Vva Bilyachat - Google Material Design


### "Brett Iglo" - chief engineer at Odecee Improving the Perf of and Ionic App.
http://techradar.odeceelabs.com.au

### Why Ionic?
- because collaborative, wanted desktop story. 
- Wanted single code base.
- get 'native look and feel' (hmmm..)

### Initial perf of app was poor.
- app.bundle.js was 5.3MB!! 
- 4s load time
- People drop out if it's slow. Even after 3.3s, 20% will drop off (from Google)
- 

### Fixes
 - Server compression - this reduced the 5mb file something like 70%
 - Headers
 - converted PNG to SVG
 - 

### Clientside optimisations
- AOT
    - Ng supports AOT and JIT compilation. When you choose AOT instead of JIT, ** you don't ship the compiler!!! **
    - use `ngc` instead of `tsc` compile. This is done through the tscofig.json file. documented well onsite. Use --prod build. 
    - AOT compilation went from 5.5MB to 1.4MB... then, plus with gzip, came down to 400kb (STILL BIG!!) 
- Code Splitting
    - side effect of supporting deep-ilnks: code splitting
    - @IonicPage({segment: 'radar/:radarId'))}
    - Didn't have a massive impact on perf as the code eventually has to be downloaded, just not at the first page view.
- Service Workers
    - Client side promxy written in JavaScript
    - Sits between the browser and the webserver
    - can intercept http requests and can get the data from elsewhere, eg the cache.
    - Powers PWAs (progressive web apps)
    - Perf
        - Caching static assets
        - offline mode
    - Push notifications
    - Native app behaviuors
        - Home screen icons
        - No browser chrome.
    - Used Workbox
        - CLI
        - Webpack plugin
    - ionic-app-scripts --prod
    - Set up service workers so that any requests to APIs went to the network first, whilst any calls to assets went to the cache first.
    - Workbox is POWERFUL
    - start simple then add capabilities
    - debugging can be tricky. Can simulate an offline mode. 
    - In chrome dev tools
        - Service workers are under application tab. 
        
#### Result?
- On web, Got first load to under 1s. Subsequent reloads, slightly faster by not noticably faster. 
- On mobile, subsequent loads were MUCH faster. This was due to service workers. Note, this is not for Ionic. This was mobile web.


### Erin - Austpost - Async / Await
- Pre ES6, you need a promise library. ES6 brings native promises. 
- Async / Await makes promises better. 
- She went into generators. I took a photo. 
- she then changed the yields in her generator to use ES6 awaits. I took another photo. The photos are good.
- BASICALLY!! INSTEAD OF USING PROMISES WITH THENS, SHE USES AWAITS.
- The bottom line is that ASYNC doesn't do anything that you can't do with generators or promises, but they do make your code a lot easier to deal with. 
- You can mix and match async and promises. Async just returns a normal promise. 

#### Gotchas.
- Can't use inside callbacks. 


    


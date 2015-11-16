# Storage in the browser

There is a some research on quotas here: http://www.html5rocks.com/en/tutorials/offline/quota-research/  
Overview of techniques: http://www.html5rocks.com/en/tutorials/offline/storage/

After playing around a bit with http://demo.agektmr.com/storage/ here are the options to save > 1GB of data permanently, with quota permissions:

- localStorage: Nope
- SessionStorage: Nope
- WebSQL: Was making me lag really badly and crashed my browser multiple times.
- IndexedDB: Was making me lag, really weird behaviour with permanent/temp storage. Really slow.
- **FileSystem: Worked without complaints. Way faster than the other options. I'd suggest we use this.**

The drawbacks to FileSystem are, that it only works on Chrome, but after reading up a bit on it, I don't think we have a good shot with other browsers anyway...

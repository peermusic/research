# Storage in the browser

## Useful references

- [Overview of techniques](http://www.html5rocks.com/en/tutorials/offline/storage/)
- [Research on quotas](http://www.html5rocks.com/en/tutorials/offline/quota-research/)
- [Demo page](http://demo.agektmr.com/storage/)

## Allowed file sizes

Since we are trying to save an entire music library in the browser, we need the ability to save at least 1.000 files with up to 10 MB. The table below shows the possible techniques of saving data with the maximum total size.

Technique       | Chrome (Desktop)      | Chrome (Andriod)
--------------- | --------------------- | ---------------------
FileSystem      | Up to requested quota | Up to requested quota
IndexedDB       | Up to requested quota | Up to requested quota
WebSQL          | Up to requested quota | Up to requested quota
LocalStorage    | 10 MB                 | 10 MB
SessionStorage  | 10 MB                 | 10 MB

As shown in the table, Local- and SessionStorage are not possible for our use-case, and we will concentrate on the last 3 options

## Browser Support

Since we are writing our application with a main focus on Chrome (Desktop & Android), we didn't make browser support to one of our main decision points, but it is an interesting discussion point nevertheless. 

Technique       | Browser Support
--------------- | ---------------------
FileSystem      | [Chrome, Opera](http://caniuse.com/#search=FileSystem) - no longer maintained
IndexedDB       | [All major browsers](http://caniuse.com/#search=IndexedDB), but not supported in Chrome for iOS
WebSQL          | [Chrome, Safari, Opera](http://caniuse.com/#search=WebSQL)- no longer maintained

## Performance

Using the [demo page](http://demo.agektmr.com/storage/), we tested the techiques for our use-case (multiple hundred files of about 5-10MB).

Technique       | Browsersupport
--------------- | ---------------------
FileSystem      | Fast, handles even big amounts of data well
IndexedDB       | Freezes the browser, really slow, non-predictable behaviour with permanent and temporary storage (might be a bug in the demo page), 
WebSQL          | Freezes the browser, Slow, doesn't handle larger files well, crashes the browser easily

## Decision: FileSystem

Although the FileSystem API is no longer officially maintained, it is still the fastest and most performant method of storing large amounts of data, without any competition. The missing availability on other browsers as a drawback was okay for us, since the application focuses on Chrome for Desktop and Andriod.

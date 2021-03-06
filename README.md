# Up2Date
Android Micro-Library for checking if your app is up-to-date.

### Adding to your Android app
In your root level `build.gradle`

```	
allprojects {
	repositories {
		...
		maven { url "https://jitpack.io" } // add this line
	}
}
```

In your app/module level `build.gradle`

```
dependencies {
	compile 'com.github.andressantiago:Up2Date:9bb682a365dcd948f8a7ec6757eb5d0d38516bd7'
}
```

Note: If you want a particular commit,
replace the hash with a commit hash of your liking.

### Usage
`Up2Date.checkVersion(...)` requires a `Context` (usually an `Activity`), and a `Up2Date.VersionListener`.

The listener will have two callbacks. 

A `versionCheckSuccess` that returns `true` if the current app's version is equal
to the app's Play Store listing version, and a `String` of the Play Store listing's version (e.g. `"2.9.2"`).

A `versionCheckError` returns a `FailureReason` code. This may occur when unable to find 
the app's package name in the Play Store for example.

For example:

```
Up2Date.checkVersion(this, new Up2Date.VersionListener() {
    @Override
    public void versionCheckSuccess(boolean b, String s) {
        Log.i(TAG, "Success - UpToDate: " + b + " VersionInStore: " + s);
    }
    
    @Override
    public void versionCheckError(int i) {
        Log.i(TAG, "Failure - ErrorCode: " + i);
    }
});
```

### Status
This project is very much a **WORK IN PROGRESS**.

### Contribute
Contributions are welcome!

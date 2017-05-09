# AdoptOpenJDK API

The AdoptOpenJDK API provides a way to consume JSON information about the AdoptOpenJDK releases and nightly builds.

Here is an example using `curl` (see the [curl documentation](https://curl.haxx.se/docs/tooldocs.html)). This command and returns information about all AdoptOpenJDK releases, and includes an 'accept header' to specify **v1.0.0** of the API. This will ensure consistency when future versions of the API are announced.

```
curl -H 'accept-version: 1.0.0' api.adoptopenjdk.net/releases
```

However, new API developments could benefit your project! Sign up to the [mailing list](http://mail.openjdk.java.net/mailman/listinfo/adoption-discuss) where API updates will be announced, and visit [adoptopenjdk.net](https://adoptopenjdk.net) to find out more about the community.

## v1.0.0

### Paths
You can append the following paths to the `api.adoptopenjdk.net` URL, either in the above `curl` format, in a browser, or through an HTTP client, to return different JSON information:

|Path               |Returns  |
|-------------------|---------|
|`/releases`          |All releases, all platforms.      |
|`/releases/latest`   |The latest release, all platforms.|
|`/nightly`           |All nightly builds, all platforms.|
|`/nightly/latest`    |The latest nightly build, all platforms.   |
|`/nightly/<platform>`|All nightly builds, one specified platform.|
|`/nightly/<platform>/latest`|The latest nightly build, one specified platform.|

### Platforms
You can specify a platform by inserting one of the following names, in upper-case or lower-case, where you see `<platform>` in the path options:

- `x64_linux`
- `x64_mac`
- `s390x_linux`
- `ppc64le_linux`

### Additional options
By default, the API returns a pretty-printed JSON. You can disable this pretty-printing by appending `?pretty=false` to the end of any URL. For example:
```
curl -H 'accept-version: 1.0.0' api.adoptopenjdk.net/releases?pretty=false
```

### Examples
```
curl -H 'accept-version: 1.0.0' api.adoptopenjdk.net/nightly
curl -H 'accept-version: 1.0.0' api.adoptopenjdk.net/releases/latest?pretty=false
curl -H 'accept-version: 1.0.0' api.adoptopenjdk.net/nightly/x64_linux/latest
```
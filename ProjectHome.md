# Android Maps Extensions  #

[![](http://developer.android.com/images/brand/en_generic_rgb_wo_60.png)](https://play.google.com/store/apps/details?id=pl.mg6.android.maps.extensions.demo)

This library "extends" `GoogleMap` and related objects from [Google Maps Android API v2](https://developers.google.com/maps/documentation/android/).

| ![http://android-maps-extensions.googlecode.com/files/before_clustering.jpeg](http://android-maps-extensions.googlecode.com/files/before_clustering.jpeg) | ![http://android-maps-extensions.googlecode.com/files/after_clustering.jpeg](http://android-maps-extensions.googlecode.com/files/after_clustering.jpeg) |
|:----------------------------------------------------------------------------------------------------------------------------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------|

## Motivation ##

[Google Maps Android API v2](https://developers.google.com/maps/documentation/android/) is one small step for Google, a giant leap for Android developers. Even though some said it carries a lot of limitations and is not extensible, Android Maps Extensions brings a few very useful features, most notably: **Marker Clustering** and ability to carry model data within markers (and other visual objects) to be retrieved as needed.

## Extensions ##

Currently implemented extensions include:
  * Marker Clustering with `GoogleMap.setClustering(ClusteringSettings)`
    * `ClusteringSettings.clusterOptionsProvider(ClusterOptionsProvider)` is required for it all to work
    * `ClusteringSettings.addMarkersDynamically` when having [too many markers](https://developers.google.com/maps/articles/toomanymarkers)
    * `ClusteringSettings.clusterSize` to control... cluster size
  * `Object getData()` and `setData(Object)` on
    * `Marker`
    * `Circle`
    * `GroundOverlay`
    * `Polygon`
    * `Polyline`
    * `TileOverlay`
  * `List<Marker> GoogleMap.getMarkers()` and
    * `List<Circle> GoogleMap.getCircles()`
    * `List<GroundOverlay> GoogleMap.getGroundOverlays()`
    * etc.
  * `boolean Circle.contains(LatLng)`
  * `Marker GoogleMap.getMarkerShowingInfoWindow()`
  * `List<Marker> GoogleMap.getDisplayedMarkers()`
  * `float GoogleMap.getMinZoomLevelNotClustered(Marker)`
  * `Marker.animatePosition(LatLng target, AnimationSettings settings)`
  * `Marker.setClusterGroup(int)`

## Development ##

Focusing on:
  * keeping up with the latest release
  * performance
  * bugfixing (especially clustering engine)
    * please [post any issues](http://code.google.com/p/android-maps-extensions/issues/list) you notice
  * adding more APIs not available in the original library

## Migration from Android API v2 ##

When migrating to Extensions, all you have to change is:
  1. a couple of import statements,
  1. `SupportMapFragment` (or `MapView`) full class names in xml and
  1. call **`getExtendedMap`** instead of `getMap` on `SupportMapFragment` (or `MapView`).

Note for versions 2.x: also add google-play-services-lib (or keep it if you were already using it). Since 2.0 this library is decoupled from Google Play Services and you may use any version from 3.2.65 (the last working on Android API 8) or above.
Note for versions 1.x (deprecated): you will have to remove original google-play-services-lib from your workspace, as this library replaces it.

See [reference commit](http://code.google.com/p/android-maps-extensions/source/detail?r=76555070fb5a781a35f48567dd4c1aaa2aab1bc3) for how it was done in Google Play Services maps samples.

## Maven users ##

To build and run using maven:
  * `mvn install` (this also installs dependencies missing from the central repo)
  * `cd android-maps-extensions-demo`
  * `mvn android:deploy android:run`

Eclipse-maven-android integration seems to be buggy. You will have to delete libs folder after installing dependencies with `mvn install` and maybe do strange things like Maven->Update project or closing and reopening demos.

If you know how to work around these problems, please contact me. Here are issues that seem relevant:
  * [m2e-android #104](https://github.com/rgladwell/m2e-android/issues/104)
  * [m2e-android #121](https://github.com/rgladwell/m2e-android/issues/121)

## Attribution Requirements ##

While you don't need to reference this library inside your project in any way you may still need to add Google Play Services attribution text as described under [Attribution Requirements](https://developers.google.com/maps/documentation/android/intro#attribution_requirements).

## Versions ##

Check out [wiki on GitHub](https://github.com/mg6maciej/android-maps-extensions/wiki/Versions).

## Questions or problems using Extensions? ##

The best way to resolve any problems (that are not bugs or feature requests) is by asking a question on [StackOverflow](http://stackoverflow.com/) with a tag [android-maps-extensions](http://stackoverflow.com/questions/tagged/android-maps-extensions).

## Like Forking? ##

This project is also available on [GitHub](https://github.com/mg6maciej/android-maps-extensions) and [Bitbucket](https://bitbucket.org/mg6maciej/android-maps-extensions).
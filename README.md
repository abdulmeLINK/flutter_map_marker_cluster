# Flutter Map Marker Cluster

[![pub package](https://img.shields.io/pub/v/flutter_map_marker_cluster.svg)](https://pub.dartlang.org/packages/flutter_map_marker_cluster) ![travis](https://api.travis-ci.com/lpongetti/flutter_map_marker_cluster.svg?branch=master)

A Dart implementation of Leaflet.markercluster for Flutter apps.
This is a plugin for [flutter_map](https://github.com/johnpryan/flutter_map) package

<div style="text-align: center"><table><tr>
  <td style="text-align: center">
  <a href="https://github.com/lpongetti/flutter_map_marker_cluster/blob/master/example.gif">
    <img src="https://github.com/lpongetti/flutter_map_marker_cluster/blob/master/example.gif" width="200"/></a>
</td>
</tr></table></div>

## Usage

Add flutter_map and  flutter_map_marker_cluster to your pubspec:

```yaml
dependencies:
  flutter_map: any
  flutter_map_marker_cluster: any # or the latest version on Pub
```

Add `MarkerClusterLayerWidget` in your FlutterMap `children` paramater and configure it using `MarkerClusterLayerOptions`.

```dart
  Widget build(BuildContext context) {
    return FlutterMap(
      children: [
        TileLayerOptions(
          urlTemplate: 'https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png',
          subdomains: ['a', 'b', 'c'],
        ),
        MarkerClusterLayerWidget(
            options: MarkerClusterLayerOptions(
              spiderfyCircleRadius: 80,
              spiderfySpiralDistanceMultiplier: 2,
              circleSpiralSwitchover: 12,
              maxClusterRadius: 120,
              rotate: true,
              size: const Size(40, 40),
              anchor: AnchorPos.align(AnchorAlign.center),
              fitBoundsOptions: const FitBoundsOptions(
                padding: EdgeInsets.all(50),
                maxZoom: 15,
              ),
              markers: markers,
              polygonOptions: const PolygonOptions(
                  borderColor: Colors.blueAccent,
                  color: Colors.black12,
                  borderStrokeWidth: 3),
              popupOptions: PopupOptions(
                  popupState: PopupState(),
                  popupSnap: PopupSnap.markerTop,
                  popupController: _popupController,
                  popupBuilder: (_, marker) => Container(
                        width: 200,
                        height: 100,
                        color: Colors.white,
                        child: GestureDetector(
                          onTap: () => debugPrint('Popup tap!'),
                          child: Text(
                            'Container popup for marker at ${marker.point}',
                          ),
                    ),
         )),
      ],
    );
  }
```

### Run the example

See the `example/` folder for a working example app.

## Supporting Me

A donation through my Ko-Fi page would be infinitly appriciated:
[![ko-fi](https://ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/lorenzopongetti)

but, if you can't or won't, a star on GitHub and a like on pub.dev would also go a long way!

Every donation gives me fuel to continue my open-source projects and lets me know that I'm doing a good job.

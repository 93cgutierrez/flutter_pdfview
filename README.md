# flutter_pdfview

Native PDF View for iOS and Android

[![xscode](https://img.shields.io/badge/Available%20on-xs%3Acode-blue?style=?style=plastic&logo=appveyor&logo=data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAEAAAABACAMAAACdt4HsAAAAGXRFWHRTb2Z0d2FyZQBBZG9iZSBJbWFnZVJlYWR5ccllPAAAAAZQTFRF////////VXz1bAAAAAJ0Uk5T/wDltzBKAAAAlUlEQVR42uzXSwqAMAwE0Mn9L+3Ggtgkk35QwcnSJo9S+yGwM9DCooCbgn4YrJ4CIPUcQF7/XSBbx2TEz4sAZ2q1RAECBAiYBlCtvwN+KiYAlG7UDGj59MViT9hOwEqAhYCtAsUZvL6I6W8c2wcbd+LIWSCHSTeSAAECngN4xxIDSK9f4B9t377Wd7H5Nt7/Xz8eAgwAvesLRjYYPuUAAAAASUVORK5CYII=)](https://xscode.com/endigo/flutter_pdfview)
[![Latest compatibility result for Stable channel](https://img.shields.io/endpoint?url=https://pub.green/packages/flutter_pdfview/badge?channel=stable)](https://pub.green/packages/flutter_pdfview)
[![Latest compatibility result for Beta channel](https://img.shields.io/endpoint?url=https://pub.green/packages/flutter_pdfview/badge?channel=beta)](https://pub.green/packages/flutter_pdfview)
[![Latest compatibility result for Dev channel](https://img.shields.io/endpoint?url=https://pub.green/packages/flutter_pdfview/badge?channel=dev)](https://pub.green/packages/flutter_pdfview)

# Use this package as a library

## 1. Depend on it

Add this to your package's pubspec.yaml file:

```
dependencies:
  # 1.3.3
  flutter_pdfview: 
    git:
      url: https://github.com/93cgutierrez/flutter_pdfview.git
      ref: v1.3.3
```

### 2. Install it

You can install packages from the command line:

with Flutter:

```
$ flutter packages get
```

Alternatively, your editor might support pub get or `flutter packages get`. Check the docs for your editor to learn more.

### 3. Import it

Now in your Dart code, you can use:

```
import 'package:flutter_pdfview/flutter_pdfview.dart';
```

## Options

| Name                           | Android | iOS |      Default      |
|:-------------------------------| :-----: | :-: |:-----------------:|
| defaultPage                    |   ✅    | ✅  |        `0`        |
| onViewCreated                  |   ✅    | ✅  |      `null`       |
| onRender                       |   ✅    | ✅  |      `null`       |
| onPageChanged                  |   ✅    | ✅  |      `null`       |
| onError                        |   ✅    | ✅  |      `null`       |
| onPageError                    |   ✅    | ❌  |      `null`       |
| onLinkHandle                   |   ✅    | ✅  |      `null`       |
| onTap                          |   ✅    | ❌  |      `null`       |
| onDoubleTap                    |   ✅    | ❌  |      `null`       |
| onPinchZoom                    |   ✅    | ❌  |      `null`       |
| onScrollAnimation              |   ✅    | ❌  |      `null`       |
| gestureRecognizers             |   ✅    | ✅  |      `null`       |
| filePath                       |   ✅    | ✅  |                   |
| pdfData                        |   ✅    | ✅  |                   |
| fitPolicy                      |   ✅    | ❌  | `FitPolicy.WIDTH` |
| enableSwipe                    |   ✅    | ✅  |      `true`       |
| swipeHorizontal                |   ✅    | ✅  |      `false`      |
| password                       |   ✅    | ✅  |      `null`       |
| nightMode                      |   ✅    | ❌  |      `false`      |
| password                       |   ✅    | ✅  |      `null`       |
| autoSpacing                    |   ✅    | ✅  |      `true`       |
| pageFling                      |   ✅    | ✅  |      `true`       |
| pageSnap                       |   ✅    | ❌  |      `true`       |
| preventLinkNavigation          |   ✅    | ✅  |      `false`      |
| enableDoubleTap                |   ✅    | ❌  |      `false`      |
| enableAntialiasing             |   ✅    | ❌  |      `false`      |
| enableAnnotationRendering      |   ✅    | ❌  |      `false`      |

## Controller Options

| Name           |     Description      | Parameters |     Return     |
| :------------- | :------------------: | :--------: | :------------: |
| getPageCount   | Get total page count |     -      | `Future<int>`  |
| getCurrentPage |   Get current page   |     -      | `Future<int>`  |
| setPage        |    Go to/Set page    | `int page` | `Future<bool>` |

and more ...

## Example

```dart
PDFView(
  filePath: path,
  enableSwipe: true,
  swipeHorizontal: true,
  autoSpacing: false,
  pageFling: false,
  pageSnap: true,
  defaultPage: currentPage!,
  fitPolicy: FitPolicy.WIDTH,
  fitEachPage: false,
  preventLinkNavigation: true,
  // if set to true the link is handled in flutter
  enableDoubleTap: true,
  enableAntialiasing: true,
  enableAnnotationRendering: true,
  onRender: (_pages) {
    setState(() {
      pages = _pages;
      isReady = true;
    });
  },
  onError: (error) {
    print(error.toString());
  },
  onPageError: (page, error) {
    print('$page: ${error.toString()}');
  },
  onViewCreated: (PDFViewController pdfViewController) {
    _controller.complete(pdfViewController);
  },
  onPageChanged: (int page, int total) {
    print('page change: $page/$total');
  },
  onTap: (String? motionEvent) {
    print('onTap: $motionEvent');
  },
  onDoubleTap: (String? animation, double oldZoom, double newZoom) {
    print('onDoubleTap: animation: $animation, oldZoom: $oldZoom, newZoom: $newZoom');
  },
  onPinchZoom: (String? animation, double oldZoom, double newZoom) {
    print('onPinchZoom: animation: $animation, oldZoom: $oldZoom, newZoom: $newZoom');
  },
  onScrollAnimation: (String? animation, int scrollMoveDirection) {
    print('onScrollAnimation: animation: $animation scrollMoveDirection: $scrollMoveDirection');
  },
),
```

# Dependencies

### Android

[AndroidPdfViewer](https://github.com/barteksc/AndroidPdfViewer)

### iOS (only support> 11.0)

[PDFKit](https://developer.apple.com/documentation/pdfkit)

# Future plans

### Developer

- [93cgutierrez](https://github.com/93cgutierrez)

### Based on the original:

- [endigo](https://github.com/endigo)

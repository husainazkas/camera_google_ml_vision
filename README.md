# camera_google_ml_vision

A Flutter package for iOS and Android to show a preview of the camera and detect things with Google ML Vision.

This version is a forked from [camera_google_ml_vision](https://pub.dev/packages/camera_google_ml_vision)

### Installation
First, add camera_google_ml_vision as a dependency.

```yaml
dependencies:
  flutter:
    sdk: flutter
  camera_google_ml_vision:
    git:
      url: git://github.com/husainazkas/camera_google_ml_vision.git
```
or

```yaml
dependencies:
  flutter:
    sdk: flutter
  camera_google_ml_vision:
    git: https://github.com/husainazkas/camera_google_ml_vision.git
```

Android
Change the minimum Android sdk version to 21 (or higher) in your android/app/build.gradle file.

minSdkVersion 21
ps: This is due to the dependency on the camera plugin.

### Usage
Example with Barcode:
```dart
CameraMlVision<List<Barcode>>(
  detector: GoogleVision.instance.barcodeDetector().detectInImage,
  onResult: (List<Barcode> barcodes) {
    if (!mounted || resultSent) {
      return;
    }
    resultSent = true;
    Navigator.of(context).pop<Barcode>(barcodes.first.toString());
  },
)
```
CameraMlVision is a widget that shows the preview of the camera. It takes a detector as a parameter here we pass the detectInImage method of the BarcodeDetector object. The detector parameter can take all the different CameraMlVision Detector. Here is a list :
```dart
CameraMlVision.instance.barcodeDetector().detectInImage
CameraMlVision.instance.cloudLabelDetector().detectInImage
CameraMlVision.instance.faceDetector().processImage
CameraMlVision.instance.labelDetector().detectInImage
CameraMlVision.instance.textRecognizer().processImage
```
Then when something is detected the onResult callback is called with the data in the parameter of the function.

Exposed functionality from CameraController
We expose some functionality from the CameraController class here a list of these :
```dart
value
prepareForVideoRecording
startVideoRecording
stopVideoRecording
takePicture
Getting Started
See the example directory for a complete sample app.
```
Features and bugs
Please file feature requests and bugs at the issue tracker.

Technical Support
For any technical support, don't hesitate to contact us. Find more information in our website

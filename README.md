RxMKMapView
===

RxMKMapView is a [RxSwift](https://github.com/ReactiveX/RxSwift) wrapper for MKMapView (MapKit) `delegate` providing a Reactive Delegate Proxy as well as a bindable annotations interface to dynamically change the "data source" of your map.


## Installation

### [CocoaPods](https://guides.cocoapods.org/using/using-cocoapods.html)

RxMKMapView is available through [CocoaPods](http://cocoapods.org). To install
it, simply add the following line to your Podfile:

```ruby
pod "RxMKMapView"
```

### [Carthage](https://github.com/Carthage/Carthage)

Add this to `Cartfile`

```
github "RxSwiftCommunity/RxMKMapView"
```

## Example Usages

```swift
// MARK: Setup MKMapView

let mapView = MKMapView(frame: view.frame)
view.addSubview(mapView)

// MARK: Bind Annotations

requestForAnnotations() // Observable<[MyMapAnnotation]>
    .asDriver(onErrorJustReturn: [])
    .drive(mapView.rx.annotations)
    .disposed(by: disposeBag)

// MARK: Respond to Loading Events

mapView.rx.willStartLoadingMap
       .asDriver()
       .drive(onNext: {
           print("map started loadedloading")
       })
       .disposed(by: disposeBag)

mapView.rx.didFinishLoadingMap
       .asDriver()
       .drive(onNext: {
           print("map finished loading")
       })
       .disposed(by: disposeBag)
```

## Requirements

RxMKMapView requires Swift (5.0 and RxSwift (5.0).

## License

RxMKMapView is available under the MIT license. See the LICENSE file for more info.


# PostalCodeValidator

[![Build Status][ci status badge]][ci status]
[![License][license badge]][license]
[![Swift Version][swift version badge]][swift version]

A validator for [postal codes](https://en.wikipedia.org/wiki/Postal_code)
with support for 200+ regions.

```swift
import Foundation
import PostalCodeValidator

let locale = Locale.current // American English (en-US)
if let validator = PostalCodeValidator(locale: locale) {
    validator.validate(postalCode: "95014")) // true
    validator.validate(postalCode: "22162-1010") // true

    validator.validate(postalCode: "1234567")) // false
    validator.validate(postalCode: "INVALID")) // false
}

// 248 regions supported
let 🇯🇵 = Locale(identifier: "ja-JP")
if let validator = PostalCodeValidator(locale: 🇯🇵) {
    validator.validate(postalCode: "154-0023")) // true
    validator.validate(postalCode: "12345") // false
}
```

> **Note**: Only the region of a locale is used to determine validation rules.
> To validate the postal code for a particular region,
> you can construct a locale using an identifier with the `"und"` language code.

The CLDR previously maintained a list of postal code formats,
but that information was
[deprecated in v27](http://unicode.org/reports/tr35/tr35-info.html#Postal_Code_Validation).
Following the guidance of the
[twitter-cldr-rb](https://github.com/twitter/twitter-cldr-rb/issues/166) project,
`PostalCodeValidator` sources its information from http://i18napis.appspot.com.

The most recent release of this software uses
information retrieved from the website on November 27, 2019.

## Requirements

- Swift 4.0+

## Installation

### Swift Package Manager

Add the PostalCodeValidator package to your target dependencies in `Package.swift`:

```swift
import PackageDescription

let package = Package(
  name: "YourProject",
  dependencies: [
    .package(
        url: "https://github.com/FormatterKit/PostalCodeValidator",
        from: "0.0.1"
    ),
  ]
)
```

Then run the `swift build` command to build your project.

## License

MIT

## Contact

Mattt ([@mattt](https://twitter.com/mattt))

[ci status]: https://github.com/FormatterKit/PostalCodeValidator/actions
[ci status badge]: https://github.com/FormatterKit/PostalCodeValidator/workflows/CI/badge.svg
[license]: http://img.shields.io/badge/license-MIT-blue.svg?style=flat
[license badge]: http://img.shields.io/badge/license-MIT-blue.svg?style=flat
[swift version]: https://swift.org/download/
[swift version badge]: http://img.shields.io/badge/swift%20version-4.0+-orange.svg?style=flat

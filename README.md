vCardSerialization
====================

`vCardSerialization` encodes and decodes between [vCard](http://en.wikipedia.org/wiki/VCard) and [AddressBook](https://developer.apple.com/library/ios/documentation/AddressBook/Reference/AddressBook_iPhoneOS_Framework/_index.html) records, following the API conventions of Foundation's `NSJSONSerialization` class.

## Usage

### Decoding

```objective-c
@import AddressBookUI;

#import "vCardSerialization.h"

NSURL *URL = [[NSBundle mainBundle] URLForResource:@"contact" withExtension:@"vcf"];
NSData *data = [NSData dataWithContentsOfURL:URL];

ABPersonViewController *viewController = [[ABPersonViewController alloc] init];
viewController.displayedPerson = (__bridge ABRecordRef)[[vCardSerialization addressBookRecordsWithVCardData:data error:nil] firstObject];
ABPeoplePickerNavigationController *navigationController = [[ABPeoplePickerNavigationController alloc] initWithRootViewController:viewController];
[self.navigationController presentViewController:navigationController animated:YES completion:nil];
```

### Encoding

```objective-c
NSArray *records = ...;
NSDate *data = [vCardSerialization vCardDataWithAddressBookRecords:records error:nil];
```

---

## Contact

Mattt Thompson

- http://github.com/mattt
- http://twitter.com/mattt
- m@mattt.me

## License

vCardSerialization is available under the MIT license. See the LICENSE file for more info.

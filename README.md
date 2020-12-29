# Intl Phone Number Input

A simple and customizable flutter package for international phone number input

| CustomDecoration | CustomBorder | Default |
|----------|-------------|--------|
| <img src="https://user-images.githubusercontent.com/27495055/80114512-9544b100-857b-11ea-9292-9c9c3eaf93e0.png" width="240" height="430" alt="Screenshot_1587652933"/> | <img src="https://user-images.githubusercontent.com/27495055/80115521-beb20c80-857c-11ea-9902-41c444a3bd33.png" width="240" height="430" alt="Screenshot_1587652933"/> | <img src="https://user-images.githubusercontent.com/27495055/80116034-63344e80-857d-11ea-9922-1062b4320503.png" width="240" height="430" alt="Screenshot_1587652933"/> |

### What's new
  - Added support for Flutter Web :fire: :fire: :fire: :rocket: :rocket: :rocket: .
  - Added textAlign, textAlignVertical.
  - Fixed French translation of Egypt.
  - Added option to make selector button a prefix icon in `SelectorConfig`.
  - Added `cursorColor` option.
  - Added `scrollPadding` option.
  - Added new language translations for Serbia, with two scripts.
  - Updated onSaved into `ValueChange<PhoneNumber>`. now onSaved returns a `PhoneNumber` object.
  - Added `keyboardType` option and improvements on iOS keyboard, see [#147](https://github.com/natintosh/intl_phone_number_input/pull/147), [#148](https://github.com/natintosh/intl_phone_number_input/pull/148) for more details.
  - Added locale zh-TW.
  - Added support of nb and nn locale.
  - Fixed issue with AsYouType formatter injecting country dial code on every input for phone numbers with North American Numbering Plan.
  - Fixed issue with Selector Button onTap when enable is false.
  - <b>Breaking Change</b> for v0.7.0, `SelectorConfig.backgroundColor` would be removed and replaced with `Theme.of(context).canvasColor`.
  - Added `spaceBetweenSelectorAndTextField` for padding between selector button and text field.
  - Fixed Bug with cursor position on typing, see [#130](https://github.com/natintosh/intl_phone_number_input/issues/130) for illustration and more information.
  - Fixed Bug with selector button country restoring to initialValue after updating/changing value, see [#155](https://github.com/natintosh/intl_phone_number_input/issues/155) for more information.
  - Tap outside `selectorType` `PhoneInputSelectorType.BOTTOM_SHEET` now dismisses the dialog.

### Features
  - Web support.
  - Support for RTL languages
  - Selector mode dropdown, bottom sheet and dialog
  - As You Type Formatter: formats inputs to its selected international format
  - Get Region Info with PhoneNumber.getRegionInfoFromPhoneNumber(String phoneNumber, [String isoCode]);
  - Format PhoneNumber with PhoneNumber.getParsableNumber(String phoneNumber, String isoCode) or `PhoneNumber Reference`.parseNumber()
  - Custom list of countries e.g. ['NG', 'GH', 'BJ' 'TG', 'CI']
    
```dart
    String phoneNumber =  '+234 500 500 5005';
    PhoneNumber number = await PhoneNumber.getRegionInfoFromPhoneNumber(phoneNumber);
    String parsableNumber = number.parseNumber();
    `controller reference`.text = parsableNumber
```    

### Web Support

In your app directory, edit `web/index.html` to add the following

```html

<!DOCTYPE html>
<html>
    <head>
        ...
    </head>
    <body>
    
        ...

        <script src="packages/libphonenumber_plugin/js/libphonenumber.js"></script>
        <script src="packages/libphonenumber_plugin/js/stringbuffer.js"></script>

        ...

        <script src="main.dart.js" type="application/javascript"></script>
    </body>
</html>
```

Or checkout `/example` folder from [Github](https://github.com/natintosh/intl_phone_number_input/tree/develop/example).


### Note
``` dart
    PhoneNumber.getRegionInfoFromPhoneNumber(String phoneNumber, [String isoCode])
```
> Could throw an Exception if the phoneNumber isn't recognised its a good pattern to pass the country's isoCode or have '+' at the beginning of the string

> isoCode could be null if PhoneNumber is not recognised

# Usage

### Constructors

| s/n | Constructor                                             |
| --- | ------------------------------------------------------- |
|  1  | InternationalPhoneNumberInput                           |

## Available Parameters

```dart
InternationalPhoneNumberInput({
    Key key,
      this.selectorConfig = const SelectorConfig(),
      @required this.onInputChanged,
      this.onInputValidated,
      this.onSubmit,
      this.onFieldSubmitted,
      this.validator,
      this.onSaved,
      this.textFieldController,
      this.keyboardAction,
      this.keyboardType = TextInputType.phone,
      this.initialValue,
      this.hintText = 'Phone number',
      this.errorMessage = 'Invalid phone number',
      this.selectorButtonOnErrorPadding = 24,
      this.spaceBetweenSelectorAndTextField = 12,
      this.maxLength = 15,
      this.isEnabled = true,
      this.formatInput = true,
      this.autoFocus = false,
      this.autoFocusSearch = false,
      this.autoValidateMode = AutovalidateMode.disabled,
      this.ignoreBlank = false,
      this.countrySelectorScrollControlled = true,
      this.locale,
      this.textStyle,
      this.selectorTextStyle,
      this.inputBorder,
      this.inputDecoration,
      this.searchBoxDecoration,
      this.textAlign = TextAlign.start,
      this.textAlignVertical = TextAlignVertical.center,
      this.scrollPadding = const EdgeInsets.all(20.0),
      this.focusNode,
      this.cursorColor,
      this.autofillHints,
      this.countries
    });
```|

```dart
SelectorConfig({
    this.selectorType = PhoneInputSelectorType.DROPDOWN,
    this.showFlags = true,
    this.useEmoji = false,
    this.backgroundColor,
    this.countryComparator,
    this.setSelectorButtonAsPrefixIcon = false,
});
```

| Parameter                           | Datatype               |    Initial Value          |
|---------------------------------    |------------------------|---------------------------|
| onInputChanged                      | function(PhoneNumber)  |        null               |
| onSaved                             | function(PhoneNumber)  |        null               |
| onInputValidated                    | function(bool)         |        null               |
| focusNode                           | FocusNode              |        null               |
| textFieldController                 | TextEditingController  |   TextEditingController() |
| onSubmit                            | Function()             |        null               |
| keyboardAction                      | TextInputAction        |        null               |
| keyboardType                        | TextInputType          |   TextInputType.phone     |
| countries                           | List<string>           |        null               |
| textStyle                           | TextStyle              |        null               |
| selectorTextStyle                   | TextStyle              |        null               |
| inputBorder                         | InputBorder            |        null               |
| inputDecoration                     | InputDecoration        |        null               |
| initialValue                        | PhoneNumber            |        null               |
| hintText                            | String                 |     Phone Number          |
| selectorButtonOnErrorPadding        | double                 |        24                 |
| spaceBetweenSelectorAndTextField    | double                 |        12                 |
| maxLength                           | integer                |        15                 |
| isEnabled                           | boolean                |        true               |
| autoFocus                           | boolean                |        false              |
| autoValidateMode                    | AutoValidateMode       | AutoValidateMode.disabled |
| formatInput                         | boolean                |        true               |
| errorMessage                        | String                 | Invalid phone number      |
| selectorConfig                      | SelectorConfig         | SelectorConfig()          |
| ignoreBlank                         | boolean                |       false               |
| locale                              | String                 |       null                |
| searchBoxDecoration                 | InputDecoration        |        null               |
| textAlign                           | TextAlign              |   TextAlign.start         |
| textAlignVertical                   | TextAlignVertical      | TextAlignVertical.center  |
| scrollPadding                       | EdgeInsets             | EdgeInsets.all(20.0)      |
| countrySelectorScrollControlled     | boolean                |        true               |
| cursorColor                         | String                 |       null                |
| autofillHints                       | Iterable<String>       |       null                |

### Selector Types
| DROPDOWN | BOTTOMSHEET | DIALOG |
|----------|-------------|--------|
| <img src="https://user-images.githubusercontent.com/27495055/80116593-10a76200-857e-11ea-9600-f2cfef5b2965.png" height="430" alt="Screenshot_1587652933"/>         | <img src="https://user-images.githubusercontent.com/27495055/80116677-261c8c00-857e-11ea-8167-a3de563287f4.png" width="240" height="430" alt="Screenshot_1587652933"/>            | <img src="https://user-images.githubusercontent.com/27495055/80116721-3896c580-857e-11ea-84da-4efe13011d50.png" width="240" height="430" alt="Screenshot_1587652933"/>   |

### Testing
Widget Key parameters and Helper classes are now available for integration testing check out this example 🎯 [Integration Testing Example](https://gist.github.com/natintosh/b7b40d75240a65fdb63942a4b36753e5)


# Contributions
If you encounter any problem or the library is missing a feature feel free to open an issue. Feel free to fork, improve the package and make pull request.

# Contributors 
<a href="https://github.com/natintosh/intl_phone_number_input/graphs/contributors">
  <img src="https://contributors-img.web.app/image?repo=natintosh/intl_phone_number_input" />
</a>

Made with [contributors-img](https://contributors-img.web.app).

# Dependencies

* [libphonenumber](https://pub.dev/packages/libphonenumber)
* [equatable](https://pub.dev/packages/equatable)

# Credits

A special thanks to [niinyarko](https://github.com/niinyarko/flutter-international-phone-input)

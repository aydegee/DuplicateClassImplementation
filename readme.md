Demonstrates an issue when using CocoaPods to integrate a library with the the unit test target when one of its dependencies is already included by the application. 

In this case, Xcode shows the following in the debug console while running the unit tests e.g.

> Class `AFQueryStringPair` is implemented in both `/Users/andrew/Library/Developer/CoreSimulator/Devices/7BBE0E8C-6CD1-4BFC-88CA-60BC2523DE75/data/Containers/Bundle/Application/4A81F309-461E-4A31-8C60-64FBF8C6EA03/DuplicateClassImplementation.app/DuplicateClassImplementation` and `/Users/andrew/Development/example/DuplicateClassImplementation/Build/Products/Debug-iphonesimulator/DuplicateClassImplementationTests.xctest/DuplicateClassImplementationTests`. One of the two will be used. Which one is undefined

The above output is repeated for each duplicated class implementation.


Steps to reproduce:

- Clone the sample project
- Run pod install
- Open the workspace in Xcode
- Run the unit tests

This only happens when running the tests in the iOS9.1 simulator. Using the 8.4 simulator does not exhibit this problem.

It is reproducible with CocoaPods 0.37.2 and CocoaPods 0.39.0. Other versions have not been tested.

<img src="https://swift.org/assets/images/swift.svg" alt="swift" width=20% height=20%>

![](https://devimages.apple.com.edgekey.net/swift/images/xcode.png)

> `Swift` 是由 `Apple` 創造，強大且直覺易用的全新程式語言，用於打造 `iOS` 與 `Mac` 的`app`。
> `蘋果`強調`Swift`具備「簡單、互動、現代、快速、安全」等特性，可輕鬆開發出安全而快速的軟體。對學生而言，學習Swift是其接觸現代化開發概念及最佳典範的入門，其技能將能應用於行動裝置、桌面、雲端等多種環境上，開源釋出後，更有利其廣泛使用。
> 藉由與`Objective-C`的相容，`Swift`旨在取代`Objective-C`與`Python`等程式語言。

`遞增` (`++`)
`遞減` (`--`)


```console
shell> sudo apt-get install clang libicu-dev
shell> wget -q -O - https://swift.org/keys/all-keys.asc | gpg --import -
shell> gpg --keyserver hkp://pool.sks-keyservers.net --refresh-keys Swift
shell> gpg --verify swift-<VERSION>-<PLATFORM>.tar.gz.sig
shell> tar xzf swift-<VERSION>-<PLATFORM>.tar.gz
shell> export PATH=/path/to/usr/bin:"${PATH}"

```

```console
shell> swift
Welcome to Swift version 2.2.1 (swift-2.2.1-RELEASE). Type :help for assistance.
  1>  
```

```console
shell> swift -version
Swift version 2.2.1 (swift-2.2.1-RELEASE)
Target: x86_64-unknown-linux-gnu
```

```
https://swift.org/builds/swift-2.2.1-release/ubuntu1404/swift-2.2.1-RELEASE/swift-2.2.1-RELEASE-ubuntu14.04.tar.gz
https://swift.org/builds/swift-2.2.1-release/ubuntu1510/swift-2.2.1-RELEASE/swift-2.2.1-RELEASE-ubuntu15.10.tar.gz
```

```
https://swift.org/builds/development/ubuntu1404/swift-DEVELOPMENT-SNAPSHOT-2016-06-20-a/swift-DEVELOPMENT-SNAPSHOT-2016-06-20-a-ubuntu14.04.tar.gz
https://swift.org/builds/development/ubuntu1510/swift-DEVELOPMENT-SNAPSHOT-2016-06-20-a/swift-DEVELOPMENT-SNAPSHOT-2016-06-20-a-ubuntu15.10.tar.gz
```

```swift
print("Hello, world!")
1 + 2

let greeting = "Hello!"
print(greeting)

let numbers = [1,2,3]
for n in numbers.reverse() {
  print(n)
}

import Glibc
random() % 10
```

```console
shell> swift build --help
```
```console
shell> mkdir Hello
shell> cd Hello
shell> touch Package.swift
shell> mkdir Sources
shell> main.swift

shell> swift build

shell> .build/debug/Hello
Hello, world!
```

Greeter.swift
```swift
func sayHello(personName: String) -> String {
    let greeting = "Hello, " + personName + "!"
    return greeting
}
```

main.swift
```swift
print(sayHello(personName: "Anna"))
// Prints "Hello, Anna!"

print(sayHello(personName: "Brian"))
// Prints "Hello, Brian!"
```

Greeter.swift
```swift
func sayHello(personName: String) {
    print("Hello, \(name)!")
}
```

main.swift
```swift
if Process.arguments.count != 2 {
    print("Usage: hello NAME")
} else {
    let name = Process.arguments[1]
    sayHello(personName: name)
}
```

- [Swift_Programming_Language](https://developer.apple.com/library/ios/documentation/Swift/Conceptual/Swift_Programming_Language/index.html)
- [Functions](https://developer.apple.com/library/ios/documentation/Swift/Conceptual/Swift_Programming_Language/Functions.html)

---

```swift
//  Created by Timmy on 2015/2/24.
//  Copyright (c) 2015年 Timmy. All rights reserved.

import Foundation

println("Hello, World!")

var myVariable = 42
myVariable = 50
let myConstant = 42

let label = "The width is "
let width = 94
let widthLabel = label + String(width)

let apples = 3
let oranges = 5
let appleSummary = "I have \(apples) apples."
let fruitSummary = "I have \(apples + oranges) pieces of fruit."

var shoppingList = ["catfish", "water", "tulips", "blue paint"]
shoppingList[1] = "bottle of water"
 
var occupations = [
    "Malcolm": "Captain",
    "Kaylee": "Mechanic",
]
occupations["Jayne"] = "Public Relations"

let emptyArray = [String]()
let emptyDictionary = [String: Float]()

let individualScores = [75, 43, 103, 87, 12]
var teamScore = 0
for score in individualScores {
    if score > 50 {
        teamScore += 3
    } else {
        teamScore += 1
    }
}
println(teamScore)

```

---

### :books: 參考網站：
- [swift](https://swift.org/) 
- [https://developer.apple.com/swift/](https://developer.apple.com/swift/)
- [https://www.apple.com/tw/swift/](https://www.apple.com/tw/swift/)
- [用Apple全新App開發語言Swift，4小時做出Flappy Bird遊戲](http://www.ithome.com.tw/news/88381)
- [Swift (程式語言)](http://zh.wikipedia.org/wiki/Swift_(%E7%A8%8B%E5%BC%8F%E8%AA%9E%E8%A8%80))
- [About Swift](https://developer.apple.com/library/ios/documentation/Swift/Conceptual/Swift_Programming_Language/index.html)
- [https://developer.apple.com/library/ios/documentation/Swift/Conceptual/BuildingCocoaApps/InteractingWithObjective-CAPIs.html#//apple_ref/doc/uid/TP40014216-CH4-XID_25](https://developer.apple.com/library/ios/documentation/Swift/Conceptual/BuildingCocoaApps/InteractingWithObjective-CAPIs.html#//apple_ref/doc/uid/TP40014216-CH4-XID_25)
- [Printing](https://developer.apple.com/library/ios/documentation/General/Reference/SwiftStandardLibraryReference/Printing.html)
- [String](https://developer.apple.com/library/ios/documentation/General/Reference/SwiftStandardLibraryReference/index.html#//apple_ref/doc/uid/TP40014608-CH7-SW1)
- [Array](https://developer.apple.com/library/ios/documentation/General/Reference/SwiftStandardLibraryReference/Array.html#//apple_ref/doc/uid/TP40014608-CH5-SW1)
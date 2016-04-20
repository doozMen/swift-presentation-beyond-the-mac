slidenumbers: true
# Swift Night
20 April 2016

---
- Swift Language __@stijn (30 min)__
- Using Playground's with Scripting __@Jelle (30 min)__
- Swift and Open Source __@Hans (15 min)__
- Swift and Backend Development __@Dylan @Hannes (20 min)__

---
# [fit] Bullshit you cannot draw
![original fit](Draw_owl.png)


A look at the _swift language_ from a __drawing__ perspective

^ de Owl problem verteld dat je talen kan uitleggen zonder de nuances.
^ zonder nuances kan je een uil tekenen, maar ziet hij er dan uit als een uil?

^ Meestal als je vraagt om een probleem te tekenen in een blok schema merk je voor jezelf, of voor een ander dat je het nog niet zo goed begrijpt.
^ vandaar ook de header :)

---

 Based on _[a presentation](https://vimeo.com/album/3132071/video/111942502)_ of __@srbaker__ @NSConference 2014

^ Pragmatisch omgaan met Paradigmas
^ Een taal purist ben ik niet maar het is wel fijn om te weten waar je over praat. Als iemand anders dat goed doet, tja dan moet ik het wiel niet heruitvinden:)

---

![original 200%](TypedVSFreeArray.png)

^ Hoe een taal gebouwd -> Objective-C eerste taal grondig

^ Evident een array met verschillende Type's

^ Prototypes -> Producten

^ Dynamische bedacht om snel te veranderen

^ Deze presentatie

^ 4 tekening -> potentieel van Swift

^ Zo probeer ik het toch te bevatten :)

---

![fit](Draw_procedural.png)
![fit](Draw_OO_message.png)
![fit](Draw_functional.png)
![fit](Draw_typeToByte.png)

^ Tekeningen ->
^ Procedural
^ Object Oriented - OO
^ Functional

---

![fit](Path.jpg)

Procedural / Object Oriented - __OO__ / Functional

- Type sytems



^ Uiteindelijke moeten ze allemaal met types omgaan.
^ Welk pad je ook kiest!

---

> As goes with paths, they thend to mix. But they where __never intended__ to do so...
-- @srbaker

---

![](GlowingLed.png)

# Grow the system

^ Elk programma moet uitgebried worden. Elk path dat we bespraken heeft zijn tactiek om dat te doen.

^Taal als enige bouwsteen.

^ Want hoe moelijk we er ook over doen een taal stuurt meestal een ledje aan.

---

_Bind `Code` to `hardware` => Type_

What is Type?

^ Wat doen als het veel ledjes worden.

---

![fit](Draw_typeToByte.png)

^In het begin, C, -> Anything that has the same length is a type
^ Ledjes moeten letters kunnen weergeven
^ Heeldere objecten opslaan ...

---

More later ...

Lets __juggle__ some types around...

---

![fit](Steps.png)

---


## Procedural

> Data __(Type)__ moves and Changes

---

![fit](Draw_procedural.png)

^Dit zit er wat uit als een flow diagram en dat is het eigenlijk ook.

---

# Grow?

![fit](Draw_procedural.png)

---

![fit](Draw_procedural_grow.png)

^ De flow kan veranderen
^ De data kan veranderen

---
Many _OO_ programming is actually __procedural__
-- @srbaker

---
# Examples of pure procedural

C / Go / Fortran / Pascal

^Objective-C is gebouw in C
^ Trots dat Swift gebouwd is zonder de C

---
# OO

---

![fit](Draw_OO_whatIsIt.png)

---

![fit](Draw_OO_whatIsIt.png)

Messaging

---

![fit](Draw_OO_pill.png)

> __OO__ Makes code understandable by __incapsulating__ the moving parts.
-- Micheal Feathers

---

![fit](Draw_OO_message.png)

---

![fit](Draw_OO_pill.png)

Smalltalk /  Ruby

^ Pure OO talen

---

Objective-C / Python

^ OO but

---
## Messaging?

^Maar we gingen het hebben over hoe we zo een syteem konden doen groeien

^ OO systemen zijn per definitie dynamisch.
^ Alan Key -> OO is bedoeld om dynamisch te zijn.
^ Beslis pas als het moet...

---

![fit](Draw_message_queue.png)

^messaging tussen request en ontvanger zit een queue.

^Deze queue maakt dat OO talen snel kunnen veranderen
^ Ruby doet dit omdat ze continu willen kunnen updaten zonder dat server down gaat.
^ Objective-C -> Steve Jobs rekenmachine met andere kleuren die at run time ingesteld kunnen worden.

---

## Grow?

![left fit](Draw_message_queue.png)

---
![fit](Draw_message_queue_replaceObject.png)

^Het doel van messaging is los gekoppelde Objecten te hebben.
^At runtime kunnen deze veranderen en de queue spaart de berichten op tot de verandering klaar is.

---
# So What?

```swift
class Foo {
  let webService = Service ()

  func do (completion: ()->()) {
    webService.do {
      //code async
      completion()
    }
  }
}

// write unit test

class FooTests {
  func testFoo () {
    let foo = Foo()
    foo.do {
      Assert ...
      //This will be async
    }
  }
}
```

^Er is at run time geen mogelelijkheid om do synchroon te maken in swift
^ Als je message queue hebt dan kan dat wel ...

---
# Functional

---

![fit](Draw_functional.png)

^ Geen is no encapsulation.
^ Data kan en mag niet veranderen.
^ Het is heel rechtlijnig en eenvoudig.
^ Het concept toch

---
# ?
![fit](Draw_functional.png)
![fit](Draw_owl.png)

^ voor mij functioneel toch vooral een misterie in gebruik

---

![fit](Draw_functional_seperate_pills.png)
> __FP__ Makes code understandable by __minimizing__ the moving parts.
-- Micheal Feathers

---

![fit](Draw_OO_pill.png)
![fit](Draw_functional_seperate_pills.png)

> OO -> incapsulating
> FP -> minimizing

__Moving parts__

-- Micheal Feathers

---
## Grow ?
![fit](Draw_functional_seperate_pills.png)

^ Lineair groeien
^ We kunnen de pillen niet open doen, een methode toevoegen
^ Code hergebruiken is hier minder eenduidig voor mij

---

![fit](Draw_functional_grow.png)


^ Ziet er op zich eenvoudig uit

---
![fit](Draw_functional_seperate_pills.png)

## [Fit] IMMUTABLE

~~side effects~~

^ Belang uitleggen vanuit een animerende view.

---

# Recap
![left fit](Draw_procedural.png)
![left fit](Draw_OO_message.png)
![left fit](Draw_functional.png)

^Alles klinkt nu waarschijnlijk gelijk
^ wat doet het er toe dit te weten.
^ Hoe verandert het mijn code
^ Misschien wat heeft het te maken met Swift?

---

![fit](Draw_procedural.png)
![fit](Draw_OO_message.png)
![fit](Draw_functional.png)

^Hier ontbreekt wel een deel
^ Type system
^ Swift gebruikt de patronen waar en wanner dit zinvol is.

---
# [fit] Type system

![fit](Draw_procedural.png)
![fit](Draw_OO_message.png)
![fit](Draw_functional.png)

---

![fit](Draw_typeToByte.png)

^ Goal
^ Code reuse
^ Safety
^ Possible speed improvements

^ Swift is strongly typed en static
^ even uitleggen wat dat betekend

---

```
            Java                                  Ruby
            C                                     Smalltalk
static ------------------------------------------------------ Dynamic
```

^ Discussie kan je niet ontwijken
^ Maar hopelijk gaat ze verder dan dat
^ Unit test voorbeeld verwijzen naar static typing

---
## Checking

```
            compile time                            Run time
static ------------------------------------------------------ Dynamic
```
^ static -> Type checking done at compile time
^ Dynamic -> type checking done at run time
^ Type safe betekend eigenlijk memory safe.

### Static
```swift
var i = 1
i = "One" // Error
```

---
### Dynamic

Class instantiation can be __data driven__

```objectivec


NSString *className = [self getClassNameFromJSON];


//This can only be checked at run time. The JSON file might change.
A* a = [[NSClassFromString(className) alloc] init];
```

---

## Type inference

```swift

 var s = "A string"
 var s2:String
 s2 = "Another string"


```

[More info](http://books.aidanf.net/learn-swift/types_and_type_inference)

^Je krijgt static typing for free
^Enkel in de functie namen moet je een Type melden. De rest wordt afgeleid. Je krijgt static typing dus ongeveer vanzelf.

---

![fit](weakVSStrong.png)

^ Strong betekend gewoon dat je type altijd gecheckt wordt.
^ Een taal die Strong is wil soms ook static worden -> Duby

---

# Messaging in swift


Not yet, or might __never__ be ...

[More info](http://www.buckleyisms.com/home/2014/6/16/the-case-for-message-passing-in-swift.html)

---

> Swift is an impure language that is build __intentionaly__ that way.
-- Anonymous

---
__.Net to swift__ -> will there be anything else?

![left fit](dropbox.png)

---

- Swift Language ✅
- Using Playground's with Scripting __@Jelle (30 min)__
- Swift and Open Source __@Hans (15 min)__
- Swift and Backend Development __@Dylan @Hannes (20 min)__

---


# Playground

---

# Playground __*Whut?*__

Interactive Swift coding environment

---

# Playground __*Demo*__

---

# Scripting

---

# Scripting __*Whut?*__

You can just run simple command line scripts writting in Swift.

---

# Scripting __*Setup*__

Download and install the _Swift Development Snapshot[^1]_.

[^1]: https://swift.org/download/

---

# Scripting __*Setup*__

Add `export TOOLCHAINS=swift` to your `.bash_profile`.

---

# Scripting __*Setup*__

Run the following command from your CLI.

`swift build --version`

---

# Scripting __*How?*__

Create an empty file with the Swift hashbang at the top.

``` Swift
#!/usr/bin/swift
print("We 💕 Swift!")
```

---

# Scripting __*How?*__

Give the file execution rights.

`chmod +x someScript.swift`

---

# Scripting __*Go!*__

Let's run the script.

`swift someScript.swift`
`./someScript.swift`

---

# Scripting __*Demo*__

---

# REPL

---

# REPL __*Whut?*__

Read Eval Print Loop

---

# REPL __*Demo*__

---
- Swift Language ✅
- Using Playground's with Scripting ✅
- Swift and Open Source __@Hans (15 min)__
- Swift and Backend Development __@Dylan @Hannes (20 min)__

---

#Dec 3, 2015
#🎉 Swift Open Source🎉

![inline](initial_commit.png)

**https://github.com/apple/swift/commit/18844bc65229786b96b89a9fc7739c0fc897905e**

---

# *compiler + debugger*

- LLVM, clang
- LLDB + REPL

---

# *standard library*

- fundamental data types (**Int, Double, ...**)
- collections (**Array, Dictionary, ...**)
- protocols & functions
- written in “Swift"

---

# *core libraries*

- higher level functionality (networking, file system, threads, notifications, ...)
- Foundation (**NS...**), XCTest, libdispatch
- re-implemented in Swift (~~ObjC runtime~~)
- not yet ready for production

---

# *package manager*

- cfr ruby gem, cocoapods pod
- work in progress (Swift 3.0)

![inline 100%](package_manager.png)

---

# *~~Open source~~*

- ~~Xcode~~
- ~~UIKit, AppKit, ...~~
- ~~CoreGraphics, CoreAnimation, ...~~

---

# *Evolution*

- Swift 1.x (WWDC14)
- Swift 2.0 (WWDC15)
- Swift 2.2 (current, march 2016)
- Swift 3.0

---

# *Supported Platforms*

- Apple Platforms
- Linux (Ubuntu, x86_64)

### source compatibility across multiple platforms, but implementation mechanisms may differ

---

# *Android*

- https://github.com/SwiftAndroid
- https://github.com/apple/swift/pull/1442

---

# *Android*

- standard lib compiles to Android armv7
- "run Swift code on Android device"
- hacks/disabled stuff
- ~~write Android applications in Swift~~

---

# *Android*

> "Google is considering making Swift a “first class” language for Android"
-- The Next Web

---

# *Windows*

- https://github.com/tinysun212/swift-windows
- https://github.com/apple/swift/pull/1108

---

# *Windows*

- Cygwin
- standard library
- ~~REPL, debugger.~~

---

# *Web*

- https://github.com/PerfectlySoft/Perfect
- https://github.com/qutheory/vapor
- https://github.com/IBM-Swift/Kitura
- https://github.com/necolt/Swifton
- https://github.com/elliottminns/blackfish

---

# *ARMv6/ARMv7*

- https://bugs.swift.org/browse/SR-40

---

# *Raspberry Pi*

- Raspi Model B Revision 2.0
- Raspbian
- installed clang (dependency for the compiler)
- pre-compiled ARMv6 lib

---

# *Raspberry Pi*

- https://github.com/uraimo/SwiftyGPIO

---

# 💡Demo💡

---

- Swift Language ✅
- Using Playground's with Scripting ✅
- Swift and Open Source ✅
- Swift and Backend Development __@Dylan @Hannes (20 min)__

---
# Vapor
__An elegant web framework for swift__

---

Swift-development-snapshot
__https://swift.org/download/#snapshots__

---

# Why Vapor

- Wat doe Vapor?
- Vapor Host voor website
- Geschreven in Swift

---
# Package

```swift
import PackageDescription

let package = Package(
    name: "Welcome",
    dependencies: [
        .Package(url: "https://github.com/qutheory/vapor.git", majorVersion: 0)
    ]

)

```
^ Leg uit dat dit is zoals cocoapods

---
# Serve JSON highscore

Server maken



```swift

let application = Application()
application.get("highscore") { request in
  return Json(["name": "dylan", "score": "120"])
}
application.start()
```

Maak server actief

```bash
swift build
.build/debug/Welcome
```

^ leg uit dat Welcome u package name is

---
# View Data

Url openen in webview

---
# Wat kan / kan __(nog)__ niet

- Serve JSON Data
- Databank niet gelukt `Fluent`
- Geen `Cloud code`

^Je kan niet echt queries doen tot fluent werkt
^We kunnen geen _actie_ triggeren na een _request_ -> Stuur email na login ...

---
# 💡Demo💡
---
- Swift Language ✅
- Using Playground's with Scripting ✅
- Swift and Open Source ✅
- Swift and Backend Development ✅

---

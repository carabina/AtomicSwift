# AtomicSwift
A property wrapper to declare atomic properties in swift

![AtomicSwift: The atomic qualifier Swift was missing](https://raw.githubusercontent.com/MarioIannotta/AtomicSwift/master/AtomicSwift.png)

# Installation

## Swift package manager
> From Xcode, select File → Swift Packages → Add Package Dependency → Select your project → Search **SwizzleSwift**

# Usage
Just add the `@Atomic` qualifier before your variable declaration.

# Example:

```

// the following example will crash

var aDictionary = [Int: Int]()

DispatchQueue.concurrentPerform(iterations: 1000) { _ in
    self.aDictionary[.random(in: 0...10000)] = "test"
}

// the following example won't crash

@Atomic
var anAtomicDictionary = [Int: Int]()

DispatchQueue.concurrentPerform(iterations: 1000) { _ in
    self.anAtomicDictionary[.random(in: 0...10000)] = "test"
}

```

# CFoundationExterns module for Swift

This module wraps the `<crt_externs.h>` header for OS X. As a consequence you can only import the module on OS X systems. The module is released under the MIT License.

The header file defines the following functions:

```C
extern char ***_NSGetArgv(void);
extern int *_NSGetArgc(void);
extern char ***_NSGetEnviron(void);
extern char **_NSGetProgname(void);
#ifdef __LP64__
extern struct mach_header_64 *
#else /* !__LP64__ */
extern struct mach_header *
#endif /* __LP64__ */
				_NSGetMachExecuteHeader(void);
```

To call one of them in your Swift code, add the module as a dependency of your project:

```Swift
// Package.swift

import PackageDescription

let package = Package(
    // ...
    dependencies: [
        // ...
        .Package(
            url: "https://github.com/svkurowski/swift-cfoundationexterns",
            majorVersion: 1,
            minor: 0
        )
    ]
)
```

Then import the module in your Swift code:

```Swift
#if os(Linux)
    // ...
#else
    // ...
    import CFoundationExterns
#endif
```

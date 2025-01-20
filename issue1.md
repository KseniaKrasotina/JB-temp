# Bug Report
## Title: Undo operation fails after refactoring method moving

### Description: 
Undo operation fails after refactoring such as method moving with the Error window


Priority: Medium 
Severity: Medium

## Environment:

```
IntelliJ IDEA 2024.3.2
Build #JBC-243.23654.117, built on January 16, 2025
Licensed to Ksenia Krasotina
Subscription is active until February 18, 2025.
Evaluation purpose only.
Runtime version: 21.0.5+8-b631.30 x86_64 (JCEF 122.1.9)
VM: OpenJDK 64-Bit Server VM by JetBrains s.r.o.
Toolkit: sun.lwawt.macosx.LWCToolkit
macOS 15.1.1
Controller in Remote Development
GC: G1 Young Generation, G1 Concurrent GC, G1 Old Generation
Memory: 2048M
Cores: 12
Metal Rendering is ON
Registry:
  ide.experimental.ui=true
```

## Pre-condition:

Two project files are created, each containing source code:
File 1 (Initial location for the new method)
File 2 (Target destination for the method)

## Steps to Reproduce:

1. Create a new method in File 1.
2. Perform the following actions:
3. Go to Refactor → Move Members.
4. Select the newly created method.
5. Set File 2 as the destination.
6. Click Refactor.
7. Verify that the method is moved to File 2.
8. Use Undo to revert the changes.

## Expected Result:
The new method should be restored in File 1.

## Actual Result:
Bug 1 (Priority Medium):
A modal window with an error message appears during the Undo operation. The method remains in File 2 instead of being restored to File 1.

## Sceeenshot:
  ![image](https://github.com/user-attachments/assets/80603ed6-4c83-4b65-87c1-a31d5b2cc288)

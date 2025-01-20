# Bug Report
## Title: Local History Diff does not show the Before state correctly on Undo operation after refactoring method moving

### Description: 
 Local History Diff does not show the Before state correctly on Undo operation after refactoring method moving


Priority: Low 
Severity: Low

## Environment:

Application Version: v1
Operating System: [macOS Sequoia]

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
 Local History Diff id displayed Before and After state correctly in the file 1

## Actual Result:
Local History Diff does not show the Before state correctly in a file 1

## Sceeenshot:
  ![image](https://github.com/user-attachments/assets/66f0eb00-4832-4e27-85bc-716811d34bd3)

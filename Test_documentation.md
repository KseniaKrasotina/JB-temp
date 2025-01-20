# JetBrains. The QA Test Assignment, RD team.

In this Document by _Verification_ we mean four things:
1. Verifying the content in the Editor area of the action initiator
2. The content in the Editor area is synchronized among all collaborators
2. Verifying the file content on the file system
3. Verifying content in the 'Local History -> Local changes' window

## 1. The scope of Undo/Redo functionality and the depth of testing

- Single-file operations (text edits, additions, deletions) - Shallow
- Multi-file operations (edits across files) - Intermediate
- Operations on files (file creation, deletion, movement) - Intermediate
- Combinations of different operations (file editing, file creation etc.) - Deep
- Refactoring operations (ex. renaming the class) - Deep
- Collaboration (multiple users work on the same project) - Deep
- User experience (Modal windows with the clear messages when relevant, ex. file deletion) - Deep
- Error handling (connection problems, application crashes, system unexpected reboot, operations on an empty files) - Deep

## 2. Test documentation
### Entry criteria
- Testing environment (IDE and GitPods) is properly installed and configured
- Scope of testing and coverage is defined and test Cases created
- Basic functionality works as expected (IDE, simple redo/undo scenarios)
- Tools and test data are prepared
- QA Engineers have enough knowledge of a product feature and skills
- Defined non-technical criteria for the deployment

### Exit criteria
- All defined Test Cases are executed
- Issues are reported
- No critical issues remaining (resolved or addressed to be resolved in a future releases, should be defined if it's possible to postpone until another release)
- Test report/results are available
- Approval with Stakeholders
- Release only can be done if criteria for deployment met. Stakeholders give a confirmation (can be some legal causes, release documentation should be prepared and shared with partners, localisation for main languages is completed)

### Test Scenarios
#### Scenario 1: Undo/Redo for File Copy
Steps:
1. Copy file and Paste in a root directory 
2. Perform Undo to delete the file 
3. Perform Redo to return to the file

Expected result:
The file is full and correctly located

Actual result:
The file is full and correctly located

---

#### Scenario 2: Undo/Redo for File Creation
Steps:
1. Create file in a root directory 
2. Perform Undo to delete the file 
3. Perform Redo to return to the file 
4. Verify that the file is restored and located in a root directory

Expected result:
The file is restored and located in the root directory

Actual result:
The file is restored and located in the root directory

---

#### Scenario 3: Undo/Redo for File Deletion
Steps:
1. Create file in a root directory 
2. Delete a file created 
3. Perform Undo to restore the file 
4. Perform Redo to delete the file again 
5. Verify that the file is deleted

Expected result: Tested file is deleted

Actual result: Tested file is deleted

---

#### Scenario 4: Undo/Redo in a Single File
Steps:
1. Add code to the existing file 
2. Perform several editing operations in a single file 
3. Undo N changes 
4. Verify that each change is UNDOed in correct order

Expected result: Each  change is UNDOed in correct order

Actual result: Each  change is UNDOed in correct order

---

#### Scenario 5: Undo/Redo in a Single File
Steps:
1. Create a new file 
2. Add code to the file 
3. Perform several editing operations in a single file 
4. Undo N changes 
5. Redo N changes 
6. Verify that each change is REDOed in correct order and file contains the correct code

Expected result: Each change is REDOed in correct order and file contains the correct code

Actual result: Each change is REDOed in correct order and file contains the correct code

---

#### Scenario 6: Undo/Redo in collaboration Mode
Steps:
1. Connect to the project from 2 devices 
2. Make changes in a Project file 
3. Perform Undo operation simultaneously from both devices 
4. Check how system handles parallel operations

Expected result: Both undo operations performed in the file

Actual result: TBD

---

#### Scenario 7: No Confirmation window if Undo/Redo operations only performed in a single file which is active
Steps:
1. Add code to the existing file 
2. Perform several editing operations in a single file 
3. Undo N changes 
4. Redo N changes 
5. No Confirmation window appears since changes only performed in a single active class

Expected result: No Confirmation window appears

Actual result: No Confirmation window appears

---

#### Scenario 8: Undo/Redo operations performed in multiple files
Steps:
1. Add code to the existing file 1 
2. Add code to the existing file 2 
3. Perform Undo in the active file (file 2)
4. Verify changes are reverted in a file 2, file 1 not changed

Expected result: Changes are reverted in file 1 and file 2

Actual result: Changes are reverted in file 1 and file 2

---

#### Scenario 9: Confirmation window appears if Undo/Redo operations performed on file creation/change/moving
Steps:
1. Create file in a root directory 
2. Delete a file created 
3. Perform Undo to revert the file 
4. Perform Redo to delete the file again 
5. Verify Confirmation window with the relevant message appears on each Undo and Redo operation

Expected results:
Confirmation window appears on each operation with the file with the relevant confirmation message: file name, file path, action performed

Actual result: Confirmation window appears on each performed operation with the file with the relevant confirmation message

---

#### Scenario 10: Undo/Redo after connection loss
Steps:
1. Change the code in an existing class 
2. Undo the change 
3. Perform the connection loss

Expected result: Undo performed according to Product rules about connectivity problem Scenarios. It can depend on a timeout period

Actual result: TBD

---

#### Scenario 11: Undo/Redo after saving file
Steps:
1. Perform several editing operations with the text in an existing single file
2. Save the file
3. Undo N changes
4. Redo N changes
5. Verify all N changes are UNDOed and REDOed in a correct oder and file contains the code that performed in step 1

Expected result: All N changes are UNDOed and REDOed in a correct oder and file contains the code that performed in step 1

Actual result: All N changes are UNDOed and REDOed in a correct oder and file contains the code that performed in step 1

---

#### Scenario 12: Undo operation after refactoring method renaming
Steps:
1. Pre-condition: Two project file created: file 1 with method definition, file 2 with method reference 
2. Rename the method in the file 1 
3. Verify, the method is renamed in the file 2 automatically 
4. Undo operation in file 1

Expected result: 
The method is renamed to the original name in file 1 and in file 2

Actual result:
The method is renamed to the original name in file 1 and in file 2

---

#### Scenario 13: Undo operation after refactoring method moving
1. Pre-condition: Two project file created with source code
2. Create a new method in file 1
3. Do 'Refactor-> Move members -> Select new created Method -> Select file 2 as a destination -> Click Refactor'
4. Verify method is moved to the file 2
5. Undo the changes

Expected result: New method is stored in file 1

Actual result:
- Bug. Priority Medium. Modal window with an Error appears,  new method is stored in file 2. [Click](https://github.com/KseniaKrasotina/JB-temp/edit/main/issue1.md) for Bug report
  ![image](https://github.com/user-attachments/assets/80603ed6-4c83-4b65-87c1-a31d5b2cc288)

- Bug. Priority Low. Local History Diff does not show the Before state correctly in a file 1. [Click](https://github.com/KseniaKrasotina/JB-temp/blob/main/issue2.md) for Bug report
  ![image](https://github.com/user-attachments/assets/66f0eb00-4832-4e27-85bc-716811d34bd3)

---

#### Scenario 14: Redo operation after refactoring
Steps:
1. Pre-condition: Perform Scenario 13 
2. Redo changes in file 1

Expected result:
The method is renamed in both files

Actual result:
The method is renamed in both files

---

#### Scenario 15: Undo after closing/reopening file
1. Perform  editing operation with the text in an existing single file
2. Close the file
3. Open the file
4. Undo the changes 

Expected result: Changes should be reverted to the initial state

Actual result: Changes are reverted to the initial state

---

### Tools and Approaches
Testing Tools: IntelliJ IDEA, JetBrains Gateway for remote access.
Methodology: Manual testing
Logging: Local History (Recent changes, Project History for verification)
Reporting: Report issues in details with environment, steps investigation results and other steps for further investigation if needed

### Suggestions for improvement, bugs
- Add more details into 'Local History -> Recent changes'. For example there are no details about From and To destinations when user moves the method to another class
  ![image](https://github.com/user-attachments/assets/a8bd4014-9d3e-4ce5-a2c6-4fd97f4b479d)

- Bugs are detected in Scenario 13. Screenshots are attached

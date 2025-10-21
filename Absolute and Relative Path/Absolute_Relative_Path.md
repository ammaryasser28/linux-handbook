🧭 Absolute Path vs Relative Path
| **Type**          | **Starts With** | **Description**                                                                                                                         | **Example**            | **Works From Any Location?** |
| :---------------- | :-------------: | :-------------------------------------------------------------------------------------------------------------------------------------- | :--------------------- | :--------------------------: |
| **Absolute Path** |       `/`       | The full path from the root directory `/` to the target file or folder. It always points to the same location, no matter where you are. | `/home/amr/test/file1` |             ✅ Yes            |
| **Relative Path** |   *(No slash)*  | The path relative to your current working directory. It depends on where you currently are in the system.                               | `test/file1`           |             ❌ No             |

💡 Notes
| **Command** | **Meaning**                                         | **Example / Output**      |
| :---------- | :-------------------------------------------------- | :------------------------ |
| `pwd`       | Prints the current working directory                | `/home/amr`               |
| `cd`        | Changes the current directory                       | `cd test`                 |
| `ls`        | Lists files and directories in the current location | `ls → file1 file2`        |
| `.`         | Refers to the **current directory**                 | `./file1`                 |
| `..`        | Refers to the **parent directory**                  | `cd ..` (go one level up) |

📘 Example Illustration
| **Command**                  | **Path Type** | **Creates File At**                                              |
| :--------------------------- | :------------ | :--------------------------------------------------------------- |
| `touch /home/amr/test/file1` | Absolute      | `/home/amr/test/file1`                                           |
| `touch test/file1`           | Relative      | `/home/amr/test/file1` *(because you're already in `/home/amr`)* |

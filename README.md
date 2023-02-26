## icomment

This script aims to simplify the process of adding comments when committing code to Git by adding comments to modified code blocks in the **staging area**.

#### Comment Style

```diff
//username comment date start
- origin source code
+ changed source code
//username comment date end
```

### Usage

1. Download the script and place it in your code repository. In Git Bash or a Linux terminal, run the script using the following command:

   ```shell
   $ chmod +x icomment.sh # First-time script execution requires adding execute permission
   $ ./icomment.sh <file_path> <comment>
   ```

   - <file_path>: The path of the file or folder you want to add comments to.
   - <comment>: The comment you want to add.

2. After executing the script, it will automatically add comments to the src/test.java file with the content "modify string" and add the modified file to the Git staging area. Script execution example:

   ```shell
   $ ./icomment.sh src/test.java "modify string"
   modified file src/test.java
   ```

   Original state:

   ```diff
   diff --git a/test.java b/test.java
   index 70fd330..f499d88 100644
   --- a/test.java
   +++ b/test.java
   @@ -1,5 +1,5 @@
    public class HelloWorld {
        public static void main(String[] args) {
   -        System.out.println("Hello, World!");
   +        System.out.println("Hello, icomment!");
        }
    }
   ```

   State after script execution:

   ```diff
   diff --git a/test.java b/test.java
   index 70fd330..941c28d 100644
   --- a/test.java
   +++ b/test.java
   @@ -1,5 +1,7 @@
    public class HelloWorld {
        public static void main(String[] args) {
   -        System.out.println("Hello, World!");
   +        //username modify string 2023-02-26 start
   +        System.out.println("Hello, icomment!");
   +        //username modify string 2023-02-26 end
        }
    }
   ```

### Notes

1. **The script only adds comments to changes in the staging area!!!**
2. The script only supports the following file types: .java, .py, .sh, .mk, .bp, .c, .h, .rs, .cpp, .js, and .xml. If your code repository contains other file types, modify the **markup** array in the script to add the corresponding comment symbols.
3. To avoid accidental commits, the comments added by the script will not be automatically added to the staging area. If you want to add them directly to the staging area, uncomment line 132 in the script.
4. The script does not check whether your modifications already have comments. Repeatedly executing the script will add comments repeatedly.
5. Due to the special syntax of XML, using the script to add comments to XML may have issues. Use with caution.
6. If you are not satisfied with the default comment format, modify the **insert_string** variable.

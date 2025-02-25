# Minecraft-Servers-UID-Extractor
A batch script to automatically search and back up Minecraft server files based on specified UIDs, preserving folder structure without modifying the original files.



This script is designed to **automate the backup process** for Minecraft server files by searching for specific **UIDs** (unique identifiers) within a source directory and copying matching files to a destination directory, while preserving the folder structure. Here's a detailed explanation of what it does:

### Features of the Script:
1. **Source and Destination Directories**: The script prompts you to input the **source directory** (your Minecraft server folder) and the **destination directory** (where you want the backup).
2. **UID-based Search**: The script searches for files that **match the given UIDs** (user-defined identifiers) in the source directory. It does not take file extensions like `.dat`, `.yml`, or `.json` into account; it looks for any files whose names include the specified UIDs.
3. **Folder Structure Preservation**: The script ensures that the **same folder structure** is recreated in the backup destination, meaning the files are copied into their corresponding subdirectories in the backup location.
4. **Non-destructive**: The script **does not modify or delete any files** in the source directory. It only copies the matched files to the destination.
5. **Status Display**: It will display a message indicating whether any files were found and backed up for each UID, or if no files were found for the given UID.

### Example:
If your **source directory** is structured like this:
```
minecraft-server>world>playerdata> 12345678.dat 12345678.dat_old qwertyu.dat qwertyu.dat_old
```
And you give the **UIDs** `12345678`, the script will:
- Search for any files containing `12345678` in their names.
- Copy `12345678.dat` and `12345678.dat_old` to the destination directory, preserving the folder structure.
- It **won’t copy** `qwertyu.dat` or `qwertyu.dat_old`.

### Script Walkthrough:
1. **Input Prompts**: 
   - Asks for the **source directory** where your server files are located.
   - Asks for the **destination directory** where the backup will be stored.
   - Asks for the **UIDs** (can be multiple) that you want to search for in the files.

2. **Directory Validation**: 
   - If either the source or destination directory does not exist, the script shows an error message and exits.

3. **UID Search**:
   - For each UID entered, it searches the source directory and its subdirectories (`for /r`) for files whose names contain the UID.
   - If a match is found, it will:
     - Create the same folder structure in the backup directory.
     - Copy the matching file to the backup directory.
   - A **status message** is displayed for each UID:
     - "Files for [UID] were found and backed up."
     - "No files found for [UID]."

4. **Backup Completion**: 
   - After all UIDs are processed, the script displays: `Backup completed`.

### Example Run:
- **Source**: `D:\serverdirectory\minecraftserver`
- **Destination**: `D:\backup`
- **UIDs**: `12345678`

The script will search for files containing `12345678` in the `minecraftserver` folder (like `12345678.dat` and `12345678.dat_old`), copy them to the `D:\backup` directory, and preserve the folder structure.

### Instructions:
1. Save the script as `backup.bat`.
2. Double-click to run the script.
3. It will ask you to input:
   - Source directory.
   - Destination directory.
   - UIDs to search for.
4. The script will perform the backup operation based on your inputs.

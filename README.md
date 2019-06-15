# UFPT
User Folder Protection Tool

## Escape UnauthorizedAccessException when Enumerating User Profile Folders
```csharp
public static bool CopyFolderWithoutErrors(string sourcePath, string destinationPath)
{
  try
  {
    // Set Variables
    string source_dir = Path.GetFullPath(sourcePath);
    string destination_dir = Path.GetFullPath(destinationPath);
    
    // Create subdirectory structure in destination    
    foreach (string dir in System.IO.Directory.GetDirectories(source_dir, "*", System.IO.SearchOption.AllDirectories))
    {
        System.IO.Directory.CreateDirectory(System.IO.Path.Combine(destination_dir, dir.Substring(source_dir.Length + 1)));
    }
    
    // Copy files over to their respective directories in destination
    foreach (string file_name in System.IO.Directory.GetFiles(source_dir, "*", System.IO.SearchOption.AllDirectories))
    {
        System.IO.File.Copy(file_name, System.IO.Path.Combine(destination_dir, file_name.Substring(source_dir.Length + 1)));
    }
    
    return true;
  }
  
  catch (Exception ex)
  {
    MessageBox.Show("Error: " + ex.Message, "Error!", MessageBoxButtons.OK, MessageBoxIcon.Error);
    return false;
  }
}
```

Issue resolved.

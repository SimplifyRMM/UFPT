# UFPT
User Folder Protection Tool

## Escape UnauthorizedAccessException when Enumerating User Profile Folders
```csharp-interactive
public static bool IndexFiles(string profile)
{
  try
  {
    List<string> files = new List<string>();
    
    foreach (string str in Directory.EnumerateFiles(@"C:\Users\" + profile, "*.*", DirectoryOptions.AllDirectories))
    {
      files.Add(str.ToString().Trim());
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

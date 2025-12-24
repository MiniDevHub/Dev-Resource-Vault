<div align="center">

# 💙 Windows PowerShell - Complete Mastery Guide

![PowerShell](https://img.shields.io/badge/Windows-PowerShell-blue?style=for-the-badge&logo=powershell)
![Version](https://img.shields.io/badge/Version-5.1_%7C_7.x-blue?style=for-the-badge)
![Level](https://img.shields.io/badge/Level-Beginner_to_Expert-green?style=for-the-badge)

### _From Zero to PowerShell Hero_ ⚡

**Because CMD is ancient history** 💻✨

</div>

---

## 📚 Table of Contents

- [🚀 Getting Started](#-getting-started)
- [📂 File System Operations](#-file-system-operations)
- [👥 User & Permission Management](#-user--permission-management)
- [📦 Package Management](#-package-management)
- [🔌 Process & Service Management](#-process--service-management)
- [🌐 Networking](#-networking)
- [🗃️ Registry Operations](#️-registry-operations)
- [⏰ Scheduled Tasks](#-scheduled-tasks)
- [💻 System Administration](#-system-administration)
- [🔐 Security & Encryption](#-security--encryption)
- [☁️ Remote Management](#️-remote-management)
- [🎨 Customization & Configuration](#-customization--configuration)
- [🧪 Advanced Scripting](#-advanced-scripting)
- [💡 Pro Tips & Best Practices](#-pro-tips--best-practices)

---

<div align="center">

## 🚀 Getting Started

</div>

### PowerShell Basics 🎯

```powershell
# ═══════════════════════════════════════════
# POWERSHELL vs WINDOWS POWERSHELL vs CMD
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                     VERSION DIFFERENCES                    ║
╚════════════════════════════════════════════════════════════╝

Windows PowerShell 5.1:
─────────────────────────────────────────────────────────────
• Built on .NET Framework
• Windows-only
• Comes with Windows
• powershell.exe

PowerShell 7+ (PowerShell Core):
─────────────────────────────────────────────────────────────
• Built on .NET Core / .NET 5+
• Cross-platform (Windows, macOS, Linux)
• Install separately
• pwsh.exe
• Better performance
• Modern features

CMD (Command Prompt):
─────────────────────────────────────────────────────────────
• Ancient (1981)
• Limited features
• Use PowerShell instead!

# ═══════════════════════════════════════════
# INSTALLATION
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║               INSTALL POWERSHELL 7+                        ║
╚════════════════════════════════════════════════════════════╝

# Using winget
winget install --id Microsoft.PowerShell --source winget

# Using MSI (download from GitHub)
# https://github.com/PowerShell/PowerShell/releases

# Using Chocolatey
choco install powershell-core

# Verify installation
pwsh --version
$PSVersionTable

# ═══════════════════════════════════════════
# BASIC INFORMATION
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   SYSTEM INFORMATION                       ║
╚════════════════════════════════════════════════════════════╝

# PowerShell version
$PSVersionTable
$PSVersionTable.PSVersion           # Version only
$PSVersionTable.PSEdition           # Core or Desktop

# Current directory
Get-Location                        # PowerShell way
pwd                                # UNIX alias
gl                                 # Short alias
$PWD                               # Automatic variable

# Current user
$env:USERNAME                      # Username only
$env:USERDOMAIN                    # Domain
whoami                             # Domain\Username
whoami /upn                        # User Principal Name
[System.Security.Principal.WindowsIdentity]::GetCurrent().Name

# Check if running as Administrator
([Security.Principal.WindowsPrincipal][Security.Principal.WindowsIdentity]::GetCurrent()).IsInRole([Security.Principal.WindowsBuiltInRole]::Administrator)

# Host information
Get-Host
$Host.Name
$Host.Version
$Host.UI.RawUI.WindowTitle         # Window title

# System information
Get-ComputerInfo                   # Comprehensive (slow)
systeminfo                         # Classic command
Get-CimInstance Win32_OperatingSystem
Get-CimInstance Win32_ComputerSystem

# Windows version
[System.Environment]::OSVersion
(Get-ItemProperty "HKLM:\SOFTWARE\Microsoft\Windows NT\CurrentVersion").ProductName

# Computer name
$env:COMPUTERNAME
hostname
[System.Net.Dns]::GetHostName()

# ═══════════════════════════════════════════
# CLEAR SCREEN & DISPLAY
# ═══════════════════════════════════════════

Clear-Host                         # PowerShell way
cls                               # Alias
clear                             # UNIX alias
Ctrl+L                            # Keyboard shortcut

# Clear screen but keep scrollback
[Console]::Clear()

# Set window title
$Host.UI.RawUI.WindowTitle = "My Custom Title"

# ═══════════════════════════════════════════
# COMMAND HISTORY
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   COMMAND HISTORY                          ║
╚════════════════════════════════════════════════════════════╝

Get-History                        # Show session history
history                           # Alias
h                                 # Short alias
Get-History -Count 20             # Last 20 commands

# Execute from history
Invoke-History -Id 5              # Run command #5
r 5                               # Short way

# Clear history
Clear-History                     # Session history
Clear-History -Count 10           # Last 10

# History file location
(Get-PSReadLineOption).HistorySavePath

# Search history
Get-History | Where-Object {$_.CommandLine -like "*git*"}

# PSReadLine history (persistent)
Get-Content (Get-PSReadLineOption).HistorySavePath
Get-Content (Get-PSReadLineOption).HistorySavePath | Select-String "keyword"

# Reverse history search
Ctrl+R                            # Interactive search

# ═══════════════════════════════════════════
# GETTING HELP
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                      HELP SYSTEM                           ║
╚════════════════════════════════════════════════════════════╝

# Basic help
Get-Help Get-Process
help Get-Process                  # Alias (paginated)
man Get-Process                   # UNIX alias

# Detailed help
Get-Help Get-Process -Detailed

# Full help (all details)
Get-Help Get-Process -Full

# Examples only
Get-Help Get-Process -Examples

# Online help (opens browser)
Get-Help Get-Process -Online

# Show help in window
Get-Help Get-Process -ShowWindow

# Update help files (run as admin)
Update-Help
Update-Help -Force                # Force update
Update-Help -UICulture en-US      # Specific language

# About topics
Get-Help about_*                  # List all about topics
Get-Help about_Variables
Get-Help about_Arrays
Get-Help about_Operators
Get-Help about_Comparison_Operators
Get-Help about_Pipelines

# Search for commands
Get-Command *process*             # Find commands
Get-Command -Verb Get             # All Get commands
Get-Command -Noun Service         # All Service commands
Get-Command -Module Microsoft*    # Commands from modules

# Command syntax
Get-Command Get-Process -Syntax

# ═══════════════════════════════════════════
# ALIASES
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                      ALIASES                               ║
╚════════════════════════════════════════════════════════════╝

# List all aliases
Get-Alias
gal                               # Alias for Get-Alias

# What command does alias run?
Get-Alias -Name ls
Get-Alias ls

# Find aliases for command
Get-Alias -Definition Get-ChildItem

# Create alias (session only)
Set-Alias -Name ll -Value Get-ChildItem
sal ll Get-ChildItem              # Short form

# Create alias with parameters (use function)
function ll { Get-ChildItem -Force }

# Remove alias
Remove-Alias -Name ll

# Export/Import aliases
Export-Alias -Path aliases.csv
Import-Alias -Path aliases.csv

# Common aliases
# ls, dir, gci    → Get-ChildItem
# cd, chdir, sl   → Set-Location
# pwd, gl         → Get-Location
# cat, type, gc   → Get-Content
# cp, copy        → Copy-Item
# mv, move        → Move-Item
# rm, del         → Remove-Item
# ps, gps         → Get-Process
# kill            → Stop-Process
# clear, cls      → Clear-Host

# ═══════════════════════════════════════════
# OUTPUT & FORMATTING
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   OUTPUT FORMATTING                        ║
╚════════════════════════════════════════════════════════════╝

# Write output
Write-Output "Hello"              # Standard output
Write-Host "Hello"                # Console only (colored)
Write-Verbose "Debug info" -Verbose
Write-Warning "Warning!"
Write-Error "Error!"

# Colored output
Write-Host "Success!" -ForegroundColor Green
Write-Host "Error!" -ForegroundColor Red -BackgroundColor White

# Format table
Get-Process | Format-Table
Get-Process | ft                  # Alias
Get-Process | Format-Table Name, Id, CPU -AutoSize
Get-Process | Format-Table * -Wrap

# Format list
Get-Process | Format-List
Get-Process | fl                  # Alias
Get-Process | Format-List *       # All properties

# Format wide
Get-Process | Format-Wide
Get-Process | fw                  # Alias

# Custom columns
Get-Process | Format-Table Name,
    @{Label="Memory(MB)";Expression={$_.WS/1MB};FormatString="N2"},
    @{Label="CPU(s)";Expression={$_.CPU};FormatString="N2"}

# Output to file
Get-Process | Out-File processes.txt
Get-Process | Out-File processes.txt -Append
Get-Process | Out-File processes.txt -Width 200

# Convert to formats
Get-Process | ConvertTo-Json
Get-Process | ConvertTo-Csv
Get-Process | ConvertTo-Html
Get-Process | ConvertTo-Xml

# Export
Get-Process | Export-Csv processes.csv -NoTypeInformation
Get-Process | Export-Clixml processes.xml

# GridView (GUI table)
Get-Process | Out-GridView
Get-Process | Out-GridView -PassThru  # Select and return

# Measure
Get-Process | Measure-Object
Get-ChildItem | Measure-Object -Property Length -Sum -Average

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## 📂 File System Operations

</div>

### Navigation & Listing 🗺️

```powershell
# ═══════════════════════════════════════════
# DIRECTORY NAVIGATION
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   NAVIGATION COMMANDS                      ║
╚════════════════════════════════════════════════════════════╝

# Change directory
Set-Location C:\Path\To\Directory
cd C:\Path\To\Directory           # Alias
sl C:\Path\To\Directory           # Alias
chdir C:\Path\To\Directory        # Alias

# Special directories
cd ~                              # Home directory
cd $HOME                         # Home directory
cd $env:USERPROFILE              # Home directory
cd ..                            # Parent directory
cd ..\..                         # Two levels up
cd \                             # Root of current drive
cd C:\                           # Specific drive root

# Change drive
D:                               # Switch to D drive
Set-Location D:\

# Show current location
Get-Location
pwd                              # Alias
gl                               # Alias
$PWD                             # Variable

# Directory stack
Push-Location C:\Temp            # Save current, go to new
pushd C:\Temp                    # Alias
Pop-Location                     # Return to saved
popd                             # Alias
Get-Location -Stack              # View stack

# ═══════════════════════════════════════════
# LISTING FILES & DIRECTORIES
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   LISTING COMMANDS                         ║
╚════════════════════════════════════════════════════════════╝

# Basic listing
Get-ChildItem                    # PowerShell way
gci                             # Alias
ls                              # UNIX alias
dir                             # DOS alias

# List specific path
Get-ChildItem C:\Path
Get-ChildItem -Path C:\Path

# Common parameters
Get-ChildItem -Filter *.txt      # Filter pattern
Get-ChildItem -Include *.txt     # Include files
Get-ChildItem -Exclude *.log     # Exclude files
Get-ChildItem -Recurse           # Recursive
Get-ChildItem -Force             # Include hidden
Get-ChildItem -Directory         # Directories only
Get-ChildItem -File              # Files only
Get-ChildItem -Hidden            # Hidden only
Get-ChildItem -ReadOnly          # Read-only files
Get-ChildItem -System            # System files

# Depth control
Get-ChildItem -Recurse -Depth 2  # Max 2 levels

# Name only
Get-ChildItem -Name
Get-ChildItem -Name -Recurse

# Attributes
Get-ChildItem -Attributes Hidden
Get-ChildItem -Attributes ReadOnly,Hidden

# Multiple filters
Get-ChildItem -Path C:\,D:\ -Include *.txt,*.log -Recurse -Force

# ═══════════════════════════════════════════
# DETAILED LISTINGS
# ═══════════════════════════════════════════

# Detailed listing
Get-ChildItem | Format-List *
Get-ChildItem | fl *             # Alias

# Custom columns
Get-ChildItem | Format-Table Name, Length, LastWriteTime -AutoSize
Get-ChildItem | ft Name, Length, LastWriteTime -AutoSize

# Human-readable sizes
Get-ChildItem | Select-Object Name,
    @{Name="Size(MB)";Expression={[math]::Round($_.Length/1MB, 2)}},
    LastWriteTime

# Sort options
Get-ChildItem | Sort-Object Length -Descending
Get-ChildItem | Sort-Object LastWriteTime
Get-ChildItem | Sort-Object Name
Get-ChildItem | Sort-Object Extension, Name

# Filter by size
Get-ChildItem | Where-Object {$_.Length -gt 1MB}
Get-ChildItem | Where-Object {$_.Length -gt 100MB}
Get-ChildItem | ? {$_.Length -gt 1GB}

# Filter by date
Get-ChildItem | Where-Object {$_.LastWriteTime -gt (Get-Date).AddDays(-7)}
Get-ChildItem | Where-Object {$_.CreationTime -lt (Get-Date).AddMonths(-6)}

# ═══════════════════════════════════════════
# FILE INFORMATION
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   FILE PROPERTIES                          ║
╚════════════════════════════════════════════════════════════╝

# File info
Get-Item filename.txt
gi filename.txt                  # Alias

# File properties
Get-ItemProperty filename.txt
Get-ItemProperty filename.txt -Name Length, LastWriteTime

# Specific properties
(Get-Item filename.txt).Length
(Get-Item filename.txt).LastWriteTime
(Get-Item filename.txt).CreationTime
(Get-Item filename.txt).Attributes
(Get-Item filename.txt).FullName
(Get-Item filename.txt).BaseName
(Get-Item filename.txt).Extension

# File exists?
Test-Path filename.txt
Test-Path C:\Path\To\File.txt -PathType Leaf    # File
Test-Path C:\Path\To\Folder -PathType Container  # Directory

# Get file age
$file = Get-Item filename.txt
$age = (Get-Date) - $file.LastWriteTime
$age.Days

# Directory size
Get-ChildItem -Recurse | Measure-Object -Property Length -Sum
(Get-ChildItem -Recurse | Measure-Object -Property Length -Sum).Sum / 1MB

# Faster directory size
$size = 0
Get-ChildItem -Recurse -File | ForEach-Object {$size += $_.Length}
[math]::Round($size/1GB, 2)

# File hash (checksums)
Get-FileHash filename.txt                    # SHA256 default
Get-FileHash filename.txt -Algorithm MD5
Get-FileHash filename.txt -Algorithm SHA1
Get-FileHash filename.txt -Algorithm SHA256
Get-FileHash filename.txt -Algorithm SHA512

# Compare file hashes
$hash1 = Get-FileHash file1.txt
$hash2 = Get-FileHash file2.txt
$hash1.Hash -eq $hash2.Hash

# File version info (executables)
(Get-Item program.exe).VersionInfo
(Get-Command powershell.exe).FileVersionInfo

# ═══════════════════════════════════════════
# ADVANCED FILTERING
# ═══════════════════════════════════════════

# Find large files
Get-ChildItem -Recurse -File |
    Where-Object {$_.Length -gt 100MB} |
    Sort-Object Length -Descending |
    Select-Object FullName,
        @{Name="SizeGB";Expression={[math]::Round($_.Length/1GB,2)}}

# Find old files
Get-ChildItem -Recurse |
    Where-Object {$_.LastWriteTime -lt (Get-Date).AddYears(-1)}

# Find empty directories
Get-ChildItem -Recurse -Directory |
    Where-Object {-not (Get-ChildItem $_.FullName)}

# Find duplicate files
Get-ChildItem -Recurse -File |
    Group-Object Length |
    Where-Object {$_.Count -gt 1} |
    ForEach-Object {
        $_.Group | Group-Object {(Get-FileHash $_.FullName).Hash} |
        Where-Object {$_.Count -gt 1}
    }

# Find files by extension
Get-ChildItem -Recurse -Include *.jpg,*.png,*.gif

# Find files modified today
Get-ChildItem -Recurse |
    Where-Object {$_.LastWriteTime.Date -eq (Get-Date).Date}

# Count files by extension
Get-ChildItem -Recurse -File |
    Group-Object Extension |
    Sort-Object Count -Descending |
    Select-Object Count, Name

═══════════════════════════════════════════════════════════
```

---

### File Operations 📝

```powershell
# ═══════════════════════════════════════════
# CREATING FILES & DIRECTORIES
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   CREATE OPERATIONS                        ║
╚════════════════════════════════════════════════════════════╝

# Create empty file
New-Item -ItemType File -Path filename.txt
ni -ItemType File -Path filename.txt    # Alias
"" > filename.txt                       # Quick way
Out-File -FilePath filename.txt
New-Item filename.txt                   # Short form

# Create file with content
"Hello, World!" | Out-File filename.txt
New-Item -ItemType File -Path file.txt -Value "Content"

# Create multiple files
1..10 | ForEach-Object { New-Item "file$_.txt" -ItemType File }

# Create directory
New-Item -ItemType Directory -Path FolderName
mkdir FolderName                        # Alias
md FolderName                          # Alias

# Create nested directories
New-Item -ItemType Directory -Path "Path\To\Nested\Folders" -Force
mkdir -p Path\To\Nested\Folders        # Force create

# Create directory structure
$structure = @("src\components", "src\utils", "tests", "docs")
$structure | ForEach-Object { New-Item $_ -ItemType Directory -Force }

# ═══════════════════════════════════════════
# COPYING FILES & DIRECTORIES
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   COPY OPERATIONS                          ║
╚════════════════════════════════════════════════════════════╝

# Copy file
Copy-Item source.txt destination.txt
cp source.txt destination.txt           # Alias
copy source.txt destination.txt         # Alias
cpi source.txt destination.txt          # Alias

# Copy to directory
Copy-Item source.txt C:\Destination\

# Copy directory
Copy-Item -Path SourceFolder -Destination DestFolder -Recurse
Copy-Item -Path SourceFolder -Destination DestFolder -Recurse -Force

# Copy with filter
Copy-Item -Path C:\Source\* -Include *.txt -Destination C:\Dest
Copy-Item -Path C:\Source\* -Exclude *.log -Destination C:\Dest

# Copy and force overwrite
Copy-Item source.txt dest.txt -Force

# Copy preserving structure
Copy-Item -Path C:\Source\* -Destination C:\Dest -Recurse -Container

# Copy with progress
$files = Get-ChildItem C:\Source -Recurse
$totalFiles = $files.Count
$current = 0
foreach ($file in $files) {
    $current++
    Write-Progress -Activity "Copying files" -Status "$current of $totalFiles" `
        -PercentComplete (($current/$totalFiles)*100)
    Copy-Item $file.FullName -Destination "C:\Dest"
}

# Robocopy (robust file copy)
robocopy C:\Source C:\Dest /E /Z /R:3 /W:10
# /E - Copy subdirectories including empty
# /Z - Restartable mode
# /R:3 - Retry 3 times
# /W:10 - Wait 10 seconds between retries

# ═══════════════════════════════════════════
# MOVING & RENAMING
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   MOVE & RENAME                            ║
╚════════════════════════════════════════════════════════════╝

# Move file
Move-Item source.txt destination.txt
mv source.txt destination.txt           # Alias
move source.txt destination.txt         # Alias
mi source.txt destination.txt           # Alias

# Move to directory
Move-Item source.txt C:\Destination\

# Move directory
Move-Item -Path SourceFolder -Destination C:\Destination
Move-Item -Path SourceFolder -Destination C:\Destination -Force

# Rename file
Rename-Item oldname.txt newname.txt
ren oldname.txt newname.txt            # Alias
rni oldname.txt newname.txt            # Alias

# Rename with pattern
Get-ChildItem *.txt | Rename-Item -NewName {$_.Name -replace 'old','new'}

# Bulk rename - add prefix
Get-ChildItem *.jpg | Rename-Item -NewName {"prefix_" + $_.Name}

# Bulk rename - add suffix
Get-ChildItem *.jpg | Rename-Item -NewName {$_.BaseName + "_suffix" + $_.Extension}

# Bulk rename - sequential numbering
$i = 1
Get-ChildItem *.jpg | ForEach-Object {
    Rename-Item $_ -NewName ("photo_{0:D3}{1}" -f $i, $_.Extension)
    $i++
}

# Rename with timestamp
Get-ChildItem *.txt | Rename-Item -NewName {
    $_.BaseName + "_" + (Get-Date -Format "yyyyMMdd") + $_.Extension
}

# Change file extension
Get-ChildItem *.txt | Rename-Item -NewName {$_.Name -replace '\.txt$','.log'}

# Lowercase all filenames
Get-ChildItem | Rename-Item -NewName {$_.Name.ToLower()}

# Remove spaces from filenames
Get-ChildItem | Rename-Item -NewName {$_.Name -replace ' ','_'}

# ═══════════════════════════════════════════
# DELETING FILES & DIRECTORIES
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   DELETE OPERATIONS                        ║
╚════════════════════════════════════════════════════════════╝

# Delete file
Remove-Item filename.txt
rm filename.txt                        # Alias
del filename.txt                       # Alias
ri filename.txt                        # Alias

# Delete directory
Remove-Item FolderName -Recurse
Remove-Item FolderName -Recurse -Force

# Delete with confirmation
Remove-Item filename.txt -Confirm

# Delete without confirmation
Remove-Item *.tmp -Force

# Delete matching pattern
Remove-Item *.log
Remove-Item * -Include *.tmp
Remove-Item * -Exclude *.txt

# Delete old files
Get-ChildItem |
    Where-Object {$_.LastWriteTime -lt (Get-Date).AddDays(-30)} |
    Remove-Item -Force

# Delete empty directories
Get-ChildItem -Directory -Recurse |
    Where-Object {-not (Get-ChildItem $_.FullName)} |
    Remove-Item -Force

# Delete large files
Get-ChildItem -Recurse |
    Where-Object {$_.Length -gt 1GB} |
    Remove-Item -Force

# Safe delete to Recycle Bin (requires COM)
$shell = New-Object -ComObject Shell.Application
$item = $shell.Namespace(0).ParseName("C:\Path\To\File.txt")
$item.InvokeVerb("delete")

# Permanent delete (bypass Recycle Bin)
Remove-Item C:\Path\To\File.txt -Force

# Delete read-only files
Get-ChildItem -ReadOnly | Remove-Item -Force

# ═══════════════════════════════════════════
# READING FILES
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   READING FILES                            ║
╚════════════════════════════════════════════════════════════╝

# Read entire file
Get-Content filename.txt
gc filename.txt                        # Alias
cat filename.txt                       # UNIX alias
type filename.txt                      # DOS alias

# Read as array (one line per element)
$lines = Get-Content filename.txt

# Read as single string
Get-Content filename.txt -Raw
$content = Get-Content filename.txt -Raw

# Read specific lines
Get-Content filename.txt -TotalCount 10        # First 10 lines
Get-Content filename.txt -Head 10              # First 10
Get-Content filename.txt -Tail 10              # Last 10 lines
Get-Content filename.txt | Select-Object -First 10
Get-Content filename.txt | Select-Object -Last 10

# Read range of lines
Get-Content filename.txt | Select-Object -Skip 5 -First 10

# Read and filter
Get-Content filename.txt | Select-String "pattern"
Get-Content filename.txt | Select-String "error" -CaseSensitive
Get-Content filename.txt | Select-String "error" -NotMatch

# Read with regex
Get-Content filename.txt | Select-String "\d{3}-\d{3}-\d{4}"

# Monitor file changes (like tail -f)
Get-Content filename.txt -Wait
Get-Content filename.txt -Wait -Tail 10

# Read specific encoding
Get-Content filename.txt -Encoding UTF8
Get-Content filename.txt -Encoding ASCII
Get-Content filename.txt -Encoding Unicode

# Read binary file
Get-Content file.bin -Encoding Byte
[System.IO.File]::ReadAllBytes("file.bin")

# Read file streams
Get-Content filename.txt -Stream
Get-Item filename.txt -Stream *              # List all streams

# Count lines
(Get-Content filename.txt).Count
(Get-Content filename.txt | Measure-Object -Line).Lines

# Read CSV
Import-Csv data.csv
$data = Import-Csv data.csv
$data | Where-Object {$_.Status -eq "Active"}

# Read JSON
Get-Content data.json | ConvertFrom-Json
$json = Get-Content data.json -Raw | ConvertFrom-Json

# Read XML
[xml]$xml = Get-Content data.xml
$xml = Import-Clixml data.xml

# ═══════════════════════════════════════════
# WRITING FILES
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   WRITING FILES                            ║
╚════════════════════════════════════════════════════════════╝

# Overwrite file
"Hello, World!" | Out-File filename.txt
"Hello, World!" > filename.txt              # Redirect
Set-Content filename.txt "Hello, World!"
sc filename.txt "Hello, World!"             # Alias

# Append to file
"New line" | Out-File filename.txt -Append
"New line" >> filename.txt                  # Redirect append
Add-Content filename.txt "New line"
ac filename.txt "New line"                  # Alias

# Write multiple lines
@"
Line 1
Line 2
Line 3
"@ | Out-File filename.txt

# Write array to file
$array = @("Line 1", "Line 2", "Line 3")
$array | Out-File filename.txt
Set-Content filename.txt $array

# Write without newline
"Text" | Out-File filename.txt -NoNewline

# Write with encoding
"Text" | Out-File filename.txt -Encoding UTF8
"Text" | Out-File filename.txt -Encoding ASCII

# Write CSV
$data | Export-Csv data.csv -NoTypeInformation
$data | Export-Csv data.csv -Delimiter ";"

# Write JSON
$data | ConvertTo-Json | Out-File data.json
$data | ConvertTo-Json -Depth 10 | Out-File data.json

# Write XML
$data | Export-Clixml data.xml

# Write binary
$bytes = [byte[]](0..255)
[System.IO.File]::WriteAllBytes("file.bin", $bytes)

# Atomic write (safer for critical files)
$temp = [System.IO.Path]::GetTempFileName()
"Content" | Out-File $temp
Move-Item $temp filename.txt -Force

# ═══════════════════════════════════════════
# FINDING FILES
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   SEARCHING FILES                          ║
╚════════════════════════════════════════════════════════════╝

# Find by name
Get-ChildItem -Path C:\ -Filter "*.txt" -Recurse -ErrorAction SilentlyContinue

# Find by name pattern
Get-ChildItem -Recurse -Include *.jpg,*.png,*.gif

# Find by size
Get-ChildItem -Recurse | Where-Object {$_.Length -gt 100MB}
Get-ChildItem -Recurse | Where-Object {$_.Length -lt 1KB}

# Find by date
Get-ChildItem -Recurse | Where-Object {$_.LastWriteTime -gt (Get-Date).AddDays(-7)}
Get-ChildItem -Recurse | Where-Object {$_.CreationTime -lt (Get-Date).AddYears(-1)}

# Find by attribute
Get-ChildItem -Recurse -Hidden
Get-ChildItem -Recurse -ReadOnly
Get-ChildItem -Recurse -Attributes Hidden,ReadOnly

# Search file content
Get-ChildItem -Recurse -Include *.txt | Select-String "search term"
Get-ChildItem -Recurse | Select-String "error" -List
Get-ChildItem -Recurse | Select-String "error" -CaseSensitive

# Find empty files
Get-ChildItem -Recurse -File | Where-Object {$_.Length -eq 0}

# Find files modified today
Get-ChildItem -Recurse | Where-Object {$_.LastWriteTime.Date -eq (Get-Date).Date}

# Find files by owner
Get-ChildItem -Recurse | Where-Object {
    (Get-Acl $_.FullName).Owner -eq "DOMAIN\Username"
}

# Find duplicate files by name
Get-ChildItem -Recurse |
    Group-Object Name |
    Where-Object {$_.Count -gt 1} |
    Select-Object -ExpandProperty Group

# Find duplicate files by content (hash)
Get-ChildItem -Recurse -File |
    Group-Object {(Get-FileHash $_.FullName).Hash} |
    Where-Object {$_.Count -gt 1}

# Find and count files
Get-ChildItem -Recurse -File |
    Group-Object Extension |
    Select-Object Count, Name |
    Sort-Object Count -Descending

# ═══════════════════════════════════════════
# COMPRESSION (ZIP)
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   ZIP OPERATIONS                           ║
╚════════════════════════════════════════════════════════════╝

# Create zip
Compress-Archive -Path C:\Source -DestinationPath C:\archive.zip
Compress-Archive -Path C:\Source\* -DestinationPath C:\archive.zip

# Multiple sources
Compress-Archive -Path C:\Folder1,C:\Folder2,C:\file.txt -DestinationPath C:\archive.zip

# Update existing zip
Compress-Archive -Path C:\NewFiles -Update -DestinationPath C:\archive.zip

# Compression level
Compress-Archive -Path C:\Source -DestinationPath C:\archive.zip -CompressionLevel Optimal
# Levels: NoCompression, Fastest, Optimal

# Extract zip
Expand-Archive -Path C:\archive.zip -DestinationPath C:\Destination
Expand-Archive -Path C:\archive.zip -DestinationPath C:\Dest -Force

# List zip contents
Add-Type -AssemblyName System.IO.Compression.FileSystem
$zip = [System.IO.Compression.ZipFile]::OpenRead("C:\archive.zip")
$zip.Entries | Select-Object FullName, Length, CompressedLength
$zip.Dispose()

# Extract specific file from zip
$zip = [System.IO.Compression.ZipFile]::OpenRead("C:\archive.zip")
$entry = $zip.Entries | Where-Object {$_.Name -eq "file.txt"}
[System.IO.Compression.ZipFileExtensions]::ExtractToFile($entry, "C:\Dest\file.txt", $true)
$zip.Dispose()

# 7-Zip (if installed)
& "C:\Program Files\7-Zip\7z.exe" a archive.7z C:\Source
& "C:\Program Files\7-Zip\7z.exe" x archive.7z -oC:\Dest

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## 👥 User & Permission Management

</div>

### User Management 👤

```powershell
# ═══════════════════════════════════════════
# CURRENT USER INFORMATION
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   USER INFORMATION                         ║
╚════════════════════════════════════════════════════════════╝

# Username
$env:USERNAME
whoami
[System.Security.Principal.WindowsIdentity]::GetCurrent().Name

# Domain
$env:USERDOMAIN
$env:USERDNSDOMAIN

# Computer name
$env:COMPUTERNAME

# Full identity
whoami /all                           # All info
whoami /user                          # User SID
whoami /groups                        # Group membership
whoami /priv                          # Privileges
whoami /upn                           # User Principal Name

# Current user object
$currentUser = [System.Security.Principal.WindowsIdentity]::GetCurrent()
$currentUser.Name
$currentUser.User.Value               # SID

# Check if admin
$isAdmin = ([Security.Principal.WindowsPrincipal][Security.Principal.WindowsIdentity]::GetCurrent()).IsInRole([Security.Principal.WindowsBuiltInRole]::Administrator)
if ($isAdmin) { Write-Host "Running as Administrator" }

# User profile path
$env:USERPROFILE
$env:APPDATA                          # AppData\Roaming
$env:LOCALAPPDATA                     # AppData\Local
$env:TEMP                             # Temp folder

# ═══════════════════════════════════════════
# LOCAL USERS (Requires Admin)
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   LOCAL USER MANAGEMENT                    ║
╚════════════════════════════════════════════════════════════╝

# List all users
Get-LocalUser
Get-LocalUser | Select-Object Name, Enabled, LastLogon, PasswordLastSet

# Get specific user
Get-LocalUser -Name "username"
Get-LocalUser -SID "S-1-5-21-..."

# User details
Get-LocalUser -Name "username" | Format-List *

# Create new user
$password = ConvertTo-SecureString "P@ssw0rd!" -AsPlainText -Force
New-LocalUser -Name "NewUser" -Password $password -FullName "Full Name" -Description "Description"

# Create user with options
New-LocalUser -Name "NewUser" -Password $password `
    -FullName "Full Name" `
    -Description "User Description" `
    -PasswordNeverExpires `
    -UserMayNotChangePassword `
    -AccountNeverExpires

# Enable user
Enable-LocalUser -Name "username"

# Disable user
Disable-LocalUser -Name "username"

# Remove user
Remove-LocalUser -Name "username"

# Change password
$newPassword = ConvertTo-SecureString "NewP@ss123!" -AsPlainText -Force
Set-LocalUser -Name "username" -Password $newPassword

# Password never expires
Set-LocalUser -Name "username" -PasswordNeverExpires $true

# User must change password at next logon
Set-LocalUser -Name "username" -PasswordNeverExpires $false
# Then use: net user username /logonpasswordchg:yes

# Set account expiration
Set-LocalUser -Name "username" -AccountExpires (Get-Date).AddDays(30)

# Remove account expiration
Set-LocalUser -Name "username" -AccountExpires ([datetime]::MaxValue)

# Rename user
Rename-LocalUser -Name "oldname" -NewName "newname"

# ═══════════════════════════════════════════
# LOCAL GROUPS (Requires Admin)
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   LOCAL GROUP MANAGEMENT                   ║
╚════════════════════════════════════════════════════════════╝

# List all groups
Get-LocalGroup

# Get specific group
Get-LocalGroup -Name "Administrators"

# Get group members
Get-LocalGroupMember -Group "Administrators"
Get-LocalGroupMember -Group "Users"
Get-LocalGroupMember -Group "Remote Desktop Users"

# Create group
New-LocalGroup -Name "GroupName" -Description "Description"

# Add user to group
Add-LocalGroupMember -Group "Administrators" -Member "username"
Add-LocalGroupMember -Group "GroupName" -Member "DOMAIN\User"

# Add multiple users
Add-LocalGroupMember -Group "GroupName" -Member @("user1", "user2", "user3")

# Remove user from group
Remove-LocalGroupMember -Group "GroupName" -Member "username"

# Remove group
Remove-LocalGroup -Name "GroupName"

# Check if user is in group
$members = Get-LocalGroupMember -Group "Administrators"
$members.Name -contains "COMPUTERNAME\username"

# List all groups a user belongs to
$userName = "username"
Get-LocalGroup | Where-Object {
    (Get-LocalGroupMember -Group $_.Name).Name -contains "$env:COMPUTERNAME\$userName"
}

# ═══════════════════════════════════════════
# ACTIVE DIRECTORY USERS (Domain)
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   ACTIVE DIRECTORY USERS                   ║
╚════════════════════════════════════════════════════════════╝

# Import module (RSAT required)
Import-Module ActiveDirectory

# Get AD user
Get-ADUser -Identity username
Get-ADUser -Identity username -Properties *

# Search users
Get-ADUser -Filter "Name -like '*John*'"
Get-ADUser -Filter {Enabled -eq $true}
Get-ADUser -Filter {Department -eq "IT"}

# Get all users
Get-ADUser -Filter * | Select-Object Name, SamAccountName

# User groups
Get-ADPrincipalGroupMembership -Identity username

# Create AD user
New-ADUser -Name "Full Name" `
    -SamAccountName "username" `
    -UserPrincipalName "username@domain.com" `
    -Path "OU=Users,DC=domain,DC=com" `
    -AccountPassword (ConvertTo-SecureString "P@ss123!" -AsPlainText -Force) `
    -Enabled $true

# Disable/Enable user
Disable-ADAccount -Identity username
Enable-ADAccount -Identity username

# Reset password
Set-ADAccountPassword -Identity username -Reset -NewPassword (ConvertTo-SecureString "NewP@ss!" -AsPlainText -Force)

# Unlock account
Unlock-ADAccount -Identity username

═══════════════════════════════════════════════════════════
```

---

### File Permissions 🔐

```powershell
# ═══════════════════════════════════════════
# VIEW PERMISSIONS
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   VIEW PERMISSIONS                         ║
╚════════════════════════════════════════════════════════════╝

# Get ACL (Access Control List)
Get-Acl C:\Path\To\File
Get-Acl C:\Path\To\Folder

# Detailed view
Get-Acl C:\Path\To\File | Format-List
(Get-Acl C:\Path\To\File).Access

# Owner information
(Get-Acl C:\Path\To\File).Owner

# View specific properties
$acl = Get-Acl C:\Path\To\File
$acl.Owner
$acl.Group
$acl.Access | Format-Table IdentityReference, FileSystemRights, AccessControlType

# Check if inherited
(Get-Acl C:\Path\To\File).Access |
    Select-Object IdentityReference, FileSystemRights, IsInherited

# List all permissions recursively
Get-ChildItem C:\Path -Recurse | ForEach-Object {
    $path = $_.FullName
    $acl = Get-Acl $path
    foreach ($access in $acl.Access) {
        [PSCustomObject]@{
            Path = $path
            User = $access.IdentityReference
            Rights = $access.FileSystemRights
            Type = $access.AccessControlType
        }
    }
}

# ═══════════════════════════════════════════
# SET PERMISSIONS
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   SET PERMISSIONS                          ║
╚════════════════════════════════════════════════════════════╝

# Grant full control
$acl = Get-Acl C:\Path\To\File
$permission = "DOMAIN\User", "FullControl", "Allow"
$accessRule = New-Object System.Security.AccessControl.FileSystemAccessRule $permission
$acl.SetAccessRule($accessRule)
Set-Acl C:\Path\To\File $acl

# Grant read permission
$acl = Get-Acl C:\Path\To\Folder
$permission = "DOMAIN\User", "Read", "ContainerInherit, ObjectInherit", "None", "Allow"
$accessRule = New-Object System.Security.AccessControl.FileSystemAccessRule $permission
$acl.SetAccessRule($accessRule)
Set-Acl C:\Path\To\Folder $acl

# Grant modify permission
$acl = Get-Acl C:\Path\To\Folder
$permission = "DOMAIN\User", "Modify", "ContainerInherit, ObjectInherit", "None", "Allow"
$accessRule = New-Object System.Security.AccessControl.FileSystemAccessRule $permission
$acl.SetAccessRule($accessRule)
Set-Acl C:\Path\To\Folder $acl

# Remove permission
$acl = Get-Acl C:\Path\To\File
$permission = "DOMAIN\User", "FullControl", "Allow"
$accessRule = New-Object System.Security.AccessControl.FileSystemAccessRule $permission
$acl.RemoveAccessRule($accessRule)
Set-Acl C:\Path\To\File $acl

# Remove all permissions for user
$acl = Get-Acl C:\Path\To\File
$acl.Access | Where-Object {$_.IdentityReference -eq "DOMAIN\User"} | ForEach-Object {
    $acl.RemoveAccessRule($_) | Out-Null
}
Set-Acl C:\Path\To\File $acl

# Disable inheritance
$acl = Get-Acl C:\Path\To\File
$acl.SetAccessRuleProtection($true, $false)  # Block inheritance, don't copy existing
Set-Acl C:\Path\To\File $acl

# Enable inheritance
$acl = Get-Acl C:\Path\To\File
$acl.SetAccessRuleProtection($false, $true)  # Allow inheritance
Set-Acl C:\Path\To\File $acl

# ═══════════════════════════════════════════
# OWNERSHIP
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   OWNERSHIP MANAGEMENT                     ║
╚════════════════════════════════════════════════════════════╝

# Take ownership (GUI way)
takeown /F C:\Path\To\File
takeown /F C:\Path\To\Folder /R /D Y         # Recursive

# Take ownership (PowerShell way)
$acl = Get-Acl C:\Path\To\File
$user = New-Object System.Security.Principal.NTAccount("DOMAIN\User")
$acl.SetOwner($user)
Set-Acl C:\Path\To\File $acl

# Grant full control using icacls
icacls "C:\Path\To\File" /grant USERNAME:F
icacls "C:\Path\To\Folder" /grant USERNAME:(OI)(CI)F /T
# F = Full control
# OI = Object Inherit
# CI = Container Inherit
# /T = Recursive

# Remove permissions
icacls "C:\Path\To\File" /remove USERNAME

# Reset permissions to defaults
icacls "C:\Path\To\File" /reset /T

# Deny permission
icacls "C:\Path\To\File" /deny USERNAME:F

# ═══════════════════════════════════════════
# EFFECTIVE PERMISSIONS
# ═══════════════════════════════════════════

# Check effective permissions
$acl = Get-Acl C:\Path\To\File
$user = New-Object System.Security.Principal.NTAccount("DOMAIN\User")
$acl.Access | Where-Object {$_.IdentityReference -eq $user}

# Test access
Test-Path C:\Path\To\File -PathType Leaf
# Or try to access and catch error
try {
    Get-Content C:\Path\To\File -ErrorAction Stop
    Write-Host "Access granted"
} catch {
    Write-Host "Access denied"
}

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## 📦 Package Management

</div>

### Chocolatey 🍫

```powershell
# ═══════════════════════════════════════════
# CHOCOLATEY INSTALLATION
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   INSTALL CHOCOLATEY                       ║
╚════════════════════════════════════════════════════════════╝

# Install Chocolatey (run as admin)
Set-ExecutionPolicy Bypass -Scope Process -Force
[System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072
iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))

# Verify installation
choco --version
choco -v

# Update Chocolatey
choco upgrade chocolatey

# ═══════════════════════════════════════════
# CHOCOLATEY COMMANDS
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   CHOCOLATEY USAGE                         ║
╚════════════════════════════════════════════════════════════╝

# Search packages
choco search package
choco find package
choco search --by-tag development

# Install package
choco install package
choco install package -y                # Auto-confirm
choco install package --force           # Force reinstall
choco install package --version 1.2.3   # Specific version

# Install multiple packages
choco install package1 package2 package3 -y

# Uninstall package
choco uninstall package
choco uninstall package -y

# Update package
choco upgrade package
choco upgrade package -y

# Update all packages
choco upgrade all
choco upgrade all -y

# List installed packages
choco list --local-only
choco list -l

# Package information
choco info package

# Pin package (prevent updates)
choco pin add -n=package
choco pin list
choco pin remove -n=package

# ═══════════════════════════════════════════
# COMMON PACKAGES
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   POPULAR PACKAGES                         ║
╚════════════════════════════════════════════════════════════╝

# Browsers
choco install googlechrome -y
choco install firefox -y
choco install brave -y
choco install microsoft-edge -y

# Development tools
choco install vscode -y
choco install git -y
choco install github-desktop -y
choco install postman -y
choco install docker-desktop -y

# Programming languages
choco install nodejs -y
choco install python -y
choco install ruby -y
choco install golang -y
choco install openjdk -y

# Utilities
choco install 7zip -y
choco install vlc -y
choco install notepadplusplus -y
choco install procexp -y
choco install sysinternals -y
choco install everything -y
choco install greenshot -y

# Communication
choco install slack -y
choco install discord -y
choco install zoom -y

# Batch install
$packages = @(
    "googlechrome",
    "vscode",
    "git",
    "nodejs",
    "python",
    "7zip"
)
$packages | ForEach-Object { choco install $_ -y }

═══════════════════════════════════════════════════════════
```

---

### Winget (Windows Package Manager) 📦

```powershell
# ═══════════════════════════════════════════
# WINGET (Built into Windows 10/11)
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   WINGET COMMANDS                          ║
╚════════════════════════════════════════════════════════════╝

# Winget version
winget --version
winget -v

# Search packages
winget search package
winget search "visual studio code"

# Show package details
winget show package
winget show Microsoft.VisualStudioCode

# Install package
winget install package
winget install Microsoft.VisualStudioCode
winget install --id Microsoft.VisualStudioCode
winget install -e --id Microsoft.VisualStudioCode  # Exact match

# Install specific version
winget install Microsoft.VisualStudioCode --version 1.75.0

# Install silently
winget install Microsoft.VisualStudioCode --silent

# Uninstall package
winget uninstall package
winget uninstall Microsoft.VisualStudioCode

# Update package
winget upgrade package
winget upgrade Microsoft.VisualStudioCode

# Update all packages
winget upgrade --all

# List installed packages
winget list
winget list | Select-String "Microsoft"

# Export installed apps
winget export -o packages.json

# Import apps
winget import -i packages.json

# List sources
winget source list

# Update sources
winget source update

# ═══════════════════════════════════════════
# COMMON WINGET PACKAGES
# ═══════════════════════════════════════════

# Development
winget install Microsoft.VisualStudioCode
winget install Git.Git
winget install GitHub.GitHubDesktop
winget install Microsoft.WindowsTerminal
winget install Microsoft.PowerShell

# Browsers
winget install Google.Chrome
winget install Mozilla.Firefox
winget install Brave.Brave

# Utilities
winget install 7zip.7zip
winget install VideoLAN.VLC
winget install Notepad++.Notepad++

# Batch install
$apps = @(
    "Microsoft.VisualStudioCode",
    "Git.Git",
    "Google.Chrome",
    "7zip.7zip"
)
$apps | ForEach-Object { winget install $_ --silent }

═══════════════════════════════════════════════════════════
```

---

### PowerShell Modules 🔌

```powershell
# ═══════════════════════════════════════════
# MODULE MANAGEMENT
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   POWERSHELL MODULES                       ║
╚════════════════════════════════════════════════════════════╝

# List installed modules
Get-Module -ListAvailable
Get-InstalledModule

# Find module online (PowerShell Gallery)
Find-Module -Name ModuleName
Find-Module -Name *Azure*
Find-Module -Tag "Security"

# Install module
Install-Module -Name ModuleName
Install-Module -Name ModuleName -Scope CurrentUser  # No admin needed
Install-Module -Name ModuleName -Force

# Install specific version
Install-Module -Name ModuleName -RequiredVersion 1.2.3

# Update module
Update-Module -Name ModuleName
Update-Module                     # Update all

# Uninstall module
Uninstall-Module -Name ModuleName

# Import module
Import-Module ModuleName

# List imported modules
Get-Module

# Remove module from session
Remove-Module ModuleName

# Module information
Get-Module ModuleName -ListAvailable | Format-List *

# Module path
$env:PSModulePath -split ';'

# Module commands
Get-Command -Module ModuleName

# ═══════════════════════════════════════════
# POPULAR MODULES
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   ESSENTIAL MODULES                        ║
╚════════════════════════════════════════════════════════════╝

# Posh-Git (Git integration)
Install-Module posh-git -Scope CurrentUser
Import-Module posh-git

# PSReadLine (better command line editing)
Install-Module PSReadLine -Scope CurrentUser -Force
Import-Module PSReadLine

# Terminal-Icons (file icons in terminal)
Install-Module -Name Terminal-Icons -Repository PSGallery
Import-Module Terminal-Icons

# Oh-My-Posh (beautiful prompts)
winget install JanDeDobbeleer.OhMyPosh
# Or
Install-Module oh-my-posh -Scope CurrentUser

# PowerShellGet (module management)
Install-Module PowerShellGet -Force

# Az (Azure)
Install-Module -Name Az -Scope CurrentUser

# ImportExcel (Excel without Excel)
Install-Module ImportExcel -Scope CurrentUser

# PSScriptAnalyzer (code analysis)
Install-Module PSScriptAnalyzer -Scope CurrentUser

# ═══════════════════════════════════════════
# MODULE CONFIGURATION
# ═══════════════════════════════════════════

# PSReadLine configuration
Set-PSReadLineOption -EditMode Windows
Set-PSReadLineOption -PredictionSource History
Set-PSReadLineOption -PredictionViewStyle ListView
Set-PSReadLineKeyHandler -Key Tab -Function MenuComplete
Set-PSReadLineKeyHandler -Key UpArrow -Function HistorySearchBackward
Set-PSReadLineKeyHandler -Key DownArrow -Function HistorySearchForward

# PSReadLine colors
Set-PSReadLineOption -Colors @{
    Command = 'Yellow'
    Parameter = 'Green'
    String = 'DarkCyan'
}

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## 🔌 Process & Service Management

</div>

### Process Management 🔄

```powershell
# ═══════════════════════════════════════════
# VIEWING PROCESSES
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   PROCESS OPERATIONS                       ║
╚════════════════════════════════════════════════════════════╝

# List all processes
Get-Process
gps                                # Alias
ps                                 # Alias

# Specific process by name
Get-Process -Name chrome
Get-Process -Name chrome, firefox  # Multiple

# Specific process by ID
Get-Process -Id 1234
Get-Process -Id 1234, 5678

# Sort by CPU
Get-Process | Sort-Object CPU -Descending
Get-Process | Sort-Object CPU -Descending | Select-Object -First 10

# Sort by Memory
Get-Process | Sort-Object WS -Descending
Get-Process | Sort-Object WorkingSet -Descending | Select-Object -First 10

# Custom formatted view
Get-Process | Format-Table Name, Id,
    @{Label="CPU(s)";Expression={$_.CPU};FormatString="N2"},
    @{Label="Memory(MB)";Expression={$_.WS/1MB};FormatString="N2"} -AutoSize

# With company info
Get-Process | Select-Object Name, Company, Product, ProductVersion

# ═══════════════════════════════════════════
# PROCESS DETAILS
# ═══════════════════════════════════════════

# Full details
Get-Process -Name chrome | Format-List *

# Process path
(Get-Process -Name chrome).Path
(Get-Process -Name chrome).MainModule.FileName

# Process start time
(Get-Process -Name chrome).StartTime

# Process owner
Get-CimInstance Win32_Process |
    Select-Object ProcessId, Name, @{Name="Owner";Expression={$_.GetOwner().User}}

# Process command line
Get-CimInstance Win32_Process |
    Where-Object {$_.Name -eq "chrome.exe"} |
    Select-Object ProcessId, CommandLine

# Process threads
(Get-Process -Name chrome).Threads.Count

# Process handles
(Get-Process -Name chrome).HandleCount

# ═══════════════════════════════════════════
# STARTING & STOPPING PROCESSES
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   START/STOP PROCESSES                     ║
╚════════════════════════════════════════════════════════════╝

# Start process
Start-Process notepad.exe
Start-Process "C:\Path\To\Program.exe"

# Start with arguments
Start-Process notepad.exe -ArgumentList "C:\file.txt"

# Start as administrator
Start-Process powershell -Verb RunAs
Start-Process cmd -Verb RunAs

# Start hidden
Start-Process notepad.exe -WindowStyle Hidden

# Start and wait for exit
Start-Process notepad.exe -Wait

# Start and capture output
$process = Start-Process cmd -ArgumentList "/c dir" -NoNewWindow -PassThru -Wait
$process.ExitCode

# Stop process by name
Stop-Process -Name notepad
Stop-Process -Name chrome -Force

# Stop process by ID
Stop-Process -Id 1234
Stop-Process -Id 1234 -Force

# Kill all instances
Get-Process -Name chrome | Stop-Process -Force

# Stop with confirmation
Stop-Process -Name notepad -Confirm

# ═══════════════════════════════════════════
# MONITORING PROCESSES
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   PROCESS MONITORING                       ║
╚════════════════════════════════════════════════════════════╝

# Monitor CPU usage
while($true) {
    Clear-Host
    Get-Process | Sort-Object CPU -Descending | Select-Object -First 10 Name,
        @{Label="CPU(s)";Expression={$_.CPU};FormatString="N2"},
        @{Label="Memory(MB)";Expression={$_.WS/1MB};FormatString="N2"}
    Start-Sleep -Seconds 2
}

# Monitor specific process
while($true) {
    $proc = Get-Process -Name chrome -ErrorAction SilentlyContinue
    if ($proc) {
        Clear-Host
        $proc | Select-Object Name, CPU, WS | Format-List
    } else {
        Write-Host "Process not running"
    }
    Start-Sleep -Seconds 1
}

# Alert on high CPU
$threshold = 80
$procs = Get-Process | Where-Object {$_.CPU -gt $threshold}
if ($procs) {
    $procs | ForEach-Object {
        Write-Warning "$($_.Name) is using high CPU: $($_.CPU)"
    }
}

# Process performance counters
Get-Counter '\Process(*)\% Processor Time' -SampleInterval 1 -MaxSamples 5

═══════════════════════════════════════════════════════════
```

---

### Service Management ⚙️

```powershell
# ═══════════════════════════════════════════
# VIEWING SERVICES
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   SERVICE OPERATIONS                       ║
╚════════════════════════════════════════════════════════════╝

# List all services
Get-Service
gsv                               # Alias

# Specific service
Get-Service -Name wuauserv        # Windows Update
Get-Service -Name W*              # Wildcard

# Multiple services
Get-Service -Name wuauserv, Spooler

# Running services
Get-Service | Where-Object {$_.Status -eq "Running"}

# Stopped services
Get-Service | Where-Object {$_.Status -eq "Stopped"}

# Search services
Get-Service | Where-Object {$_.Name -like "*update*"}
Get-Service | Where-Object {$_.DisplayName -like "*Windows*"}

# Sort services
Get-Service | Sort-Object Status, DisplayName

# Format output
Get-Service | Format-Table Name, DisplayName, Status -AutoSize

# ═══════════════════════════════════════════
# SERVICE CONTROL (Requires Admin)
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   SERVICE CONTROL                          ║
╚════════════════════════════════════════════════════════════╝

# Start service
Start-Service -Name wuauserv

# Stop service
Stop-Service -Name wuauserv

# Restart service
Restart-Service -Name wuauserv

# Suspend service
Suspend-Service -Name ServiceName

# Resume service
Resume-Service -Name ServiceName

# Stop with dependencies
Stop-Service -Name ServiceName -Force

# ═══════════════════════════════════════════
# SERVICE CONFIGURATION
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   SERVICE CONFIGURATION                    ║
╚════════════════════════════════════════════════════════════╝

# Service details
Get-Service -Name wuauserv | Format-List *

# Set startup type
Set-Service -Name ServiceName -StartupType Automatic
Set-Service -Name ServiceName -StartupType Manual
Set-Service -Name ServiceName -StartupType Disabled

# Change service description
Set-Service -Name ServiceName -Description "New description"

# Service dependencies
Get-Service -Name ServiceName | Select-Object -ExpandProperty DependentServices
Get-Service -Name ServiceName | Select-Object -ExpandProperty ServicesDependedOn

# Using WMI for more details
Get-CimInstance Win32_Service |
    Where-Object {$_.Name -eq "wuauserv"} |
    Select-Object Name, DisplayName, StartMode, State, PathName

# Service account
Get-CimInstance Win32_Service |
    Where-Object {$_.Name -eq "wuauserv"} |
    Select-Object Name, StartName

# ═══════════════════════════════════════════
# COMMON SERVICES
# ═══════════════════════════════════════════

# Windows Update
Get-Service wuauserv

# Windows Defender
Get-Service WinDefend

# Print Spooler
Get-Service Spooler

# Remote Desktop
Get-Service TermService

# Windows Firewall
Get-Service mpssvc

# DHCP Client
Get-Service Dhcp

# DNS Client
Get-Service Dnscache

# Windows Time
Get-Service W32Time

# ═══════════════════════════════════════════
# SERVICE MONITORING
# ═══════════════════════════════════════════

# Monitor service status
while($true) {
    $service = Get-Service -Name wuauserv
    Clear-Host
    Write-Host "Service: $($service.DisplayName)"
    Write-Host "Status: $($service.Status)"
    Write-Host "Startup Type: $($service.StartType)"
    Start-Sleep -Seconds 5
}

# Restart service if stopped
$service = Get-Service -Name wuauserv
if ($service.Status -ne "Running") {
    Start-Service -Name wuauserv
    Write-Host "Service started"
}

# Export services list
Get-Service | Export-Csv services.csv -NoTypeInformation

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## 🌐 Networking

</div>

### Network Configuration 🔧

```powershell
# ═══════════════════════════════════════════
# NETWORK INTERFACES
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   NETWORK ADAPTERS                         ║
╚════════════════════════════════════════════════════════════╝

# List all adapters
Get-NetAdapter

# Enabled adapters only
Get-NetAdapter | Where-Object {$_.Status -eq "Up"}

# Adapter details
Get-NetAdapter -Name "Ethernet" | Format-List *

# Physical adapters only
Get-NetAdapter -Physical

# Adapter statistics
Get-NetAdapterStatistics

# Enable/Disable adapter (admin required)
Enable-NetAdapter -Name "Ethernet"
Disable-NetAdapter -Name "Ethernet"

# Rename adapter
Rename-NetAdapter -Name "Ethernet" -NewName "LAN"

# Reset adapter
Restart-NetAdapter -Name "Ethernet"

# ═══════════════════════════════════════════
# IP CONFIGURATION
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   IP CONFIGURATION                         ║
╚════════════════════════════════════════════════════════════╝

# Show IP configuration
Get-NetIPAddress

# Traditional ipconfig
ipconfig
ipconfig /all

# IPv4 addresses only
Get-NetIPAddress -AddressFamily IPv4

# IPv6 addresses
Get-NetIPAddress -AddressFamily IPv6

# Specific adapter
Get-NetIPAddress -InterfaceAlias "Ethernet"

# Set static IP (admin required)
New-NetIPAddress -InterfaceAlias "Ethernet" `
    -IPAddress 192.168.1.100 `
    -PrefixLength 24 `
    -DefaultGateway 192.168.1.1

# Remove IP address
Remove-NetIPAddress -IPAddress 192.168.1.100 -Confirm:$false

# Set DHCP
Set-NetIPInterface -InterfaceAlias "Ethernet" -Dhcp Enabled
Remove-NetIPAddress -InterfaceAlias "Ethernet" -Confirm:$false
Remove-NetRoute -InterfaceAlias "Ethernet" -Confirm:$false

# Release/Renew IP
ipconfig /release
ipconfig /renew

# ═══════════════════════════════════════════
# DNS CONFIGURATION
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   DNS CONFIGURATION                        ║
╚════════════════════════════════════════════════════════════╝

# Get DNS servers
Get-DnsClientServerAddress

# Specific adapter
Get-DnsClientServerAddress -InterfaceAlias "Ethernet"

# Set DNS servers
Set-DnsClientServerAddress -InterfaceAlias "Ethernet" `
    -ServerAddresses ("8.8.8.8", "8.8.4.4")

# Set single DNS server
Set-DnsClientServerAddress -InterfaceAlias "Ethernet" `
    -ServerAddresses "1.1.1.1"

# Reset to DHCP DNS
Set-DnsClientServerAddress -InterfaceAlias "Ethernet" -ResetServerAddresses

# Clear DNS cache
Clear-DnsClientCache
ipconfig /flushdns

# View DNS cache
Get-DnsClientCache

# Register DNS
ipconfig /registerdns

# DNS client global settings
Get-DnsClient

# ═══════════════════════════════════════════
# ROUTING
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   ROUTING TABLE                            ║
╚════════════════════════════════════════════════════════════╝

# Show routing table
Get-NetRoute

# Traditional route print
route print

# IPv4 routes
Get-NetRoute -AddressFamily IPv4

# Default gateway
Get-NetRoute -DestinationPrefix 0.0.0.0/0

# Add static route
New-NetRoute -DestinationPrefix "10.0.0.0/8" `
    -InterfaceAlias "Ethernet" `
    -NextHop 192.168.1.1

# Remove route
Remove-NetRoute -DestinationPrefix "10.0.0.0/8" -Confirm:$false

# Change default gateway
Remove-NetRoute -DestinationPrefix 0.0.0.0/0 -Confirm:$false
New-NetRoute -DestinationPrefix 0.0.0.0/0 `
    -InterfaceAlias "Ethernet" `
    -NextHop 192.168.1.1

═══════════════════════════════════════════════════════════
```

---

### Network Testing 🧪

```powershell
# ═══════════════════════════════════════════
# CONNECTIVITY TESTING
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   CONNECTIVITY TESTS                       ║
╚════════════════════════════════════════════════════════════╝

# Ping
Test-Connection google.com
Test-Connection google.com -Count 4
Test-Connection google.com -Count 1 -Quiet   # Returns $true/$false
ping google.com

# Continuous ping
Test-Connection google.com -Continuous
ping -t google.com

# Ping with specific source
Test-Connection google.com -Source COMPUTERNAME

# Ping multiple hosts
Test-Connection google.com, 8.8.8.8, cloudflare.com

# Traceroute
Test-NetConnection google.com -TraceRoute
tracert google.com

# Advanced connectivity test
Test-NetConnection google.com
Test-NetConnection google.com -Port 80
Test-NetConnection google.com -Port 443
Test-NetConnection google.com -InformationLevel Detailed

# ═══════════════════════════════════════════
# PORT & SERVICE TESTING
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   PORT SCANNING                            ║
╚════════════════════════════════════════════════════════════╝

# Test specific port
Test-NetConnection google.com -Port 80
Test-NetConnection google.com -Port 443

# Test if port is open (faster method)
$client = New-Object System.Net.Sockets.TcpClient
try {
    $client.Connect("google.com", 80)
    Write-Host "Port 80 is open"
} catch {
    Write-Host "Port 80 is closed"
} finally {
    $client.Close()
}

# Scan range of ports
1..1024 | ForEach-Object {
    $port = $_
    $client = New-Object System.Net.Sockets.TcpClient
    try {
        $client.Connect("localhost", $port)
        Write-Host "Port $port is open"
        $client.Close()
    } catch {
        # Port closed
    }
}

# Check local listening ports
Get-NetTCPConnection -State Listen

# All TCP connections
Get-NetTCPConnection

# Connections by state
Get-NetTCPConnection -State Established
Get-NetTCPConnection -State TimeWait

# Connections by port
Get-NetTCPConnection -LocalPort 80
Get-NetTCPConnection -RemotePort 443

# netstat equivalents
netstat -ano                              # All connections
netstat -ano | findstr "LISTENING"       # Listening ports
netstat -ano | findstr "ESTABLISHED"     # Established connections

# Find process using port
Get-NetTCPConnection -LocalPort 80 | Select-Object OwningProcess
Get-Process -Id (Get-NetTCPConnection -LocalPort 80).OwningProcess

# ═══════════════════════════════════════════
# DNS TESTING
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   DNS TESTING                              ║
╚════════════════════════════════════════════════════════════╝

# DNS lookup
Resolve-DnsName google.com
nslookup google.com

# Specific DNS server
Resolve-DnsName google.com -Server 8.8.8.8

# Specific record type
Resolve-DnsName google.com -Type A          # IPv4
Resolve-DnsName google.com -Type AAAA       # IPv6
Resolve-DnsName google.com -Type MX         # Mail servers
Resolve-DnsName google.com -Type NS         # Name servers
Resolve-DnsName google.com -Type TXT        # TXT records
Resolve-DnsName google.com -Type CNAME      # Canonical name

# Reverse DNS lookup
Resolve-DnsName 8.8.8.8

# ═══════════════════════════════════════════
# DOWNLOAD FILES
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   FILE DOWNLOADS                           ║
╚════════════════════════════════════════════════════════════╝

# Download file
Invoke-WebRequest -Uri "https://example.com/file.zip" -OutFile "file.zip"

# Aliases
wget "https://example.com/file.zip" -OutFile "file.zip"
curl "https://example.com/file.zip" -OutFile "file.zip"

# Download with progress
$ProgressPreference = 'Continue'
Invoke-WebRequest -Uri "URL" -OutFile "file.zip"

# Download without progress (faster)
$ProgressPreference = 'SilentlyContinue'
Invoke-WebRequest -Uri "URL" -OutFile "file.zip"

# Download and execute
Invoke-Expression (Invoke-WebRequest -Uri "URL" -UseBasicParsing).Content

# Get web page content
$response = Invoke-WebRequest -Uri "https://example.com"
$response.Content
$response.StatusCode
$response.Headers

# REST API request
Invoke-RestMethod -Uri "https://api.github.com/users/username"

# POST request
$body = @{
    name = "John"
    email = "john@example.com"
} | ConvertTo-Json

Invoke-RestMethod -Uri "https://api.example.com/users" `
    -Method Post `
    -Body $body `
    -ContentType "application/json"

# ═══════════════════════════════════════════
# FIREWALL
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   WINDOWS FIREWALL                         ║
╚════════════════════════════════════════════════════════════╝

# Firewall status
Get-NetFirewallProfile

# Firewall profile settings
Get-NetFirewallProfile -Profile Domain, Public, Private

# Enable firewall (admin)
Set-NetFirewallProfile -Profile Domain, Public, Private -Enabled True

# Disable firewall (admin)
Set-NetFirewallProfile -Profile Domain, Public, Private -Enabled False

# List firewall rules
Get-NetFirewallRule

# Enabled rules only
Get-NetFirewallRule | Where-Object {$_.Enabled -eq $true}

# Search rules
Get-NetFirewallRule | Where-Object {$_.DisplayName -like "*Remote*"}

# Add firewall rule (admin)
New-NetFirewallRule -DisplayName "Allow Port 80" `
    -Direction Inbound `
    -LocalPort 80 `
    -Protocol TCP `
    -Action Allow

# Remove firewall rule
Remove-NetFirewallRule -DisplayName "Allow Port 80"

# Block IP address
New-NetFirewallRule -DisplayName "Block IP" `
    -Direction Inbound `
    -RemoteAddress 192.168.1.100 `
    -Action Block

# Allow program
New-NetFirewallRule -DisplayName "Allow Program" `
    -Direction Inbound `
    -Program "C:\Path\To\Program.exe" `
    -Action Allow

# Disable rule
Disable-NetFirewallRule -DisplayName "Rule Name"

# Enable rule
Enable-NetFirewallRule -DisplayName "Rule Name"

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## 🗃️ Registry Operations

</div>

### Registry Management 📋

```powershell
# ═══════════════════════════════════════════
# REGISTRY BASICS
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   REGISTRY NAVIGATION                      ║
╚════════════════════════════════════════════════════════════╝

# Registry drives (providers)
Get-PSDrive -PSProvider Registry

# Navigate registry
Set-Location HKLM:
Set-Location HKCU:
cd HKLM:\SOFTWARE
cd HKCU:\Software

# List registry keys
Get-ChildItem HKLM:\SOFTWARE
Get-ChildItem HKCU:\Software\Microsoft

# List registry values
Get-ItemProperty HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion

# Registry hives:
# HKEY_CLASSES_ROOT   (HKCR:)
# HKEY_CURRENT_USER   (HKCU:)
# HKEY_LOCAL_MACHINE  (HKLM:)
# HKEY_USERS          (HKU:)
# HKEY_CURRENT_CONFIG (HKCC:)

# ═══════════════════════════════════════════
# READING REGISTRY
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   READ REGISTRY                            ║
╚════════════════════════════════════════════════════════════╝

# Get registry value
Get-ItemProperty -Path "HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion" -Name "ProgramFilesDir"

# Get specific property
(Get-ItemProperty -Path "HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion").ProgramFilesDir

# Get all properties
Get-ItemProperty -Path "HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion"

# Check if key exists
Test-Path "HKLM:\SOFTWARE\MyApp"

# Check if value exists
$key = Get-ItemProperty -Path "HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion"
$key.PSObject.Properties.Name -contains "ProgramFilesDir"

# Get registry key
Get-Item "HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion"

# Registry value types
$value = Get-ItemProperty -Path "HKLM:\SOFTWARE\MyApp" -Name "Setting"
$value.GetType().Name

# ═══════════════════════════════════════════
# WRITING REGISTRY
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   WRITE REGISTRY                           ║
╚════════════════════════════════════════════════════════════╝

# Create registry key
New-Item -Path "HKLM:\SOFTWARE\MyApp" -Force

# Create nested keys
New-Item -Path "HKLM:\SOFTWARE\MyApp\Settings\Advanced" -Force

# Set registry value (String)
Set-ItemProperty -Path "HKLM:\SOFTWARE\MyApp" -Name "AppName" -Value "My Application"

# Create new value
New-ItemProperty -Path "HKLM:\SOFTWARE\MyApp" -Name "Version" -Value "1.0" -PropertyType String

# Different value types
New-ItemProperty -Path "HKLM:\SOFTWARE\MyApp" -Name "Enabled" -Value 1 -PropertyType DWord
New-ItemProperty -Path "HKLM:\SOFTWARE\MyApp" -Name "Count" -Value 100 -PropertyType DWord
New-ItemProperty -Path "HKLM:\SOFTWARE\MyApp" -Name "Path" -Value "C:\Path" -PropertyType String
New-ItemProperty -Path "HKLM:\SOFTWARE\MyApp" -Name "Paths" -Value @("C:\Path1", "C:\Path2") -PropertyType MultiString
New-ItemProperty -Path "HKLM:\SOFTWARE\MyApp" -Name "Data" -Value ([byte[]](0x01,0x02,0x03)) -PropertyType Binary

# Registry value types:
# String       - REG_SZ
# ExpandString - REG_EXPAND_SZ (contains environment variables)
# Binary       - REG_BINARY
# DWord        - REG_DWORD (32-bit number)
# MultiString  - REG_MULTI_SZ (array of strings)
# QWord        - REG_QWORD (64-bit number)

# Rename registry value
Rename-ItemProperty -Path "HKLM:\SOFTWARE\MyApp" -Name "OldName" -NewName "NewName"

# Copy registry key
Copy-Item -Path "HKLM:\SOFTWARE\MyApp" -Destination "HKLM:\SOFTWARE\MyAppBackup" -Recurse

# Move registry key
Move-Item -Path "HKLM:\SOFTWARE\MyApp" -Destination "HKLM:\SOFTWARE\MyNewApp"

# ═══════════════════════════════════════════
# DELETING REGISTRY
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   DELETE REGISTRY                          ║
╚════════════════════════════════════════════════════════════╝

# Delete registry value
Remove-ItemProperty -Path "HKLM:\SOFTWARE\MyApp" -Name "Setting"

# Delete registry key
Remove-Item -Path "HKLM:\SOFTWARE\MyApp"

# Delete registry key and all subkeys
Remove-Item -Path "HKLM:\SOFTWARE\MyApp" -Recurse

# Delete with confirmation
Remove-Item -Path "HKLM:\SOFTWARE\MyApp" -Confirm

# ═══════════════════════════════════════════
# REGISTRY BACKUPS
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   BACKUP & RESTORE                         ║
╚════════════════════════════════════════════════════════════╝

# Export registry key
reg export "HKLM\SOFTWARE\MyApp" "C:\Backup\myapp.reg"

# Import registry file
reg import "C:\Backup\myapp.reg"

# Export using PowerShell
$key = Get-Item "HKLM:\SOFTWARE\MyApp"
$key | Export-Clixml "C:\Backup\myapp.xml"

# Import using PowerShell
$key = Import-Clixml "C:\Backup\myapp.xml"

# ═══════════════════════════════════════════
# COMMON REGISTRY LOCATIONS
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   USEFUL REGISTRY PATHS                    ║
╚════════════════════════════════════════════════════════════╝

# Windows version
Get-ItemProperty "HKLM:\SOFTWARE\Microsoft\Windows NT\CurrentVersion"

# Installed programs
Get-ItemProperty "HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall\*"
Get-ItemProperty "HKLM:\SOFTWARE\Wow6432Node\Microsoft\Windows\CurrentVersion\Uninstall\*"

# Startup programs
Get-ItemProperty "HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Run"
Get-ItemProperty "HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion\Run"

# Environment variables
Get-ItemProperty "HKLM:\SYSTEM\CurrentControlSet\Control\Session Manager\Environment"
Get-ItemProperty "HKCU:\Environment"

# Windows Update settings
Get-ItemProperty "HKLM:\SOFTWARE\Policies\Microsoft\Windows\WindowsUpdate"

# File associations
Get-ItemProperty "HKCR:\.txt"

# Network settings
Get-ItemProperty "HKLM:\SYSTEM\CurrentControlSet\Services\Tcpip\Parameters"

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## ⏰ Scheduled Tasks

</div>

### Task Scheduler Management 📅

```powershell
# ═══════════════════════════════════════════
# VIEWING SCHEDULED TASKS
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   VIEW SCHEDULED TASKS                     ║
╚════════════════════════════════════════════════════════════╝

# List all scheduled tasks
Get-ScheduledTask

# Running tasks only
Get-ScheduledTask | Where-Object {$_.State -eq "Running"}

# Ready tasks
Get-ScheduledTask | Where-Object {$_.State -eq "Ready"}

# Disabled tasks
Get-ScheduledTask | Where-Object {$_.State -eq "Disabled"}

# Specific task
Get-ScheduledTask -TaskName "TaskName"

# Tasks in specific folder
Get-ScheduledTask -TaskPath "\Microsoft\Windows\*"

# Task details
Get-ScheduledTask -TaskName "TaskName" | Format-List *

# Task info
Get-ScheduledTaskInfo -TaskName "TaskName"

# Last run time
(Get-ScheduledTaskInfo -TaskName "TaskName").LastRunTime

# Next run time
(Get-ScheduledTaskInfo -TaskName "TaskName").NextRunTime

# ═══════════════════════════════════════════
# CREATING SCHEDULED TASKS
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   CREATE SCHEDULED TASKS                   ║
╚════════════════════════════════════════════════════════════╝

# Simple task - Run daily at 9 AM
$action = New-ScheduledTaskAction -Execute "PowerShell.exe" -Argument "-File C:\Scripts\backup.ps1"
$trigger = New-ScheduledTaskTrigger -Daily -At 9am
Register-ScheduledTask -TaskName "DailyBackup" -Action $action -Trigger $trigger -Description "Daily backup script"

# Run weekly on Monday at 6 PM
$action = New-ScheduledTaskAction -Execute "PowerShell.exe" -Argument "-File C:\Scripts\weekly.ps1"
$trigger = New-ScheduledTaskTrigger -Weekly -DaysOfWeek Monday -At 6pm
Register-ScheduledTask -TaskName "WeeklyTask" -Action $action -Trigger $trigger

# Run at startup
$action = New-ScheduledTaskAction -Execute "C:\Program.exe"
$trigger = New-ScheduledTaskTrigger -AtStartup
Register-ScheduledTask -TaskName "StartupTask" -Action $action -Trigger $trigger

# Run at logon
$action = New-ScheduledTaskAction -Execute "PowerShell.exe" -Argument "-File C:\Scripts\logon.ps1"
$trigger = New-ScheduledTaskTrigger -AtLogOn
Register-ScheduledTask -TaskName "LogonTask" -Action $action -Trigger $trigger

# Run hourly
$action = New-ScheduledTaskAction -Execute "PowerShell.exe" -Argument "-File C:\Scripts\hourly.ps1"
$trigger = New-ScheduledTaskTrigger -Once -At (Get-Date) -RepetitionInterval (New-TimeSpan -Hours 1) -RepetitionDuration ([TimeSpan]::MaxValue)
Register-ScheduledTask -TaskName "HourlyTask" -Action $action -Trigger $trigger

# Run every 5 minutes
$action = New-ScheduledTaskAction -Execute "PowerShell.exe" -Argument "-File C:\Scripts\monitor.ps1"
$trigger = New-ScheduledTaskTrigger -Once -At (Get-Date) -RepetitionInterval (New-TimeSpan -Minutes 5) -RepetitionDuration ([TimeSpan]::MaxValue)
Register-ScheduledTask -TaskName "Monitor" -Action $action -Trigger $trigger

# Run as SYSTEM
$action = New-ScheduledTaskAction -Execute "PowerShell.exe" -Argument "-File C:\Scripts\system.ps1"
$trigger = New-ScheduledTaskTrigger -Daily -At 9am
$principal = New-ScheduledTaskPrincipal -UserId "NT AUTHORITY\SYSTEM" -LogonType ServiceAccount -RunLevel Highest
Register-ScheduledTask -TaskName "SystemTask" -Action $action -Trigger $trigger -Principal $principal

# Run with specific user
$action = New-ScheduledTaskAction -Execute "PowerShell.exe" -Argument "-File C:\Scripts\user.ps1"
$trigger = New-ScheduledTaskTrigger -Daily -At 9am
$principal = New-ScheduledTaskPrincipal -UserId "DOMAIN\Username" -LogonType Password -RunLevel Highest
Register-ScheduledTask -TaskName "UserTask" -Action $action -Trigger $trigger -Principal $principal

# Multiple triggers
$action = New-ScheduledTaskAction -Execute "PowerShell.exe" -Argument "-File C:\Scripts\script.ps1"
$trigger1 = New-ScheduledTaskTrigger -Daily -At 9am
$trigger2 = New-ScheduledTaskTrigger -Daily -At 6pm
Register-ScheduledTask -TaskName "MultiTrigger" -Action $action -Trigger $trigger1, $trigger2

# Task with conditions
$action = New-ScheduledTaskAction -Execute "PowerShell.exe" -Argument "-File C:\Scripts\script.ps1"
$trigger = New-ScheduledTaskTrigger -Daily -At 9am
$settings = New-ScheduledTaskSettingsSet -AllowStartIfOnBatteries -DontStopIfGoingOnBatteries -StartWhenAvailable
Register-ScheduledTask -TaskName "ConditionalTask" -Action $action -Trigger $trigger -Settings $settings

# ═══════════════════════════════════════════
# MANAGING SCHEDULED TASKS
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   MANAGE SCHEDULED TASKS                   ║
╚════════════════════════════════════════════════════════════╝

# Start task immediately
Start-ScheduledTask -TaskName "TaskName"

# Stop running task
Stop-ScheduledTask -TaskName "TaskName"

# Enable task
Enable-ScheduledTask -TaskName "TaskName"

# Disable task
Disable-ScheduledTask -TaskName "TaskName"

# Unregister (delete) task
Unregister-ScheduledTask -TaskName "TaskName" -Confirm:$false

# Export task to XML
Export-ScheduledTask -TaskName "TaskName" | Out-File "C:\Backup\task.xml"

# Import task from XML
Register-ScheduledTask -Xml (Get-Content "C:\Backup\task.xml" | Out-String) -TaskName "ImportedTask"

# Modify existing task
$task = Get-ScheduledTask -TaskName "TaskName"
$task.Description = "Updated description"
$task | Set-ScheduledTask

# Change trigger
$task = Get-ScheduledTask -TaskName "TaskName"
$newtrigger = New-ScheduledTaskTrigger -Daily -At 10am
Set-ScheduledTask -TaskName "TaskName" -Trigger $newtrigger

# ═══════════════════════════════════════════
# TASK HISTORY & LOGS
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   TASK HISTORY                             ║
╚════════════════════════════════════════════════════════════╝

# Get task history (from Event Log)
Get-WinEvent -LogName "Microsoft-Windows-TaskScheduler/Operational" |
    Where-Object {$_.Message -like "*TaskName*"} |
    Select-Object TimeCreated, Id, LevelDisplayName, Message

# Last 10 task events
Get-WinEvent -LogName "Microsoft-Windows-TaskScheduler/Operational" -MaxEvents 10

# Task execution results
Get-ScheduledTask | ForEach-Object {
    $info = Get-ScheduledTaskInfo -TaskName $_.TaskName
    [PSCustomObject]@{
        TaskName = $_.TaskName
        LastRunTime = $info.LastRunTime
        LastTaskResult = $info.LastTaskResult
        NextRunTime = $info.NextRunTime
        State = $_.State
    }
} | Format-Table -AutoSize

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## 💻 System Administration

</div>

### System Information & Management 🖥️

```powershell
# ═══════════════════════════════════════════
# SYSTEM INFORMATION
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   SYSTEM INFORMATION                       ║
╚════════════════════════════════════════════════════════════╝

# Computer info (comprehensive but slow)
Get-ComputerInfo

# Quick system info
systeminfo

# OS information
Get-CimInstance Win32_OperatingSystem |
    Select-Object Caption, Version, BuildNumber, OSArchitecture, InstallDate, LastBootUpTime

# Windows version
[System.Environment]::OSVersion.Version
(Get-ItemProperty "HKLM:\SOFTWARE\Microsoft\Windows NT\CurrentVersion").ProductName
(Get-ItemProperty "HKLM:\SOFTWARE\Microsoft\Windows NT\CurrentVersion").ReleaseId

# Computer name
$env:COMPUTERNAME
hostname
[System.Net.Dns]::GetHostName()

# BIOS information
Get-CimInstance Win32_BIOS

# System manufacturer and model
Get-CimInstance Win32_ComputerSystem |
    Select-Object Manufacturer, Model, TotalPhysicalMemory

# Processor information
Get-CimInstance Win32_Processor |
    Select-Object Name, NumberOfCores, NumberOfLogicalProcessors, MaxClockSpeed

# Memory information
Get-CimInstance Win32_PhysicalMemory |
    Select-Object BankLabel, Capacity, Speed, Manufacturer

# Total RAM
$os = Get-CimInstance Win32_OperatingSystem
$totalRAM = [math]::Round($os.TotalVisibleMemorySize / 1MB, 2)
$freeRAM = [math]::Round($os.FreePhysicalMemory / 1MB, 2)
Write-Host "Total RAM: $totalRAM GB"
Write-Host "Free RAM: $freeRAM GB"

# ═══════════════════════════════════════════
# DISK INFORMATION
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   DISK MANAGEMENT                          ║
╚════════════════════════════════════════════════════════════╝

# Disk space
Get-PSDrive -PSProvider FileSystem

# Disk details
Get-Disk

# Disk with free space
Get-Volume

# Detailed disk info
Get-CimInstance Win32_LogicalDisk |
    Select-Object DeviceID,
        @{Name="Size(GB)";Expression={[math]::Round($_.Size/1GB, 2)}},
        @{Name="FreeSpace(GB)";Expression={[math]::Round($_.FreeSpace/1GB, 2)}},
        @{Name="PercentFree";Expression={[math]::Round(($_.FreeSpace/$_.Size)*100, 2)}}

# Partition information
Get-Partition

# Physical disks
Get-PhysicalDisk

# Disk health
Get-PhysicalDisk | Select-Object FriendlyName, HealthStatus, OperationalStatus

# SMART status
Get-StorageReliabilityCounter -PhysicalDisk (Get-PhysicalDisk)

# ═══════════════════════════════════════════
# POWER MANAGEMENT
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   POWER MANAGEMENT                         ║
╚════════════════════════════════════════════════════════════╝

# Shutdown computer
Stop-Computer
Stop-Computer -Force

# Restart computer
Restart-Computer
Restart-Computer -Force

# Log off
logoff
shutdown /l

# Hibernate
shutdown /h

# Sleep
rundll32.exe powrprof.dll,SetSuspendState 0,1,0

# Lock computer
rundll32.exe user32.dll,LockWorkStation

# Power plan
powercfg /list
powercfg /getactivescheme

# Set power plan
powercfg /setactive SCHEME_GUID

# Battery status
Get-CimInstance Win32_Battery |
    Select-Object BatteryStatus, EstimatedChargeRemaining, EstimatedRunTime

# ═══════════════════════════════════════════
# WINDOWS UPDATE
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   WINDOWS UPDATE                           ║
╚════════════════════════════════════════════════════════════╝

# Install PSWindowsUpdate module
Install-Module PSWindowsUpdate -Force

# Check for updates
Get-WindowsUpdate

# Install all updates
Install-WindowsUpdate -AcceptAll -AutoReboot

# Install updates without reboot
Install-WindowsUpdate -AcceptAll -IgnoreReboot

# Update history
Get-WindowsUpdate -History

# Uninstall update
Uninstall-WindowsUpdate -KBArticleID "KB5000000"

# Hide update
Hide-WindowsUpdate -KBArticleID "KB5000000"

# Traditional Windows Update commands
# Check for updates
UsoClient StartScan

# Download updates
UsoClient StartDownload

# Install updates
UsoClient StartInstall

# ═══════════════════════════════════════════
# WINDOWS FEATURES
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   WINDOWS FEATURES                         ║
╚════════════════════════════════════════════════════════════╝

# List Windows features
Get-WindowsOptionalFeature -Online

# Enabled features
Get-WindowsOptionalFeature -Online |
    Where-Object {$_.State -eq "Enabled"}

# Enable feature
Enable-WindowsOptionalFeature -Online -FeatureName "TelnetClient" -NoRestart

# Disable feature
Disable-WindowsOptionalFeature -Online -FeatureName "TelnetClient" -NoRestart

# Enable WSL
Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux

# Enable Hyper-V
Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Hyper-V -All

# DISM commands
dism /online /get-features
dism /online /enable-feature /featurename:TelnetClient

# ═══════════════════════════════════════════
# EVENT LOGS
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   EVENT LOGS                               ║
╚════════════════════════════════════════════════════════════╝

# List event logs
Get-EventLog -List

# Get System event log
Get-EventLog -LogName System -Newest 100

# Get Application event log
Get-EventLog -LogName Application -Newest 100

# Filter by entry type
Get-EventLog -LogName System -EntryType Error -Newest 50
Get-EventLog -LogName System -EntryType Warning -Newest 50

# Filter by source
Get-EventLog -LogName System -Source "Service Control Manager"

# Get events from specific time
Get-EventLog -LogName System -After (Get-Date).AddDays(-7)

# Using Get-WinEvent (newer, faster)
Get-WinEvent -LogName System -MaxEvents 100

# Filter WinEvent
Get-WinEvent -FilterHashtable @{
    LogName = 'System'
    Level = 2  # Error
    StartTime = (Get-Date).AddDays(-7)
}

# Event log levels:
# 1 - Critical
# 2 - Error
# 3 - Warning
# 4 - Information
# 5 - Verbose

# Export event log
Get-EventLog -LogName System | Export-Csv "system-events.csv" -NoTypeInformation

# Clear event log
Clear-EventLog -LogName System

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## 🔐 Security & Encryption

</div>

### Security Operations 🛡️

```powershell
# ═══════════════════════════════════════════
# USER ACCOUNT CONTROL (UAC)
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   UAC & ELEVATION                          ║
╚════════════════════════════════════════════════════════════╝

# Check if running as admin
$isAdmin = ([Security.Principal.WindowsPrincipal][Security.Principal.WindowsIdentity]::GetCurrent()).IsInRole([Security.Principal.WindowsBuiltInRole]::Administrator)

# Restart script as admin
if (-not $isAdmin) {
    Start-Process powershell.exe "-NoProfile -ExecutionPolicy Bypass -File `"$PSCommandPath`"" -Verb RunAs
    exit
}

# Run command as different user
Start-Process powershell -Credential (Get-Credential) -ArgumentList "-Command Get-Process"

# ═══════════════════════════════════════════
# WINDOWS DEFENDER
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   WINDOWS DEFENDER                         ║
╚════════════════════════════════════════════════════════════╝

# Defender status
Get-MpComputerStatus

# Scan for threats
Start-MpScan -ScanType QuickScan
Start-MpScan -ScanType FullScan
Start-MpScan -ScanType CustomScan -ScanPath "C:\Path"

# Update definitions
Update-MpSignature

# Get threat catalog
Get-MpThreatCatalog

# Get threat detections
Get-MpThreat

# Remove threat
Remove-MpThreat

# Exclusions
Add-MpPreference -ExclusionPath "C:\Path\To\Exclude"
Add-MpPreference -ExclusionExtension ".tmp"
Add-MpPreference -ExclusionProcess "process.exe"

# Remove exclusions
Remove-MpPreference -ExclusionPath "C:\Path\To\Exclude"

# Get exclusions
Get-MpPreference | Select-Object Exclusion*

# Real-time protection
Set-MpPreference -DisableRealtimeMonitoring $true   # Disable
Set-MpPreference -DisableRealtimeMonitoring $false  # Enable

# ═══════════════════════════════════════════
# BITLOCKER ENCRYPTION
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   BITLOCKER                                ║
╚════════════════════════════════════════════════════════════╝

# Check BitLocker status
Get-BitLockerVolume

# Enable BitLocker
Enable-BitLocker -MountPoint "C:" -EncryptionMethod XtsAes256 -RecoveryPasswordProtector

# Disable BitLocker
Disable-BitLocker -MountPoint "C:"

# Unlock BitLocker volume
Unlock-BitLocker -MountPoint "E:" -Password (ConvertTo-SecureString "password" -AsPlainText -Force)

# Suspend BitLocker (for updates)
Suspend-BitLocker -MountPoint "C:" -RebootCount 1

# Resume BitLocker
Resume-BitLocker -MountPoint "C:"

# Backup recovery key
BackupToAAD-BitLockerKeyProtector -MountPoint "C:" -KeyProtectorId "{ID}"

# ═══════════════════════════════════════════
# ENCRYPTION & HASHING
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   ENCRYPTION                               ║
╚════════════════════════════════════════════════════════════╝

# File hash
Get-FileHash file.txt -Algorithm SHA256
Get-FileHash file.txt -Algorithm MD5
Get-FileHash file.txt -Algorithm SHA1

# String hash
$string = "Hello, World!"
$bytes = [System.Text.Encoding]::UTF8.GetBytes($string)
$hash = [System.Security.Cryptography.SHA256]::Create().ComputeHash($bytes)
[BitConverter]::ToString($hash) -replace '-'

# Secure string
$secureString = ConvertTo-SecureString "Password123!" -AsPlainText -Force
$encryptedString = $secureString | ConvertFrom-SecureString

# Decrypt secure string
$secureString = ConvertTo-SecureString $encryptedString
$ptr = [System.Runtime.InteropServices.Marshal]::SecureStringToBSTR($secureString)
$plainText = [System.Runtime.InteropServices.Marshal]::PtrToStringAuto($ptr)

# Encrypt file (EFS)
cipher /e /s:"C:\Path\To\Folder"

# Decrypt file
cipher /d /s:"C:\Path\To\Folder"

# ═══════════════════════════════════════════
# CERTIFICATES
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   CERTIFICATES                             ║
╚════════════════════════════════════════════════════════════╝

# List certificates
Get-ChildItem Cert:\CurrentUser\My
Get-ChildItem Cert:\LocalMachine\Root

# Get specific certificate
Get-ChildItem Cert:\CurrentUser\My | Where-Object {$_.Subject -like "*CommonName*"}

# Export certificate
$cert = Get-ChildItem Cert:\CurrentUser\My | Select-Object -First 1
Export-Certificate -Cert $cert -FilePath "C:\cert.cer"

# Import certificate
Import-Certificate -FilePath "C:\cert.cer" -CertStoreLocation Cert:\CurrentUser\My

# Remove certificate
Get-ChildItem Cert:\CurrentUser\My | Where-Object {$_.Subject -like "*OldCert*"} | Remove-Item

# Self-signed certificate
$cert = New-SelfSignedCertificate -DnsName "localhost" -CertStoreLocation Cert:\CurrentUser\My

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## ☁️ Remote Management

</div>

### PowerShell Remoting 🌐

```powershell
# ═══════════════════════════════════════════
# ENABLE REMOTING
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   ENABLE PS REMOTING                       ║
╚════════════════════════════════════════════════════════════╝

# Enable PowerShell Remoting (run as admin on target)
Enable-PSRemoting -Force

# Enable remoting and skip network profile check
Enable-PSRemoting -SkipNetworkProfileCheck -Force

# Disable remoting
Disable-PSRemoting -Force

# Test WinRM service
Test-WSMan
Test-WSMan -ComputerName "RemotePC"

# Configure trusted hosts (for workgroup)
Set-Item WSMan:\localhost\Client\TrustedHosts -Value "RemotePC,192.168.1.100" -Force
Set-Item WSMan:\localhost\Client\TrustedHosts -Value "*" -Force  # All hosts (not recommended)

# View trusted hosts
Get-Item WSMan:\localhost\Client\TrustedHosts

# ═══════════════════════════════════════════
# REMOTE SESSIONS
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   REMOTE SESSIONS                          ║
╚════════════════════════════════════════════════════════════╝

# Enter interactive session
Enter-PSSession -ComputerName "RemotePC"
Enter-PSSession -ComputerName "RemotePC" -Credential (Get-Credential)

# Exit session
Exit-PSSession

# Create persistent session
$session = New-PSSession -ComputerName "RemotePC"
$session = New-PSSession -ComputerName "RemotePC" -Credential (Get-Credential)

# Use session
Enter-PSSession -Session $session

# Run commands in session
Invoke-Command -Session $session -ScriptBlock { Get-Process }

# Close session
Remove-PSSession -Session $session

# Get all sessions
Get-PSSession

# Close all sessions
Get-PSSession | Remove-PSSession

# ═══════════════════════════════════════════
# REMOTE COMMANDS
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   INVOKE COMMANDS                          ║
╚════════════════════════════════════════════════════════════╝

# Run command on remote computer
Invoke-Command -ComputerName "RemotePC" -ScriptBlock { Get-Process }

# Multiple computers
Invoke-Command -ComputerName "PC1", "PC2", "PC3" -ScriptBlock { Get-Service }

# With credentials
$cred = Get-Credential
Invoke-Command -ComputerName "RemotePC" -Credential $cred -ScriptBlock { Get-EventLog -LogName System -Newest 10 }

# Run script on remote computer
Invoke-Command -ComputerName "RemotePC" -FilePath "C:\Scripts\script.ps1"

# Pass parameters
Invoke-Command -ComputerName "RemotePC" -ScriptBlock {
    param($ServiceName)
    Get-Service -Name $ServiceName
} -ArgumentList "wuauserv"

# Run as background job
Invoke-Command -ComputerName "RemotePC" -ScriptBlock { Get-Process } -AsJob

# Get job results
Get-Job | Receive-Job

# ═══════════════════════════════════════════
# FILE COPY
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   REMOTE FILE COPY                         ║
╚════════════════════════════════════════════════════════════╝

# Copy to remote computer
$session = New-PSSession -ComputerName "RemotePC"
Copy-Item -Path "C:\Local\file.txt" -Destination "C:\Remote\" -ToSession $session

# Copy from remote computer
Copy-Item -Path "C:\Remote\file.txt" -Destination "C:\Local\" -FromSession $session

# Copy directory
Copy-Item -Path "C:\Local\Folder" -Destination "C:\Remote\" -ToSession $session -Recurse

# Using UNC path (if shares enabled)
Copy-Item -Path "C:\Local\file.txt" -Destination "\\RemotePC\C$\Remote\"

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## 🎨 Customization & Configuration

</div>

### PowerShell Profile 📋

```powershell
# ═══════════════════════════════════════════
# POWERSHELL PROFILE LOCATIONS
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   PROFILE LOCATIONS                        ║
╚════════════════════════════════════════════════════════════╝

# Check profile path
$PROFILE
$PROFILE | Format-List * -Force

# Profile locations
$PROFILE.CurrentUserCurrentHost    # Current user, current host
$PROFILE.CurrentUserAllHosts       # Current user, all hosts
$PROFILE.AllUsersCurrentHost       # All users, current host
$PROFILE.AllUsersAllHosts         # All users, all hosts

# Typical paths:
# CurrentUserCurrentHost:
#   C:\Users\Username\Documents\PowerShell\Microsoft.PowerShell_profile.ps1 (PowerShell 7+)
#   C:\Users\Username\Documents\WindowsPowerShell\Microsoft.PowerShell_profile.ps1 (Windows PowerShell 5.1)

# Check if profile exists
Test-Path $PROFILE

# Create profile if it doesn't exist
if (!(Test-Path $PROFILE)) {
    New-Item -Path $PROFILE -ItemType File -Force
}

# Edit profile
notepad $PROFILE
code $PROFILE        # VS Code
vim $PROFILE         # Vim

# Reload profile
. $PROFILE

# ═══════════════════════════════════════════
# SAMPLE PROFILE CONFIGURATION
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   PROFILE EXAMPLES                         ║
╚════════════════════════════════════════════════════════════╝

# ─────────────────────────────────────────────────────────────
# Add this to your $PROFILE:
# ─────────────────────────────────────────────────────────────

# Set encoding
[Console]::OutputEncoding = [System.Text.Encoding]::UTF8
$OutputEncoding = [System.Text.Encoding]::UTF8

# Set execution policy for current user
Set-ExecutionPolicy -Scope CurrentUser -ExecutionPolicy RemoteSigned -Force

# ═══════════════════════════════════════════
# CUSTOM PROMPT
# ═══════════════════════════════════════════

# Simple custom prompt
function prompt {
    $path = (Get-Location).Path.Replace($HOME, "~")
    Write-Host "PS " -NoNewline -ForegroundColor Green
    Write-Host $path -NoNewline -ForegroundColor Blue
    Write-Host " >" -NoNewline -ForegroundColor Yellow
    return " "
}

# Advanced prompt with Git status (requires posh-git)
function prompt {
    $path = (Get-Location).Path.Replace($HOME, "~")

    # Username@Computername
    Write-Host "$env:USERNAME" -NoNewline -ForegroundColor Cyan
    Write-Host "@" -NoNewline -ForegroundColor Gray
    Write-Host "$env:COMPUTERNAME" -NoNewline -ForegroundColor Cyan
    Write-Host " in " -NoNewline -ForegroundColor Gray

    # Path
    Write-Host $path -NoNewline -ForegroundColor Blue

    # Git status (if in git repo)
    if (Get-Command git -ErrorAction SilentlyContinue) {
        $gitStatus = git status --porcelain 2>$null
        if ($?) {
            $branch = git branch --show-current
            Write-Host " on " -NoNewline -ForegroundColor Gray
            Write-Host "($branch)" -NoNewline -ForegroundColor Magenta

            if ($gitStatus) {
                Write-Host " ✗" -NoNewline -ForegroundColor Red
            } else {
                Write-Host " ✓" -NoNewline -ForegroundColor Green
            }
        }
    }

    # Admin indicator
    $isAdmin = ([Security.Principal.WindowsPrincipal][Security.Principal.WindowsIdentity]::GetCurrent()).IsInRole([Security.Principal.WindowsBuiltInRole]::Administrator)
    if ($isAdmin) {
        Write-Host " [ADMIN]" -NoNewline -ForegroundColor Red
    }

    Write-Host ""
    Write-Host "❯" -NoNewline -ForegroundColor Yellow
    return " "
}

# ═══════════════════════════════════════════
# CUSTOM ALIASES
# ═══════════════════════════════════════════

# File system aliases
Set-Alias -Name ll -Value Get-ChildItem
Set-Alias -Name la -Value Get-ChildItem

# Navigation aliases
function .. { Set-Location .. }
function ... { Set-Location ..\.. }
function .... { Set-Location ..\..\.. }

# Git aliases
Set-Alias -Name g -Value git
function gs { git status }
function ga { git add $args }
function gc { git commit -m $args }
function gp { git push }
function gl { git log --oneline --graph --decorate -10 }

# Common tools
Set-Alias -Name grep -Value Select-String
Set-Alias -Name which -Value Get-Command
Set-Alias -Name touch -Value New-Item

# ═══════════════════════════════════════════
# CUSTOM FUNCTIONS
# ═══════════════════════════════════════════

# Get public IP
function Get-PublicIP {
    (Invoke-WebRequest -Uri "https://api.ipify.org" -UseBasicParsing).Content
}
Set-Alias -Name myip -Value Get-PublicIP

# Get weather
function Get-Weather {
    param([string]$City = "")
    (Invoke-WebRequest -Uri "https://wttr.in/$City" -UserAgent "curl" -UseBasicParsing).Content
}

# Open current directory in Explorer
function Open-Explorer {
    explorer.exe .
}
Set-Alias -Name open -Value Open-Explorer

# Quick edit profile
function Edit-Profile {
    code $PROFILE
}

# Reload profile
function Update-Profile {
    . $PROFILE
    Write-Host "Profile reloaded!" -ForegroundColor Green
}

# Find files quickly
function Find-File {
    param([string]$Name)
    Get-ChildItem -Recurse -Filter "*$Name*" -ErrorAction SilentlyContinue |
        Select-Object FullName
}
Set-Alias -Name ff -Value Find-File

# Quick directory navigation
function Go-Projects {
    Set-Location "C:\Projects"
}
Set-Alias -Name projects -Value Go-Projects

# System info
function Get-SystemInfo {
    $os = Get-CimInstance Win32_OperatingSystem
    $cpu = Get-CimInstance Win32_Processor
    $disk = Get-Volume | Where-Object {$_.DriveLetter -eq 'C'}

    Write-Host "═══════════════════════════════════════" -ForegroundColor Cyan
    Write-Host "         SYSTEM INFORMATION" -ForegroundColor Cyan
    Write-Host "═══════════════════════════════════════" -ForegroundColor Cyan
    Write-Host "OS: " -NoNewline -ForegroundColor Yellow
    Write-Host $os.Caption
    Write-Host "Computer: " -NoNewline -ForegroundColor Yellow
    Write-Host $env:COMPUTERNAME
    Write-Host "User: " -NoNewline -ForegroundColor Yellow
    Write-Host $env:USERNAME
    Write-Host "CPU: " -NoNewline -ForegroundColor Yellow
    Write-Host $cpu.Name
    Write-Host "RAM: " -NoNewline -ForegroundColor Yellow
    Write-Host "$([math]::Round($os.TotalVisibleMemorySize / 1MB, 2)) GB"
    Write-Host "Disk C: " -NoNewline -ForegroundColor Yellow
    Write-Host "$([math]::Round($disk.SizeRemaining / 1GB, 2)) GB free of $([math]::Round($disk.Size / 1GB, 2)) GB"
    Write-Host "═══════════════════════════════════════" -ForegroundColor Cyan
}
Set-Alias -Name sysinfo -Value Get-SystemInfo

# Quick HTTP server
function Start-HTTPServer {
    param([int]$Port = 8000)
    $listener = New-Object System.Net.HttpListener
    $listener.Prefixes.Add("http://localhost:$Port/")
    $listener.Start()
    Write-Host "Server started at http://localhost:$Port/" -ForegroundColor Green
    Write-Host "Press Ctrl+C to stop" -ForegroundColor Yellow

    while ($listener.IsListening) {
        $context = $listener.GetContext()
        $response = $context.Response
        $content = "Hello from PowerShell HTTP Server!"
        $buffer = [System.Text.Encoding]::UTF8.GetBytes($content)
        $response.ContentLength64 = $buffer.Length
        $response.OutputStream.Write($buffer, 0, $buffer.Length)
        $response.Close()
    }
}

# ═══════════════════════════════════════════
# LOAD MODULES
# ═══════════════════════════════════════════

# Import modules
Import-Module posh-git -ErrorAction SilentlyContinue
Import-Module Terminal-Icons -ErrorAction SilentlyContinue
Import-Module PSReadLine -ErrorAction SilentlyContinue

# Oh-My-Posh theme (if installed)
if (Get-Command oh-my-posh -ErrorAction SilentlyContinue) {
    oh-my-posh init pwsh --config "$env:POSH_THEMES_PATH\paradox.omp.json" | Invoke-Expression
}

# ═══════════════════════════════════════════
# PSREADLINE CONFIGURATION
# ═══════════════════════════════════════════

# Set edit mode
Set-PSReadLineOption -EditMode Windows

# Prediction
Set-PSReadLineOption -PredictionSource History
Set-PSReadLineOption -PredictionViewStyle ListView

# History search
Set-PSReadLineKeyHandler -Key UpArrow -Function HistorySearchBackward
Set-PSReadLineKeyHandler -Key DownArrow -Function HistorySearchForward

# Tab completion
Set-PSReadLineKeyHandler -Key Tab -Function MenuComplete
Set-PSReadLineKeyHandler -Key Shift+Tab -Function Complete

# Custom key bindings
Set-PSReadLineKeyHandler -Chord 'Ctrl+d' -Function DeleteChar
Set-PSReadLineKeyHandler -Chord 'Ctrl+w' -Function BackwardDeleteWord

# Colors
Set-PSReadLineOption -Colors @{
    Command            = 'Yellow'
    Parameter          = 'Green'
    Operator           = 'Magenta'
    Variable           = 'DarkGreen'
    String             = 'DarkCyan'
    Number             = 'DarkCyan'
    Type               = 'DarkYellow'
    Comment            = 'DarkGray'
}

# ═══════════════════════════════════════════
# GREETING MESSAGE
# ═══════════════════════════════════════════

# Welcome message
Write-Host ""
Write-Host "═══════════════════════════════════════" -ForegroundColor Cyan
Write-Host "  Welcome back, " -NoNewline
Write-Host "$env:USERNAME" -NoNewline -ForegroundColor Yellow
Write-Host "!"
Write-Host "  $(Get-Date -Format 'dddd, MMMM dd, yyyy - HH:mm')"
Write-Host "  PowerShell $($PSVersionTable.PSVersion)"
Write-Host "═══════════════════════════════════════" -ForegroundColor Cyan
Write-Host ""

# ═══════════════════════════════════════════
# ENVIRONMENT VARIABLES
# ═══════════════════════════════════════════

# Add to PATH
$env:PATH += ";C:\CustomPath\bin"

# Custom environment variables
$env:EDITOR = "code"
$env:VISUAL = "code"

# ═══════════════════════════════════════════
# PERFORMANCE OPTIONS
# ═══════════════════════════════════════════

# Disable progress bars for faster performance
$ProgressPreference = 'SilentlyContinue'

# Disable confirmation prompts
$ConfirmPreference = 'None'

═══════════════════════════════════════════════════════════
```

---

### Execution Policy 🔐

```powershell
# ═══════════════════════════════════════════
# EXECUTION POLICY
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   EXECUTION POLICY                         ║
╚════════════════════════════════════════════════════════════╝

# View current execution policy
Get-ExecutionPolicy

# View for all scopes
Get-ExecutionPolicy -List

# Execution Policy Levels (most to least restrictive):
# ─────────────────────────────────────────────────────────────
# Restricted       - No scripts allowed (default on Windows clients)
# AllSigned        - Only signed scripts by trusted publisher
# RemoteSigned     - Local scripts OK, downloaded must be signed
# Unrestricted     - All scripts allowed, warns on downloaded
# Bypass           - Nothing blocked, no warnings
# Undefined        - No policy set

# Set execution policy for current user (no admin needed)
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser

# Set for local machine (admin required)
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope LocalMachine

# Temporary bypass for current session
Set-ExecutionPolicy -ExecutionPolicy Bypass -Scope Process

# Run script with bypass
powershell.exe -ExecutionPolicy Bypass -File script.ps1

# Scopes:
# MachinePolicy    - Set by Group Policy for all users
# UserPolicy       - Set by Group Policy for current user
# Process          - Current PowerShell session only
# CurrentUser      - Current user
# LocalMachine     - All users on computer

# Unblock downloaded script
Unblock-File -Path "C:\Scripts\downloaded-script.ps1"

# Unblock all scripts in folder
Get-ChildItem -Path "C:\Scripts" -Recurse | Unblock-File

═══════════════════════════════════════════════════════════
```

---

### Windows Terminal Configuration 🖥️

```json
# ═══════════════════════════════════════════
# WINDOWS TERMINAL SETTINGS.JSON
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   WINDOWS TERMINAL CONFIG                  ║
╚════════════════════════════════════════════════════════════╝

// Location: %LOCALAPPDATA%\Packages\Microsoft.WindowsTerminal_*\LocalState\settings.json
// Or: Settings → Open JSON file

{
    "$schema": "https://aka.ms/terminal-profiles-schema",

    // ═══════════════════════════════════════════
    // GENERAL SETTINGS
    // ═══════════════════════════════════════════

    "defaultProfile": "{574e775e-4f2a-5b96-ac1e-a2962a402336}",  // PowerShell
    "copyOnSelect": true,
    "copyFormatting": false,
    "confirmCloseAllTabs": true,
    "startOnUserLogin": false,
    "launchMode": "default",
    "initialRows": 30,
    "initialCols": 120,

    // ═══════════════════════════════════════════
    // PROFILES
    // ═══════════════════════════════════════════

    "profiles": {
        "defaults": {
            // Default settings for all profiles
            "fontFace": "CascadiaCode Nerd Font",
            "fontSize": 11,
            "fontWeight": "normal",
            "colorScheme": "One Half Dark",
            "useAcrylic": true,
            "acrylicOpacity": 0.85,
            "cursorShape": "bar",
            "cursorColor": "#FFFFFF",
            "antialiasingMode": "grayscale",
            "padding": "8, 8, 8, 8",
            "scrollbarState": "visible"
        },
        "list": [
            {
                // PowerShell 7
                "guid": "{574e775e-4f2a-5b96-ac1e-a2962a402336}",
                "name": "PowerShell 7",
                "commandline": "pwsh.exe -NoLogo",
                "icon": "ms-appx:///ProfileIcons/{574e775e-4f2a-5b96-ac1e-a2962a402336}.png",
                "startingDirectory": "%USERPROFILE%",
                "hidden": false
            },
            {
                // Windows PowerShell
                "guid": "{61c54bbd-c2c6-5271-96e7-009a87ff44bf}",
                "name": "Windows PowerShell",
                "commandline": "powershell.exe -NoLogo",
                "icon": "ms-appx:///ProfileIcons/{61c54bbd-c2c6-5271-96e7-009a87ff44bf}.png",
                "startingDirectory": "%USERPROFILE%",
                "hidden": false
            },
            {
                // Command Prompt
                "guid": "{0caa0dad-35be-5f56-a8ff-afceeeaa6101}",
                "name": "Command Prompt",
                "commandline": "cmd.exe",
                "icon": "ms-appx:///ProfileIcons/{0caa0dad-35be-5f56-a8ff-afceeeaa6101}.png",
                "hidden": false
            },
            {
                // Git Bash (if installed)
                "guid": "{00000000-0000-0000-ba54-000000000002}",
                "name": "Git Bash",
                "commandline": "\"%PROGRAMFILES%\\Git\\bin\\bash.exe\" -i -l",
                "icon": "%PROGRAMFILES%\\Git\\mingw64\\share\\git\\git-for-windows.ico",
                "startingDirectory": "%USERPROFILE%",
                "hidden": false
            },
            {
                // Ubuntu WSL (if installed)
                "guid": "{2c4de342-38b7-51cf-b940-2309a097f518}",
                "name": "Ubuntu",
                "source": "Windows.Terminal.Wsl",
                "hidden": false
            }
        ]
    },

    // ═══════════════════════════════════════════
    // COLOR SCHEMES
    // ═══════════════════════════════════════════

    "schemes": [
        {
            "name": "One Half Dark",
            "black": "#282c34",
            "red": "#e06c75",
            "green": "#98c379",
            "yellow": "#e5c07b",
            "blue": "#61afef",
            "purple": "#c678dd",
            "cyan": "#56b6c2",
            "white": "#dcdfe4",
            "brightBlack": "#5a6374",
            "brightRed": "#e06c75",
            "brightGreen": "#98c379",
            "brightYellow": "#e5c07b",
            "brightBlue": "#61afef",
            "brightPurple": "#c678dd",
            "brightCyan": "#56b6c2",
            "brightWhite": "#dcdfe4",
            "background": "#282c34",
            "foreground": "#dcdfe4",
            "selectionBackground": "#3e4451",
            "cursorColor": "#528bff"
        },
        {
            "name": "Dracula",
            "black": "#000000",
            "red": "#ff5555",
            "green": "#50fa7b",
            "yellow": "#f1fa8c",
            "blue": "#bd93f9",
            "purple": "#ff79c6",
            "cyan": "#8be9fd",
            "white": "#bbbbbb",
            "brightBlack": "#555555",
            "brightRed": "#ff5555",
            "brightGreen": "#50fa7b",
            "brightYellow": "#f1fa8c",
            "brightBlue": "#bd93f9",
            "brightPurple": "#ff79c6",
            "brightCyan": "#8be9fd",
            "brightWhite": "#ffffff",
            "background": "#1e1f29",
            "foreground": "#f8f8f2",
            "cursorColor": "#bbbbbb",
            "selectionBackground": "#44475a"
        },
        {
            "name": "GitHub Dark",
            "black": "#000000",
            "red": "#f78166",
            "green": "#56d364",
            "yellow": "#e3b341",
            "blue": "#6cb6ff",
            "purple": "#bc8cff",
            "cyan": "#76e3ea",
            "white": "#b1bac4",
            "brightBlack": "#6e7681",
            "brightRed": "#f78166",
            "brightGreen": "#56d364",
            "brightYellow": "#e3b341",
            "brightBlue": "#6cb6ff",
            "brightPurple": "#bc8cff",
            "brightCyan": "#76e3ea",
            "brightWhite": "#f0f3f6",
            "background": "#0d1117",
            "foreground": "#b1bac4",
            "cursorColor": "#6cb6ff",
            "selectionBackground": "#1f2937"
        }
    ],

    // ═══════════════════════════════════════════
    // KEY BINDINGS
    // ═══════════════════════════════════════════

    "actions": [
        // Copy/Paste
        { "command": { "action": "copy", "singleLine": false }, "keys": "ctrl+c" },
        { "command": "paste", "keys": "ctrl+v" },

        // Tabs
        { "command": "newTab", "keys": "ctrl+t" },
        { "command": "closeTab", "keys": "ctrl+w" },
        { "command": "duplicateTab", "keys": "ctrl+shift+d" },
        { "command": { "action": "nextTab" }, "keys": "ctrl+tab" },
        { "command": { "action": "prevTab" }, "keys": "ctrl+shift+tab" },

        // Panes
        { "command": { "action": "splitPane", "split": "horizontal" }, "keys": "alt+shift+-" },
        { "command": { "action": "splitPane", "split": "vertical" }, "keys": "alt+shift+plus" },
        { "command": { "action": "moveFocus", "direction": "down" }, "keys": "alt+down" },
        { "command": { "action": "moveFocus", "direction": "up" }, "keys": "alt+up" },
        { "command": { "action": "moveFocus", "direction": "left" }, "keys": "alt+left" },
        { "command": { "action": "moveFocus", "direction": "right" }, "keys": "alt+right" },
        { "command": "closePane", "keys": "ctrl+shift+w" },

        // Zoom
        { "command": { "action": "adjustFontSize", "delta": 1 }, "keys": "ctrl+plus" },
        { "command": { "action": "adjustFontSize", "delta": -1 }, "keys": "ctrl+-" },
        { "command": "resetFontSize", "keys": "ctrl+0" },

        // Search
        { "command": "find", "keys": "ctrl+shift+f" },

        // Settings
        { "command": "openSettings", "keys": "ctrl+," },
        { "command": { "action": "openSettings", "target": "defaultsFile" }, "keys": "ctrl+alt+," }
    ]
}

// ═══════════════════════════════════════════
// INSTALL NERD FONTS (for icons)
// ═══════════════════════════════════════════

# Using Scoop
scoop bucket add nerd-fonts
scoop install CascadiaCode-NF

# Or download from:
# https://www.nerdfonts.com/

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## 🧪 Advanced Scripting

</div>

### PowerShell Pipeline & Operators 🔀

```powershell
# ═══════════════════════════════════════════
# PIPELINE BASICS
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   PIPELINE OPERATORS                       ║
╚════════════════════════════════════════════════════════════╝

# Pipeline passes objects, not text!
Get-Process | Where-Object {$_.CPU -gt 100} | Sort-Object CPU -Descending | Select-Object -First 10

# Pipeline variable
Get-Process | ForEach-Object {
    Write-Host "$($_.Name): $($_.CPU)"
}

# Short form
Get-Process | % { Write-Host "$($_.Name): $($_.CPU)" }

# ═══════════════════════════════════════════
# WHERE-OBJECT (Filtering)
# ═══════════════════════════════════════════

# Full syntax
Get-Process | Where-Object {$_.CPU -gt 100}
Get-ChildItem | Where-Object {$_.Length -gt 1MB}
Get-Service | Where-Object {$_.Status -eq "Running"}

# Short form
Get-Process | ? {$_.CPU -gt 100}

# Multiple conditions
Get-Process | Where-Object {$_.CPU -gt 100 -and $_.WS -gt 100MB}
Get-Process | Where-Object {$_.Name -like "chrome*" -or $_.Name -like "firefox*"}

# Comparison operators
# -eq  (equal)
# -ne  (not equal)
# -gt  (greater than)
# -ge  (greater or equal)
# -lt  (less than)
# -le  (less or equal)
# -like (wildcard match)
# -notlike
# -match (regex match)
# -notmatch
# -contains
# -notcontains
# -in
# -notin

# ═══════════════════════════════════════════
# SELECT-OBJECT
# ═══════════════════════════════════════════

# Select properties
Get-Process | Select-Object Name, CPU, WS

# First/Last items
Get-Process | Select-Object -First 5
Get-Process | Select-Object -Last 5
Get-Process | Select-Object -Skip 5 -First 10

# Unique values
Get-Process | Select-Object Company -Unique

# Calculated properties
Get-Process | Select-Object Name,
    @{Name="MemoryMB";Expression={[math]::Round($_.WS/1MB, 2)}},
    @{Name="CPUTime";Expression={$_.CPU};FormatString="N2"}

# ═══════════════════════════════════════════
# FOREACH-OBJECT
# ═══════════════════════════════════════════

# Full syntax
Get-ChildItem *.txt | ForEach-Object {
    $_.Name
}

# Short form
Get-ChildItem *.txt | % { $_.Name }

# With Begin, Process, End
Get-ChildItem | ForEach-Object -Begin {
    $total = 0
} -Process {
    $total += $_.Length
} -End {
    Write-Host "Total size: $total bytes"
}

# ═══════════════════════════════════════════
# MEASURE-OBJECT
# ═══════════════════════════════════════════

# Count
Get-ChildItem | Measure-Object

# Statistics
Get-Process | Measure-Object -Property WS -Sum -Average -Maximum -Minimum

# Line count
Get-Content file.txt | Measure-Object -Line

# ═══════════════════════════════════════════
# GROUP-OBJECT
# ═══════════════════════════════════════════

Get-Process | Group-Object Company
Get-Service | Group-Object Status
Get-ChildItem | Group-Object Extension

# With count
Get-Process | Group-Object Company | Select-Object Count, Name | Sort-Object Count -Descending

# ═══════════════════════════════════════════
# SORT-OBJECT
# ═══════════════════════════════════════════

Get-Process | Sort-Object CPU
Get-Process | Sort-Object CPU -Descending
Get-Process | Sort-Object Company, Name
Get-ChildItem | Sort-Object Length -Descending | Select-Object -First 10

# ═══════════════════════════════════════════
# OPERATORS
# ═══════════════════════════════════════════

# Arithmetic operators
$a + $b         # Addition
$a - $b         # Subtraction
$a * $b         # Multiplication
$a / $b         # Division
$a % $b         # Modulo
$a++ / $a--     # Increment/Decrement

# Assignment operators
$a = 10
$a += 5         # $a = $a + 5
$a -= 5         # $a = $a - 5
$a *= 2         # $a = $a * 2
$a /= 2         # $a = $a / 2
$a %= 3         # $a = $a % 3

# Logical operators
-and            # Logical AND
-or             # Logical OR
-not / !        # Logical NOT
-xor            # Logical XOR

# String operators
$str1 + $str2   # Concatenation
$str * 3        # Repeat
-join           # Join array
-split          # Split string
-replace        # Replace
-match          # Match pattern
-like           # Wildcard match

# Range operator
1..10           # Array of 1 to 10
'a'..'z'        # Array of letters

# Type operators
$var -is [int]
$var -isnot [string]
$var -as [int]

═══════════════════════════════════════════════════════════
```

---

### Variables & Data Types 📊

```powershell
# ═══════════════════════════════════════════
# VARIABLES
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   VARIABLES                                ║
╚════════════════════════════════════════════════════════════╝

# Create variable
$name = "MrDib"
$age = 25
$isActive = $true
$salary = 50000.50

# Variable naming rules
# - Must start with letter or underscore
# - Can contain letters, numbers, underscore
# - Case insensitive
# - No spaces

# Valid names
$myVariable = "value"
$_temp = "value"
$Variable123 = "value"

# Typed variables
[string]$text = "Hello"
[int]$number = 42
[double]$decimal = 3.14
[bool]$flag = $true
[datetime]$date = Get-Date
[array]$arr = @(1, 2, 3)
[hashtable]$hash = @{key="value"}

# Check type
$var.GetType()
$var.GetType().Name

# ═══════════════════════════════════════════
# ARRAYS
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   ARRAYS                                   ║
╚════════════════════════════════════════════════════════════╝

# Create array
$array = @(1, 2, 3, 4, 5)
$array = 1, 2, 3, 4, 5
$array = 1..10          # Range

# Empty array
$array = @()

# Mixed types
$array = @("text", 123, $true, (Get-Date))

# Access elements
$array[0]               # First element
$array[-1]              # Last element
$array[1..3]            # Multiple elements
$array[0,2,4]           # Specific indices

# Array properties
$array.Count            # Number of elements
$array.Length           # Same as Count

# Modify array
$array += 6             # Add element
$array += @(7, 8, 9)    # Add multiple
$array[0] = 10          # Change element

# Array methods
$array.Contains(5)      # Check if contains
$array.IndexOf(3)       # Find index
[array]::Reverse($array)  # Reverse
[array]::Sort($array)   # Sort

# Multidimensional arrays
$matrix = @(
    @(1, 2, 3),
    @(4, 5, 6),
    @(7, 8, 9)
)
$matrix[0][1]           # Access: 2

# Array operations
$arr1 + $arr2           # Concatenate
$arr1 | Where-Object {$_ -gt 5}  # Filter
$arr1 | ForEach-Object {$_ * 2}  # Map

# ═══════════════════════════════════════════
# HASH TABLES
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   HASH TABLES                              ║
╚════════════════════════════════════════════════════════════╝

# Create hash table
$hash = @{
    Name = "MrDib"
    Age = 25
    City = "New York"
}

# Empty hash table
$hash = @{}

# Access values
$hash["Name"]
$hash.Name              # Dot notation
$hash.Age

# Add/modify
$hash["Email"] = "email@example.com"
$hash.Phone = "123-456-7890"

# Remove
$hash.Remove("City")

# Check if key exists
$hash.ContainsKey("Name")
$hash.ContainsValue("MrDib")

# Keys and values
$hash.Keys
$hash.Values

# Iterate
foreach ($key in $hash.Keys) {
    Write-Host "$key : $($hash[$key])"
}

# Ordered hash table
$ordered = [ordered]@{
    First = 1
    Second = 2
    Third = 3
}

# ═══════════════════════════════════════════
# SPECIAL VARIABLES
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   SPECIAL VARIABLES                        ║
╚════════════════════════════════════════════════════════════╝

$_                      # Current pipeline object
$?                      # Last command success status
$^                      # First token of last line
$args                   # Function arguments
$Error                  # Array of errors
$ExecutionContext       # Execution environment
$false / $true          # Boolean values
$HOME                   # User home directory
$Host                   # Host application
$input                  # Enumerator for pipeline input
$LASTEXITCODE           # Exit code of last program
$Matches                # Regex matches
$MyInvocation           # Command invocation info
$null                   # Null value
$PID                    # Process ID
$PROFILE                # Profile path
$PSBoundParameters      # Function parameters
$PSCommandPath          # Script path
$PSScriptRoot           # Script directory
$PSVersionTable         # PowerShell version info
$PWD                    # Current directory

# Environment variables
$env:PATH
$env:USERNAME
$env:COMPUTERNAME
$env:USERPROFILE
$env:TEMP
$env:PROGRAMFILES

═══════════════════════════════════════════════════════════
```

---

### Control Flow & Functions 🔄

```powershell
# ═══════════════════════════════════════════
# IF/ELSE STATEMENTS
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   CONDITIONALS                             ║
╚════════════════════════════════════════════════════════════╝

# Basic if
$age = 25
if ($age -ge 18) {
    Write-Host "Adult"
}

# If/Else
if ($age -ge 18) {
    Write-Host "Adult"
} else {
    Write-Host "Minor"
}

# If/ElseIf/Else
if ($age -lt 13) {
    Write-Host "Child"
} elseif ($age -lt 18) {
    Write-Host "Teenager"
} else {
    Write-Host "Adult"
}

# Ternary operator (PowerShell 7+)
$status = ($age -ge 18) ? "Adult" : "Minor"

# ═══════════════════════════════════════════
# SWITCH STATEMENTS
# ═══════════════════════════════════════════

$day = 3

switch ($day) {
    1 { "Monday" }
    2 { "Tuesday" }
    3 { "Wednesday" }
    4 { "Thursday" }
    5 { "Friday" }
    {$_ -in 6,7} { "Weekend" }
    default { "Invalid day" }
}

# Switch with break
switch ($value) {
    1 { "One"; break }
    2 { "Two"; break }
    default { "Other" }
}

# ═══════════════════════════════════════════
# LOOPS
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   LOOPS                                    ║
╚════════════════════════════════════════════════════════════╝

# ForEach loop
$items = 1..5
foreach ($item in $items) {
    Write-Host $item
}

# For loop
for ($i = 0; $i -lt 5; $i++) {
    Write-Host $i
}

# While loop
$count = 0
while ($count -lt 5) {
    Write-Host $count
    $count++
}

# Do-While loop
$count = 0
do {
    Write-Host $count
    $count++
} while ($count -lt 5)

# Do-Until loop
$count = 0
do {
    Write-Host $count
    $count++
} until ($count -ge 5)

# ForEach-Object (pipeline)
1..5 | ForEach-Object {
    Write-Host $_
}

# Loop control
foreach ($i in 1..10) {
    if ($i -eq 5) {
        break           # Exit loop
    }
    if ($i % 2 -eq 0) {
        continue        # Skip iteration
    }
    Write-Host $i
}

# ═══════════════════════════════════════════
# FUNCTIONS
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   FUNCTIONS                                ║
╚════════════════════════════════════════════════════════════╝

# Basic function
function Say-Hello {
    Write-Host "Hello, World!"
}

Say-Hello

# Function with parameters
function Say-HelloTo {
    param(
        [string]$Name
    )
    Write-Host "Hello, $Name!"
}

Say-HelloTo -Name "MrDib"

# Advanced function
function Get-FileSize {
    [CmdletBinding()]
    param(
        [Parameter(Mandatory=$true, Position=0)]
        [ValidateScript({Test-Path $_ -PathType Leaf})]
        [string]$Path,

        [Parameter(Mandatory=$false)]
        [ValidateSet("KB","MB","GB")]
        [string]$Unit = "MB"
    )

    $size = (Get-Item $Path).Length

    switch ($Unit) {
        "KB" { $size = $size / 1KB }
        "MB" { $size = $size / 1MB }
        "GB" { $size = $size / 1GB }
    }

    return [math]::Round($size, 2)
}

# Function with multiple return values
function Get-MinMax {
    param([array]$Numbers)

    $min = ($Numbers | Measure-Object -Minimum).Minimum
    $max = ($Numbers | Measure-Object -Maximum).Maximum

    return @{
        Minimum = $min
        Maximum = $max
    }
}

$result = Get-MinMax -Numbers @(5, 2, 8, 1, 9)
$result.Minimum
$result.Maximum

# Function with pipeline input
function Get-Square {
    param(
        [Parameter(ValueFromPipeline=$true)]
        [int]$Number
    )

    process {
        return $Number * $Number
    }
}

1..10 | Get-Square

# ═══════════════════════════════════════════
# ERROR HANDLING
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   ERROR HANDLING                           ║
╚════════════════════════════════════════════════════════════╝

# Try/Catch
try {
    Get-Item "C:\NonExistent.txt" -ErrorAction Stop
} catch {
    Write-Host "Error: $($_.Exception.Message)" -ForegroundColor Red
}

# Try/Catch/Finally
try {
    $content = Get-Content "C:\file.txt"
} catch {
    Write-Host "Failed to read file"
} finally {
    Write-Host "Cleanup code here"
}

# Specific exception types
try {
    [int]$number = "not a number"
} catch [System.InvalidCastException] {
    Write-Host "Invalid cast error"
} catch {
    Write-Host "Other error"
}

# Error action preference
Get-Item "C:\NonExistent.txt" -ErrorAction SilentlyContinue
Get-Item "C:\NonExistent.txt" -ErrorAction Continue
Get-Item "C:\NonExistent.txt" -ErrorAction Stop

# Set global preference
$ErrorActionPreference = "Stop"

# Throw custom error
if ($value -lt 0) {
    throw "Value cannot be negative"
}

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## 💡 Pro Tips & Best Practices

</div>

### One-Liners & Useful Scripts 🚀

```powershell
# ═══════════════════════════════════════════
# SYSTEM INFORMATION ONE-LINERS
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   SYSTEM ONE-LINERS                        ║
╚════════════════════════════════════════════════════════════╝

# Computer info summary
Get-ComputerInfo | Select-Object CsName, WindowsVersion, OsArchitecture, CsProcessors, CsTotalPhysicalMemory

# Disk space all drives
Get-PSDrive -PSProvider FileSystem | Select-Object Name, @{n="Used(GB)";e={[math]::Round($_.Used/1GB,2)}}, @{n="Free(GB)";e={[math]::Round($_.Free/1GB,2)}}, @{n="Total(GB)";e={[math]::Round(($_.Used+$_.Free)/1GB,2)}}

# Top 10 CPU processes
Get-Process | Sort-Object CPU -Descending | Select-Object -First 10 Name, @{n="CPU(s)";e={$_.CPU}}, @{n="Mem(MB)";e={[math]::Round($_.WS/1MB,2)}}

# Top 10 memory processes
Get-Process | Sort-Object WS -Descending | Select-Object -First 10 Name, @{n="Mem(MB)";e={[math]::Round($_.WS/1MB,2)}}

# Top 10 largest files in directory
Get-ChildItem -Recurse -File | Sort-Object Length -Descending | Select-Object -First 10 FullName, @{n="Size(MB)";e={[math]::Round($_.Length/1MB,2)}}

# Find duplicate files by hash
Get-ChildItem -Recurse -File | Group-Object {(Get-FileHash $_.FullName).Hash} | Where-Object {$_.Count -gt 1} | Select-Object -ExpandProperty Group

# Count files by extension
Get-ChildItem -Recurse -File | Group-Object Extension | Select-Object Count, Name | Sort-Object Count -Descending

# Files modified in last 7 days
Get-ChildItem -Recurse | Where-Object {$_.LastWriteTime -gt (Get-Date).AddDays(-7)} | Select-Object FullName, LastWriteTime

# Empty directories
Get-ChildItem -Recurse -Directory | Where-Object {!(Get-ChildItem $_.FullName)}

# ═══════════════════════════════════════════
# NETWORK ONE-LINERS
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   NETWORK ONE-LINERS                       ║
╚════════════════════════════════════════════════════════════╝

# Get public IP
(Invoke-WebRequest -Uri "https://api.ipify.org" -UseBasicParsing).Content

# Get local IP addresses
Get-NetIPAddress -AddressFamily IPv4 | Where-Object {$_.IPAddress -notlike "127.*"} | Select-Object IPAddress, InterfaceAlias

# Active network connections
Get-NetTCPConnection -State Established | Select-Object LocalAddress, LocalPort, RemoteAddress, RemotePort, State, OwningProcess

# Listening ports with process
Get-NetTCPConnection -State Listen | Select-Object LocalPort, @{n="Process";e={(Get-Process -Id $_.OwningProcess).Name}}

# DNS servers
Get-DnsClientServerAddress | Where-Object {$_.ServerAddresses} | Select-Object InterfaceAlias, ServerAddresses

# MAC addresses
Get-NetAdapter | Select-Object Name, MacAddress, Status

# Network speed test (download 10MB)
Measure-Command { Invoke-WebRequest -Uri "https://speed.cloudflare.com/__down?bytes=10000000" -UseBasicParsing } | Select-Object TotalSeconds

# ═══════════════════════════════════════════
# USEFUL FUNCTIONS
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   USEFUL FUNCTIONS                         ║
╚════════════════════════════════════════════════════════════╝

# Create directory structure
function New-ProjectStructure {
    param([string]$Name)
    @("src", "tests", "docs", "bin") | ForEach-Object {
        New-Item -Path "$Name\$_" -ItemType Directory -Force
    }
}

# Bulk rename with pattern
function Rename-FilesPattern {
    param(
        [string]$Path,
        [string]$OldPattern,
        [string]$NewPattern
    )
    Get-ChildItem $Path | Where-Object {$_.Name -like "*$OldPattern*"} |
        Rename-Item -NewName {$_.Name -replace $OldPattern, $NewPattern}
}

# Convert seconds to human readable
function ConvertTo-HumanTime {
    param([int]$Seconds)

    $days = [math]::Floor($Seconds / 86400)
    $hours = [math]::Floor(($Seconds % 86400) / 3600)
    $minutes = [math]::Floor(($Seconds % 3600) / 60)
    $secs = $Seconds % 60

    "$days days, $hours hours, $minutes minutes, $secs seconds"
}

# Get folder size
function Get-FolderSize {
    param([string]$Path)
    $size = (Get-ChildItem $Path -Recurse | Measure-Object -Property Length -Sum).Sum
    [math]::Round($size / 1GB, 2)
}

# Benchmark command
function Measure-CommandPerformance {
    param(
        [scriptblock]$Command,
        [int]$Iterations = 10
    )

    $times = 1..$Iterations | ForEach-Object {
        (Measure-Command $Command).TotalMilliseconds
    }

    [PSCustomObject]@{
        Average = ($times | Measure-Object -Average).Average
        Minimum = ($times | Measure-Object -Minimum).Minimum
        Maximum = ($times | Measure-Object -Maximum).Maximum
    }
}

# ═══════════════════════════════════════════
# PERFORMANCE TIPS
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   PERFORMANCE TIPS                         ║
╚════════════════════════════════════════════════════════════╝

# ✓ DO: Use -Filter instead of Where-Object for Get-ChildItem
Get-ChildItem -Filter "*.txt"

# ✗ DON'T:
Get-ChildItem | Where-Object {$_.Extension -eq ".txt"}

# ✓ DO: Use [System.IO.File] for large files
[System.IO.File]::ReadAllLines("large-file.txt")

# ✗ DON'T:
Get-Content "large-file.txt"

# ✓ DO: Disable progress for speed
$ProgressPreference = 'SilentlyContinue'

# ✓ DO: Use foreach instead of ForEach-Object for arrays
foreach ($item in $array) { }

# ✗ DON'T: (slower)
$array | ForEach-Object { }

# ✓ DO: Use StringBuilder for string concatenation
$sb = New-Object System.Text.StringBuilder
1..1000 | ForEach-Object { [void]$sb.Append($_) }
$sb.ToString()

# ✗ DON'T: (much slower)
$str = ""
1..1000 | ForEach-Object { $str += $_ }

# ✓ DO: Use -contains for array membership
if ($array -contains $item) { }

# ✗ DON'T: (slower)
if ($array | Where-Object {$_ -eq $item}) { }

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## 🎓 Resources & Learning

</div>

### Learning Platforms 📚

```
╔════════════════════════════════════════════════════════════╗
║                   OFFICIAL RESOURCES                       ║
╚════════════════════════════════════════════════════════════╝

📘 Microsoft Documentation
   https://docs.microsoft.com/powershell/
   https://learn.microsoft.com/powershell/

📗 PowerShell Gallery
   https://www.powershellgallery.com/

📙 PowerShell GitHub
   https://github.com/PowerShell/PowerShell

╔════════════════════════════════════════════════════════════╗
║                   LEARNING RESOURCES                       ║
╚════════════════════════════════════════════════════════════╝

📚 Online Resources
   PowerShell.org: https://powershell.org/
   SS64 PowerShell: https://ss64.com/ps/
   Learn PowerShell: https://learnxinyminutes.com/docs/powershell/
   PowerShell Explained: https://powershellexplained.com/

📖 Books
   "Learn PowerShell in a Month of Lunches" - Don Jones
   "PowerShell for Sysadmins" - Adam Bertram
   "Windows PowerShell Cookbook" - Lee Holmes
   "Mastering PowerShell Scripting" - Chris Dent

🎥 Video Tutorials
   Microsoft Learn
   PowerShell.org YouTube Channel
   ITPro.TV PowerShell Training
   Pluralsight PowerShell Courses

🏋️ Practice & Challenges
   PSKoans: https://github.com/vexx32/PSKoans
   UnderTheWire: https://underthewire.tech/
   OverTheWire: https://overthewire.org/wargames/

╔════════════════════════════════════════════════════════════╗
║                   COMMUNITY                                ║
╚════════════════════════════════════════════════════════════╝

💬 Forums & Communities
   Reddit: r/PowerShell
   Stack Overflow: [powershell]
   PowerShell.org Forums
   TechNet Forums

🐦 Twitter
   @PowerShell_Team
   @jsnover (Jeffrey Snover - Creator of PowerShell)
   @PowerShellMag

📧 Newsletters
   PowerShell Weekly
   PowerShell.org Newsletter

╔════════════════════════════════════════════════════════════╗
║                   TOOLS & EXTENSIONS                       ║
╚════════════════════════════════════════════════════════════╝

🔧 IDEs & Editors
   Visual Studio Code + PowerShell Extension
   PowerShell ISE (built-in)
   Windows Terminal
   ConEmu
   Cmder

📦 Useful Modules
   PSReadLine - Better command-line experience
   posh-git - Git integration
   Oh-My-Posh - Beautiful prompts
   Terminal-Icons - File icons
   PSScriptAnalyzer - Code analysis
   Pester - Testing framework
```

---

<div align="center">

**Built with 💙 by MrDib and the PowerShell Community**

_"PowerShell: Because life's too short for batch files"_ 🚀

**Happy PowerShell Scripting!** ✨

### May your scripts be bug-free and your pipelines be efficient! 🎯

---

**⭐ Star this repo if you found it helpful!**

**🔀 Fork it to customize for your needs!**

**📝 Contribute to make it even better!**

</div>

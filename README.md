# votv-modding-for-dummies

## Epic Games Launcher

## Unreal Engine Setup

## Project Setup
Now, it's time to create your UE4 "VotV" project, where you'll be developing your mods.

```powershell
ni -Name VotV -ItemType directory
ni -Name VotV.uproject -ItemType file -Path '.\VotV' -Value '{"FileVersion":3,"EngineAssociation":"4.27"}'
```

```powershell
ni -Name Config -ItemType directory -Path '.\VotV'
$DefaultGame = ni -Name DefaultGame.ini -ItemType file -Path '.\VotV\Config'

ac -Path $DefaultGame -Value '[/Script/UnrealEd.ProjectPackagingSettings]'
ac -Path $DefaultGame -Value 'bGenerateChunks=True'
ac -Path $DefaultGame -Value 'bShareMaterialShaderCode=False'
```

```powershell
$vpurl = 'https://github.com/jiltq/votv-modding-for-dummies/releases/download/VictoryPlugin27/VictoryPlugin27.zip'
$cont = (iwr -Uri $vpurl).Content
```

```powershell
$stream = New-Object System.IO.MemoryStream
$stream.Write($cont, 0, $cont.Length)
$stream.Position = 0
```

```powershell
$zip = [System.IO.Compression.ZipArchive]::new($stream, [System.IO.Compression.ZipArchiveMode]::Read)

ni -Name Plugins -ItemType directory -Path '.\VotV'
ni -Name VictoryBPLibrary -ItemType directory -Path '.\VotV\Plugins'

[System.IO.Compression.ZipFileExtensions]::ExtractToDirectory($zip, '.\VotV\Plugins\VictoryBPLibrary')
```

```powershell
start .\VotV\VotV.uproject
```

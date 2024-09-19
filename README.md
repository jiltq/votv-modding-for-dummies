# votv-modding-for-dummies

## Epic Games Launcher

## Unreal Engine Setup

## idk
```powershell
ni -Name VotV -ItemType directory | sl
ni -Name VotV.uproject -ItemType file -Value '{"FileVersion":3,"EngineAssociation":"4.27"}'
start VotV.uproject
```

```powershell
ni -Name Config -ItemType directory | sl
$DefaultGame = ni -Name DefaultGame.ini -ItemType file

ac -Path $DefaultGame -Value '[/Script/UnrealEd.ProjectPackagingSettings]'
ac -Path $DefaultGame -Value 'bGenerateChunks=True'
ac -Path $DefaultGame -Value 'bShareMaterialShaderCode=False'
```

```powershell
$stream = New-Object System.IO.MemoryStream

iwr -Uri "http://www.contoso.com" -OutFile $stream
$stream.Position = 0

$Compression = [System.IO.Compression]

$zip = $Compression.ZipArchive::new($stream, $Compression.ZipArchiveMode::Read)
$zip.ExtractToDirectory($destinationPath)

$stream.Dispose()
$zip.Dispose()
```

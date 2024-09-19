# votv-modding-for-dummies

## Epic Games Launcher

## Unreal Engine Setup

## Project Setup
Now, it's time to create your UE4 "VotV" project, where you'll be developing your mods.

```powershell
ni -Name VotV.uproject -ItemType file -Path '.\VotV' -Force -Value '{"FileVersion":3,"EngineAssociation":"4.27"}'
```
Configure the project to be compatible with modding...
```powershell
$DefaultGame = ni -Name DefaultGame.ini -ItemType file -Path '.\VotV\Config' -Force

ac -Path $DefaultGame -Value '[/Script/UnrealEd.ProjectPackagingSettings]'
ac -Path $DefaultGame -Value 'bGenerateChunks=True'
ac -Path $DefaultGame -Value 'bShareMaterialShaderCode=False'
```
Download VictoryPlugin27...
```powershell
$vpurl = 'https://github.com/jiltq/votv-modding-for-dummies/releases/download/VictoryPlugin27/VictoryPlugin27.zip'
$cont = (iwr -Uri $vpurl).Content
```
Write the zipped plugin to memory...
```powershell
$stream = New-Object System.IO.MemoryStream
$stream.Write($cont, 0, $cont.Length)
$stream.Position = 0
```
Install the plugin to the project...
```powershell
$zip = [System.IO.Compression.ZipArchive]::new($stream, [System.IO.Compression.ZipArchiveMode]::Read)

$vpdir = ni -Name VictoryBPLibrary -ItemType directory -Path '.\VotV\Plugins' -Force

[System.IO.Compression.ZipFileExtensions]::ExtractToDirectory($zip, $vpdir)
```
And fire up the editor...!
```powershell
start .\VotV\VotV.uproject
```

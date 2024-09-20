# votv-modding-for-dummies

## Prerequisites
This guide assumes you have a fairly recent version of Powershell.

## Epic Games Launcher

## Unreal Engine Setup

## Project Setup
Now, it's time to create your UE4 "VotV" project, where you'll be developing your mods.
```powershell
# Create project
ni -Name VotV.uproject -ItemType file -Path '.\VotV' -Force -Value '{"FileVersion":3,"EngineAssociation":"4.27"}'
```
```powershell
# Configure project for modding
$DefaultGame = ni -Name DefaultGame.ini -ItemType file -Path '.\VotV\Config' -Force

ac -Path $DefaultGame -Value '[/Script/UnrealEd.ProjectPackagingSettings]'
ac -Path $DefaultGame -Value 'bGenerateChunks=True'
ac -Path $DefaultGame -Value 'bShareMaterialShaderCode=False'
```
```powershell
# Download VictoryPlugin27
$vpurl = 'https://github.com/jiltq/votv-modding-for-dummies/releases/download/VictoryPlugin27/VictoryPlugin27.zip'
$cont = (iwr -Uri $vpurl).Content
```
```powershell
# Write zipped plugin to memory
$stream = New-Object System.IO.MemoryStream
$stream.Write($cont, 0, $cont.Length)
$stream.Position = 0
```
```powershell
# Install plugin to project
$zip = [System.IO.Compression.ZipArchive]::new($stream, [System.IO.Compression.ZipArchiveMode]::Read)

$vpdir = ni -Name VictoryBPLibrary -ItemType directory -Path '.\VotV\Plugins' -Force
[System.IO.Compression.ZipFileExtensions]::ExtractToDirectory($zip, $vpdir)
```
### VoidMod
Head on over to the [EternityDev Games "VoidMod Loader" thread](https://discord.com/channels/512287844258021376/1135662233460949002/1250255466928275537) and download `VoidModDevKit-2.0.0.zip`.

Back at your terminal, run the following:
```powershell
# Copy "Content" dir to clipboard, open Explorer
ni -Name Content -ItemType directory -Path '.\VotV' | scb
explorer
```
Then extract the DevKit as you would any ZIP file, but use the value in your clipboard as the target path.

And fire up the editor...!
```powershell
start .\VotV\VotV.uproject
```

## In the Editor
wip

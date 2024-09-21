# votv-modding-for-dummies

## Prerequisites
This guide assumes you have a fairly recent version of Powershell.

## Epic Games Launcher

## Unreal Engine Setup

## Project Setup
Now, it's time to create your UE4 "VotV" project, where you'll be developing your mods.
```powershell
# Create project
ni '.\VotV' -Name VotV.uproject -ItemType File -Force -Value '{"FileVersion":3,"EngineAssociation":"4.27"}'
```
```powershell
# Configure project for modding
$DefaultGame = ni '.\VotV\Config' -Name DefaultGame.ini -ItemType File -Force

ac $DefaultGame '[/Script/UnrealEd.ProjectPackagingSettings]'
ac $DefaultGame 'bGenerateChunks=True'
ac $DefaultGame 'bShareMaterialShaderCode=False'
```
```powershell
# Download VictoryPlugin27 (86.5 MB)
$vpurl = 'https://github.com/jiltq/votv-modding-for-dummies/releases/download/VictoryPlugin27/VictoryPlugin27.zip'
$cont = (iwr $vpurl).Content
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
ni '.\VotV' -Name Content -ItemType Directory | scb
explorer
```
Then extract the DevKit as you would any ZIP file, but use the value in your clipboard as the target path.

And fire up the editor...!
```powershell
.\VotV\VotV.uproject
```
After this, Unreal Engine will remember the project and let you open it from the project select menu.

## Editor Setup
You'll want to make sure that "Victory Plugin" is enabled. To do so, go to Edit > Preferences > Plugins and search the name

wip

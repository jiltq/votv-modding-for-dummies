# votv-modding-for-dummies

## Epic Games Launcher

## Unreal Engine Setup

## idk
```powershell
New-Item -Name VotV -ItemType directory | Set-Location
New-Item -Name VotV.uproject -ItemType file -Value '{"FileVersion":3,"EngineAssociation":"4.27"}'
Start-Process VotV.uproject
```

```powershell
New-Item -Name Config -ItemType directory | Set-Location
$DefaultGame = New-Item -Name DefaultGame.ini -ItemType file

Add-Content -Path $DefaultGame -Value '[/Script/UnrealEd.ProjectPackagingSettings]'
Add-Content -Path $DefaultGame -Value 'bGenerateChunks=True'
Add-Content -Path $DefaultGame -Value 'bShareMaterialShaderCode=False'
```
ndasdahsddnmasda

```powershell
# vvv change this if necessary vvv
$VictoryPlugin = 'X:\Some\Path' # change this


Expand-Archive -LiteralPath 'C:\Archives\Draft[v1].zip' -DestinationPath C:\Reference
```

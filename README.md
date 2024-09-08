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
ndasdahsddnmasda

```powershell
# vvv change this if necessary vvv
$VictoryPlugin = 'X:\Some\Path' # change this


Expand-Archive -LiteralPath 'C:\Archives\Draft[v1].zip' -DestinationPath C:\Reference
```

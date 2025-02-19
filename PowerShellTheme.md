# Instalation

## First step => Download and install Hack NF

Download and install Hack NF font from [nerd-fonts](https://github.com/ryanoasis/nerd-fonts/blob/master/patched-fonts/Hack/Regular/complete/Hack%20Regular%20Nerd%20Font%20Complete%20Mono%20Windows%20Compatible.ttf)

## Second step

This environment requires pre-release modules and to allow the instalation of pre-release modules in Powershell, you need to run the follow command:

```powershell
Install-Module PowerShellGet -Force
```

After, you need to close the terminal and open again as Administrator.

## Third step

```powershell
Set-ExecutionPolicy Unrestricted
Install-Module PSReadLine -Force -SkipPublisherCheck -AllowPrerelease
Install-Module posh-git -Force -SkipPublisherCheck -AllowPrerelease
Install-Module oh-my-posh -Force -SkipPublisherCheck -AllowPrerelease
Install-Module -Name Terminal-Icons -Repository PSGallery

Import-Module posh-git
Import-Module oh-my-posh
Import-Module -Name Terminal-Icons
Set-PoshPrompt slim

Set-PSReadlineKeyHandler -Key Tab -Function MenuComplete
Set-PSReadLineOption -PredictionSource History
Set-PSReadLineOption -PredictionViewStyle ListView
Set-PSReadLineOption -EditMode Windows

# this will override your current profile, so if you have something custom, do not execute it.
$sb = New-Object -TypeName System.Text.StringBuilder
$sb.AppendLine("Import-Module posh-git");
$sb.AppendLine("Import-Module oh-my-posh");
$sb.AppendLine("Import-Module -Name Terminal-Icons");
$sb.AppendLine("Set-PoshPrompt slim");
$sb.AppendLine("");
$sb.AppendLine("Set-PSReadlineKeyHandler -Key Tab -Function MenuComplete");
$sb.AppendLine("Set-PSReadLineOption -PredictionSource History");
$sb.AppendLine("Set-PSReadLineOption -PredictionViewStyle ListView");
$sb.AppendLine("Set-PSReadLineOption -EditMode Windows");

$sb.ToString() | Out-File -FilePath $profile
```

Then restart your powershell terminal

## Fourth step

Enable dotnet-suggestion

Follow the tutorial: https://github.com/dotnet/command-line-api/blob/main/docs/dotnet-suggest.md

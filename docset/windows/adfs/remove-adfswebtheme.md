---
ms.mktglfcycl: manage
ms.sitesec: library
ms.author: brianlic
author: brianlic-msft-msft
description: Use this topic to help manage Windows and Windows Server technologies with Windows PowerShell.
external help file: Microsoft.IdentityServer.Management.dll-Help.xml
keywords: powershell, cmdlet
manager: alanth
ms.date: 2016-12-20
ms.prod: w10
ms.technology: powershell-windows
ms.topic: reference
online version: 
schema: 2.0.0
title: Remove-AdfsWebTheme
ms.assetid: 4ABFCA5A-253A-44F6-87EE-C9C3CFDA772A
---

# Remove-AdfsWebTheme

## SYNOPSIS
Removes a web theme.

## SYNTAX

### IdentifierName
```
Remove-AdfsWebTheme [-TargetName] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### IdentifierObject
```
Remove-AdfsWebTheme [-TargetWebTheme] <AdfsWebTheme> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
The **Remove-AdfsWebTheme** cmdlet removes an **AdfsWebTheme** object.
Specify a web theme by name or by using the **Get-AdfsWebTheme** cmdlet.

## EXAMPLES

### Example 1: Remove a named web theme
```
PS C:\> Remove-AdfsWebTheme -TargetName "Theme01"
```

This command removes the web theme named Theme01.

### Example 2: Remove a web theme by specifying a web theme object
```
PS C:\> Get-AdfsWebTheme -Name "Theme02" | Remove-AdfsWebTheme
```

This command uses the **Get-AdfsWebTheme** cmdlet to get the web theme named Theme02, and then passes it to the current cmdlet by using the pipeline operator.
The cmdlet removes that web theme.

## PARAMETERS

### -Confirm
Prompts you for confirmation before running the cmdlet.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -TargetName
Specifies a name.
The cmdlet removes the theme that you specify by name.

```yaml
Type: String
Parameter Sets: IdentifierName
Aliases: 

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -TargetWebTheme
Specifies an **AdfsWebTheme** object.
The cmdlet removes the theme that you specify.
To obtain an **AdfsWebTheme** object, use the **Get-AdfsWebTheme** cmdlet.

```yaml
Type: AdfsWebTheme
Parameter Sets: IdentifierObject
Aliases: 

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -WhatIf
Shows what would happen if the cmdlet runs.
The cmdlet is not run.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

### System.String;Microsoft.IdentityServer.Management.Resources.AdfsWebTheme

## OUTPUTS

## NOTES

## RELATED LINKS

[Export-AdfsWebTheme](./Export-AdfsWebTheme.md)

[Get-AdfsWebTheme](./Get-AdfsWebTheme.md)

[New-AdfsWebTheme](./New-AdfsWebTheme.md)

[Set-AdfsWebTheme](./Set-AdfsWebTheme.md)

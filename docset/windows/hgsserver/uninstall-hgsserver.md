---
author: brianlic-msft
description: Use this topic to help manage Windows and Windows Server technologies with Windows PowerShell.
external help file: HgsServer-help.xml
keywords: powershell, cmdlet
manager: alanth
Module Name: HgsServer
ms.assetid: 956A5568-C1B4-4B19-9270-EB13C68BCD42
ms.author: brianlic
ms.date: 12/20/2016
ms.mktglfcycl: manage
ms.prod: w10
ms.sitesec: library
ms.technology: powershell-windows
ms.topic: reference
online version: 
schema: 2.0.0
title: Uninstall-HgsServer
---

# Uninstall-HgsServer

## SYNOPSIS
Removes a local node from a Host Guardian Service and from the domain.

## SYNTAX

```
Uninstall-HgsServer [-LocalAdministratorPassword] <SecureString> [-HgsDomainCredential <PSCredential>] [-Force]
 [-Restart] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
The **Uninstall-HgsServer** cmdlet removes a local node from a Host Guardian Service (HGS).

This cmdlet makes the following configuration changes in order to remove the HGS configuration from the additional HGS node: 

- Unregisters the Attestation Service web application with the IIS service. 
- Unregisters the Key Protection Service web application with the IIS service. 
- Disables Just Enough Administration on the local node. 
- Removes the local node from the existing failover cluster. 
- Removes the local node from being a domain controller.

This cmdlet makes the following configuration changes in order to remove the HGS configuration from the last HGS node: 

- Unregisters the Attestation Service web application with the IIS service. 
- Unregisters the Key Protection Service web application with the IIS service. 
- Removes the distributed network name (DNN) resource corresponding to the HGS name.
- Disables Just Enough Administration on the local node.
- Destroys the cluster on the local node. 
- Removes the local node from being a domain controller and removes the HGS domain.

For more information about the scenario terms, see [Security and Assurance](http://go.microsoft.com/fwlink/?LinkId=699209).

## EXAMPLES

### Example 1: Remove the node from HGS
```
PS C:\> $Cred = Get-Credential
PS C:\> Uninstall-HgsServer -HgsDomainCredential $cred -LocalAdministratorPassword $secureString
```

This example removes the node from an existing HGS setup.
If the second command removes the final node, then it also destroys the cluster.

## PARAMETERS

### -Force
Forces the command to run without asking for user confirmation.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -HgsDomainCredential
Specifies the Active Directory domain administrator credentials for the primary HGS server.

```yaml
Type: PSCredential
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LocalAdministratorPassword
Specifies the password for the local administrator account when the computer is no longer a domain controller.

```yaml
Type: SecureString
Parameter Sets: (All)
Aliases: 

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Restart
Indicates that a reboot is initiated automatically after running this command.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

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
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

## OUTPUTS

## NOTES

## RELATED LINKS

[HGS Server Cmdlets](./hgsserver.md)

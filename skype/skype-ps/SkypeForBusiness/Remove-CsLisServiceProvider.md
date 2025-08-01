---
applicable: Lync Server 2010, Lync Server 2013, Skype for Business Server 2015, Skype for Business Server 2019
author: hirenshah1
external help file: Microsoft.Rtc.Management.dll-help.xml
Locale: en-US
manager: rogupta
Module Name: SkypeForBusiness
ms.author: hirshah
online version: https://learn.microsoft.com/powershell/module/skype/remove-cslisserviceprovider
schema: 2.0.0
title: Remove-CsLisServiceProvider
---

# Remove-CsLisServiceProvider

## SYNOPSIS
Removes an object containing information about the web service provided by the Enhanced 9-1-1 (E9-1-1) Network Routing Provider to verify locations.
This cmdlet was introduced in Lync Server 2010.


## SYNTAX

```
Remove-CsLisServiceProvider [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
In an Enterprise Voice implementation with E9-1-1, emergency calls must first be routed through an E9-1-1 Network Routing Provider to ensure that the calls are routed to the appropriate Public Safety Answering Point (PSAP).
(A PSAP is the agency in the United States that directs the calls to the nearest emergency services, such as police, fire and ambulance services.) In order to do this, the provider must have a list of locations from the organization that it can then match against the Master Street Address Guide to ensure all locations are valid.
This cmdlet removes an entry for a provider; after running this cmdlet there will be no web service access to the provider.


## EXAMPLES

### Example 1
```
Remove-CsLisServiceProvider
```

This example removes the service provider web service from the E9-1-1 implementation.
There will only be, at most, one service provider defined, which will be removed by this cmdlet.


## PARAMETERS

### -Confirm

> Applicable: Lync Server 2010, Lync Server 2013, Skype for Business Server 2015, Skype for Business Server 2019

Prompts you for confirmation before executing the command.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

> Applicable: Lync Server 2010, Lync Server 2013, Skype for Business Server 2015, Skype for Business Server 2019

Describes what would happen if you executed the command without actually executing the command.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (https://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

### System.String
Accepts pipelined input of a Location Information Server (LIS) service provider object.

## OUTPUTS

### None
This cmdlet does not return an object or a value.

## NOTES

## RELATED LINKS

[Set-CsLisServiceProvider](Set-CsLisServiceProvider.md)

[Get-CsLisServiceProvider](Get-CsLisServiceProvider.md)

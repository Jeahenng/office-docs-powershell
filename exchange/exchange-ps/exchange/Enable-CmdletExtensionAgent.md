---
external help file: Microsoft.Exchange.ProvisioningAndMigration-Help.xml
online version: https://learn.microsoft.com/powershell/module/exchange/enable-cmdletextensionagent
applicable: Exchange Server 2010, Exchange Server 2013, Exchange Server 2016, Exchange Server 2019
title: Enable-CmdletExtensionAgent
schema: 2.0.0
author: chrisda
ms.author: chrisda
ms.reviewer:
---

# Enable-CmdletExtensionAgent

## SYNOPSIS
This cmdlet is available only in on-premises Exchange.

Use the Enable-CmdletExtensionAgent cmdlet to enable existing cmdlet extension agents.

For information about the parameter sets in the Syntax section below, see [Exchange cmdlet syntax](https://learn.microsoft.com/powershell/exchange/exchange-cmdlet-syntax).

## SYNTAX

```
Enable-CmdletExtensionAgent [-Identity] <CmdletExtensionAgentIdParameter>
 [-Confirm]
 [-DomainController <Fqdn>]
 [-WhatIf]
 [<CommonParameters>]
```

## DESCRIPTION
Cmdlet extension agents are used by Exchange cmdlets in Exchange Server 2010 and later. Cmdlets provided by other Microsoft or non-Microsoft products can't use cmdlet extension agents.

When you enable a cmdlet extension agent, the agent is run on every Exchange server in the organization. When an agent is enabled, it's made available to cmdlets that can then use the agent to perform additional operations.

Before you enable agents, be sure that you're aware of how the agent works and what impact the agent will have on your organization.

You need to be assigned permissions before you can run this cmdlet. Although this topic lists all parameters for the cmdlet, you may not have access to some parameters if they're not included in the permissions assigned to you. To find the permissions required to run any cmdlet or parameter in your organization, see [Find the permissions required to run any Exchange cmdlet](https://learn.microsoft.com/powershell/exchange/find-exchange-cmdlet-permissions).

## EXAMPLES

### Example 1
```powershell
Enable-CmdletExtensionAgent "Scripting Agent"
```

This example enables the cmdlet extension agent named Scripting Agent. Before you enable the Scripting Agent, you need to configure the %ExchangeInstallPath%Bin\\CmdletExtensionAgents\\ScriptingAgentConfig.xml.sample file and rename it to ScriptingAgentConfig.xml on all the Exchange servers in your organization. If you don't, all non-Get cmdlets will fail.

## PARAMETERS

### -Identity
The Identity parameter specifies the disabled cmdlet extension agent that you want to enable. You can use any value that uniquely identifies the agent. For example:

- Name
- Distinguished name (DN)
- GUID

```yaml
Type: CmdletExtensionAgentIdParameter
Parameter Sets: (All)
Aliases:
Applicable: Exchange Server 2010, Exchange Server 2013, Exchange Server 2016, Exchange Server 2019

Required: True
Position: 1
Default value: None
Accept pipeline input: True
Accept wildcard characters: False
```

### -Confirm
The Confirm switch specifies whether to show or hide the confirmation prompt. How this switch affects the cmdlet depends on if the cmdlet requires confirmation before proceeding.

- Destructive cmdlets (for example, Remove-\* cmdlets) have a built-in pause that forces you to acknowledge the command before proceeding. For these cmdlets, you can skip the confirmation prompt by using this exact syntax: `-Confirm:$false`.
- Most other cmdlets (for example, New-\* and Set-\* cmdlets) don't have a built-in pause. For these cmdlets, specifying the Confirm switch without a value introduces a pause that forces you acknowledge the command before proceeding.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: cf
Applicable: Exchange Server 2010, Exchange Server 2013, Exchange Server 2016, Exchange Server 2019

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DomainController
The DomainController parameter specifies the domain controller that's used by this cmdlet to read data from or write data to Active Directory. You identify the domain controller by its fully qualified domain name (FQDN). For example, dc01.contoso.com.

```yaml
Type: Fqdn
Parameter Sets: (All)
Aliases:
Applicable: Exchange Server 2010, Exchange Server 2013, Exchange Server 2016, Exchange Server 2019

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf
The WhatIf switch simulates the actions of the command. You can use this switch to view the changes that would occur without actually applying those changes. You don't need to specify a value with this switch.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: wi
Applicable: Exchange Server 2010, Exchange Server 2013, Exchange Server 2016, Exchange Server 2019

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/p/?LinkID=113216).

## INPUTS

### Input types
To see the input types that this cmdlet accepts, see [Cmdlet Input and Output Types](https://go.microsoft.com/fwlink/p/?LinkId=616387). If the Input Type field for a cmdlet is blank, the cmdlet doesn't accept input data.

## OUTPUTS

### Output types
To see the return types, which are also known as output types, that this cmdlet accepts, see [Cmdlet Input and Output Types](https://go.microsoft.com/fwlink/p/?LinkId=616387). If the Output Type field is blank, the cmdlet doesn't return data.

## NOTES

## RELATED LINKS

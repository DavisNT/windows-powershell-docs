---
description: Use this topic to help manage Windows and Windows Server technologies with Windows PowerShell.
external help file: Microsoft.ActiveDirectory.Management.dll-Help.xml
Module Name: ActiveDirectory
ms.date: 12/27/2016
online version: https://learn.microsoft.com/powershell/module/activedirectory/get-adauthenticationpolicysilo?view=windowsserver2022-ps&wt.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ADAuthenticationPolicySilo
---

# Get-ADAuthenticationPolicySilo

## SYNOPSIS
Gets one or more Active Directory Domain Services authentication policy silos.

## SYNTAX

### Filter (Default)
```
Get-ADAuthenticationPolicySilo [-AuthType <ADAuthType>] [-Credential <PSCredential>] -Filter <String>
 [-Properties <String[]>] [-ResultPageSize <Int32>] [-ResultSetSize <Int32>] [-Server <String>]
 [<CommonParameters>]
```

### Identity
```
Get-ADAuthenticationPolicySilo [-AuthType <ADAuthType>] [-Credential <PSCredential>]
 [-Identity] <ADAuthenticationPolicySilo> [-Properties <String[]>] [-Server <String>] [<CommonParameters>]
```

### LdapFilter
```
Get-ADAuthenticationPolicySilo [-AuthType <ADAuthType>] [-Credential <PSCredential>] -LDAPFilter <String>
 [-Properties <String[]>] [-ResultPageSize <Int32>] [-ResultSetSize <Int32>] [-Server <String>]
 [<CommonParameters>]
```

## DESCRIPTION
The **Get-ADAuthenticationPolicySilo** cmdlet gets an authentication policy silo or performs a search to get authentication policy silos.

The *Identity* parameter specifies the Active Directory Domain Services authentication policy silo to get.
You can identify an authentication policy silo by its distinguished name (DN), GUID or name.
You can also use the *Identity* parameter to specify a variable that contains an authentication policy silo object, or you can use the pipeline operator to pass an authentication policy silo object to the *Identity* parameter.

You can search for and use multiple authentication policies by specifying the *Filter* parameter or the *LDAPFilter* parameter.
The *Filter* parameter uses the Windows PowerShell® expression language to write query strings for Active Directory Domain Services.
Windows PowerShell expression language syntax provides rich type conversion support for value types received by the *Filter* parameter.
For more information about the *Filter* parameter syntax, type `Get-Help about_ActiveDirectory_Filter`.
If you have existing Lightweight Directory Access Protocol (LDAP) query strings, you can use the *LDAPFilter* parameter.

## EXAMPLES

### Example 1: Get an authentication policy silo object
```
PS C:\> Get-ADAuthenticationPolicySilo -Identity AuthenticationPolicySilo01
```

This command gets an authentication policy silo object named AuthenticationPolicySilo01.

### Example 2: Get all authentication policy silo objects that match a filter
```
PS C:\> Get-ADAuthenticationPolicySilo -Filter 'Name -like "*AuthenticationPolicySilo*"' | Format-Table Name, Enforce -AutoSize
Name  Enforce
----  -------
silo     True
silos   False
```

This command gets all the authentication policy silos that match the filter specified by the Filter parameter.
The output is then passed to the Format-Table cmdlet to display the name of the policy and the value for Enforce on each policy.

### Example 3: Get all properties of a specific authentication policy silo
```
PS C:\> Get-ADAuthenticationPolicySilo -Identity AuthenticationPolicySilo02 -Properties *
```

This command gets all properties for the authentication policy silo named AuthenticationPolicySilo02.

## PARAMETERS

### -AuthType
Specifies the authentication method to use.
The acceptable values for this parameter are:

- Negotiate or 0
- Basic or 1

The default authentication method is Negotiate.
A Secure Sockets Layer (SSL) connection is required for the Basic authentication method.

```yaml
Type: ADAuthType
Parameter Sets: (All)
Aliases: 
Accepted values: Negotiate, Basic

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential
Specifies a user account that has permission to perform the task.
The default is the current user.
Type a user name, such as User01 or Domain01\User01, or enter a **PSCredential** object, such as one generated by the **Get-Credential** cmdlet.

By default, the cmdlet uses the credentials of the currently logged on user unless the cmdlet is run from an Active Directory Domain Services Windows PowerShell provider drive.
If you run the cmdlet in a provider drive, the account associated with the drive is the default.

If you specify credentials that do not have permission to perform the task, the cmdlet returns an error.

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

### -Filter
Specifies a query string that retrieves Active Directory Domain Services objects.
This string uses the Windows PowerShell expression language syntax.
The Windows PowerShell expression language syntax provides rich type-conversion support for value types received by the *Filter* parameter.

Specify the *Filter* parameter in one of the following formats: 

- To match a single filter element: {Attributeoperator  "value"} 
- To match multiple filter elements: {(Attribute1operator1 "value1") joinOperator (Attribute2operator2 "value2")}

Windows PowerShell wildcards other than "*", such as "?" are not supported by the *Filter* syntax.

Valid filter operators are: 

 -eq, -le, -ge, -ne, -lt, -gt, -approx, -bor, -band, -recursivematch, -like, -notlike

Valid join operators are: 

-and, -or

The not operator is -not

For a list of supported types for values, type `Get-Help  about_ActiveDirectory_ObjectModel`.
For more information about the *Filter* parameter, type `Get-Help about_ActiveDirectory_Filter`.

```yaml
Type: String
Parameter Sets: Filter
Aliases: 

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Identity
Specifies an Active Directory Domain Services authentication policy silo object.
Specify the authentication policy silo object in one of the following formats: 

- A distinguished name
- A GUID
- A Name

This parameter can also get this object through the pipeline or you can set this parameter to an object instance.

The cmdlet searches the default naming context or partition to find the object.
If the cmdlet finds two or more objects, the cmdlet returns a non-terminating error.

```yaml
Type: ADAuthenticationPolicySilo
Parameter Sets: Identity
Aliases: 

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -LDAPFilter
Specifies an LDAP query string used to filter Active Directory Domain Services objects.
Use this parameter to run your existing LDAP queries.

```yaml
Type: String
Parameter Sets: LdapFilter
Aliases: 

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Properties
Specifies the properties of the output object to get from the server.
Use this parameter to get properties that are not included in the default set.

Specify the properties to get as a comma separated list of names.
For properties that are not default or extended properties, you must specify the LDAP display name of the property.
To display all of the properties that are set on the object, specify an asterisk wildcard.

To get properties for an object and display them, you can use this cmdlet and pass the output to the **Get-Member** cmdlet by using the pipeline operator.

```yaml
Type: String[]
Parameter Sets: (All)
Aliases: Property

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ResultPageSize
Specifies the number of objects to include in one page for an Active Directory Domain Services query.
The default value is 256 objects per page.

```yaml
Type: Int32
Parameter Sets: Filter, LdapFilter
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ResultSetSize
Specifies the maximum number of objects to return for an Active Directory Domain Services query.
If you want to get all of the objects, set this parameter to $Null.
You can use Ctrl+C to stop the query and the return of objects.

The default value is $Null.

```yaml
Type: Int32
Parameter Sets: Filter, LdapFilter
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Server
Specifies the Active Directory Domain Services instance to which to connect, by providing one of the following values for a corresponding domain name or directory server.
The service may be any of the following:  Active Directory Lightweight Domain Services, Active Directory Domain Services, or Active Directory snapshot instance.

Specify the Active Directory Domain Services instance in one of the following ways:  

Domain name values: 
- Fully qualified domain name
- NetBIOS name

Directory server values:  
- Fully qualified directory server name
- NetBIOS name
- Fully qualified directory server name and port

The default value for this parameter is determined by one of the following methods in the order that they are listed:

- By using the *Server* value from objects passed through the pipeline
- By using the server information associated with the Active Directory Domain Services Windows PowerShell provider drive, when the cmdlet runs in that drive
- By using the domain of the computer running Windows PowerShell

```yaml
Type: String
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

### None or Microsoft.ActiveDirectory.Management.ADAuthenticationPolicySilo
This cmdlet accepts an authentication policy silo object.

## OUTPUTS

### Microsoft.ActiveDirectory.Management.ADAuthenticationPolicySilo
Returns one or more authentication policy silo objects.
This cmdlet returns a default set of **ADAuthenticationPolicySilo** property values.
To retrieve additional **ADAuthenticationPolicySilo** properties, use the *Properties* parameter.

## NOTES

## RELATED LINKS

[New-ADAuthenticationPolicySilo](./New-ADAuthenticationPolicySilo.md)

[Remove-ADAuthenticationPolicySilo](./Remove-ADAuthenticationPolicySilo.md)

[Set-ADAuthenticationPolicySilo](./Set-ADAuthenticationPolicySilo.md)

[AD DS Administration Cmdlets in Windows PowerShell](./activedirectory.md)


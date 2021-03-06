---
title: "Secure SharePoint Online sites and files"
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 12/14/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection: 
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_Architecture
ms.assetid: 1d51bd87-17bf-457c-b698-61821de3afa0
description: "Summary: Configuration recommendations for protecting files in SharePoint Online and Office 365."
---

# Secure SharePoint Online sites and files

 **Summary:** Configuration recommendations for protecting files in SharePoint Online and Office 365.
  
This article provides recommendations for configuring SharePoint Online team sites and file protection that balances security with ease of collaboration. This article defines four different configurations, starting with a public site within your organization with the most open sharing policies. Each additional configuration represents a meaningful step up in protection, but the ability to access and collaborate on resources is reduced to the relevant set of users. Use these recommendations as a starting point and adjust the configurations to meet the needs of your organization. 
  
The configurations in this article align with Microsoft's recommendations for three tiers of protection for data, identities, and devices:
  
- Baseline protection
    
- Sensitive protection
    
- Highly confidential protection
    
For more information about these tiers and capabilities recommended for each tier, see the following resources. 
  
- [Identity and Device Protection for Office 365](https://docs.microsoft.com/office365/enterprise/microsoft-cloud-it-architecture-resources#BKMK_O365IDP)
    
- [File Protection Solutions in Office 365](https://docs.microsoft.com/office365/enterprise/microsoft-cloud-it-architecture-resources#BKMK_O365fileprotect)
    
## Capability overview

Recommendations for SharePoint Online team sites draw on a variety of Office 365 capabilities. For highly confidential sites, Azure Information Protection is recommended. This is included in Enterprise Mobility + Security (EMS). 
  
The following illustration shows the recommended configurations for four SharePoint Online team sites.

![Recommended configuration for SharePoint sites](Media/SharePoint-site-configuration-v2.png)

As illustrated:
  
- Baseline protection includes two options for SharePoint Online team sites — a public site and private site. Public sites can be discovered and accessed by anybody in the organization. Private sites can only be discovered and accessed by members of the site. Both of these site configurations allow for sharing outside the group. 
    
- Sites for sensitive and highly confidential protection are private sites with access limited only to members of specific groups.
    
- If needed for your scenario, you can use Azure Information Protection to encrypt and grants permissions to files that are highly confidential. This is not recommended for all customers.
    
## Tenant-wide settings for SharePoint Online and OneDrive for Business

SharePoint Online and OneDrive for Business include tenant-wide settings that affect all sites and users. Some of these settings can also be adjusted at the site level to be more restrictive (but not less). This section discusses tenant-wide settings that affect security and collaboration. 
  
### Sharing

For this solution, we recommend the following tenant-wide settings:
  
- Keep the default sharing policy that allows all sharing with all account types, including anonymous sharing.
    
- Set anonymous links to expire, if desired.
    
- Change the default link type for sharing to Internal. This helps prevent accidental data leakage outside your organization.
    
While it might seem counterintuitive to allow external sharing, this approach provides more control over file sharing compared to sending files in email. SharePoint Online and Outlook work together to provide secure collaboration on files. 
  
- By default, Outlook shares a link to a file instead of sending the file in email. 
    
- SharePoint Online and OneDrive for Business make it easy to share links to files with contributors who are both inside and outside your organization
    
You also have controls to help govern external sharing. For example, you can:
  
- Disable an anonymous guest link.
    
- Revoke user access to a site.
    
- See who has access to a specific site or document.
    
- Set anonymous sharing links to expire (tenant setting).
    
- Limit who can share outside your organization (tenant setting).
    
### Device access settings

Device access settings for SharePoint Online and OneDrive for Business let you determine whether access is limited to browser only (files can't be downloaded) or if access is blocked. These settings are currently in First Release and apply tenant-wide. Coming soon is the ability to configure device access policies at the site level. For this solution, we recommend not using device access settings that apply tenant-wide.
  
To use device access settings while these are in first release: [Set up the Standard or First Release Options in Office 365](https://support.office.com/article/Set-up-the-Standard-or-First-Release-options-in-Office-365-3B3ADFA4-1777-4FF0-B606-FB8732101F47).
  
### OneDrive for Business

Visit these settings to decide if you want to change the default settings for OneDrive for Business sites. Currently, the sharing and device access settings are duplicated from the SharePoint Online admin center and apply to both environments.
  
## SharePoint team site configuration

The following table summarizes the configuration for each of the team sites described earlier in this article. Use these configurations as starting point recommendations and adjust the site types and configurations to meet the needs of your organization. Not every organization needs every type of site. Only a small number of organizations require highly confidential protection.
  
||||||
|:-----|:-----|:-----|:-----|:-----|
||**Baseline protection #1** <br/> |**Baseline protection #2** <br/> |**Sensitive protection** <br/> |**Highly confidential** <br/> |
|Description  <br/> |Open discovery and collaboration within the organization.  <br/> |Private site and group with sharing allowed outside the group.  <br/> |Isolated site, in which levels of access are defined by membership in specific groups. Sharing is only allowed to members of the site.  <br/> |Isolated site + file encryption and permissions with Azure Information Protection.  <br/> |
|Private or public team site  <br/> |Public  <br/> |Private  <br/> |Private  <br/> |Private  <br/> |
|Who has access?  <br/> |Everybody in the organization, including B2B users and guest users.  <br/> |Members of the site only. Others can request access.  <br/> |Members of the site only. Others can request access.  <br/> |Members only. Others cannot request access.  <br/> |
|Site-level sharing controls  <br/> |Sharing allowed with anybody. Default settings.  <br/> |Sharing allowed with anybody. Default settings.  <br/> |Members cannot share access to the site.  <br/> Non-members can request access to the site, but these requests need to be addressed by a site administrator.  <br/> |Members cannot share access to the site.  <br/> Non-members cannot request access to the site or contents.  <br/> |
|Site-level device access controls  <br/> |No additional controls.  <br/> |No additional controls.  <br/> |Site-level controls are coming soon, which prevents users from downloading files to non-compliant or non-domain joined devices. This allows browser-only access from all other devices.  <br/> |Site-level controls are coming soon, which blocks downloading of files to non-compliant or non-domain joined devices.  <br/> |
|Azure Information Protection  <br/> ||||Use Azure Information Protection to automatically encrypt and grant permissions to files. This protection travels with the files in case they are leaked.  <br/> Office 365 cannot read files encrypted with Azure Information Protection.  <br/> |
   
For the steps to deploy the four different types of SharePoint Online team sites in this solution, see [Deploy SharePoint Online sites for three tiers of protection](deploy-sharepoint-online-sites-for-three-tiers-of-protection.md). 
  
## Azure Information Protection

If warranted for your security scenario, you can use Azure Information Protection to apply labels and protections that follow the files wherever they go. Azure Information Protection labels are different than Office 365 labels. For this solution, we recommend you use a scoped Azure Information Protection policy and a sub-label of the Highly Confidential label to encrypt and grant permissions to files that need to be protected with the highest level of security. 
  
Be aware that when Azure Information Protection encryption is applied to files stored in Office 365, the service cannot process the contents of these files. Co-authoring, eDiscovery, search, Delve, and other collaborative features do not work. 
  
![Azure Information Protection is configured in Azure and labels show up in the client toolbar](media/1266a7a0-5078-49ab-bbf1-b0cf41451f62.png)
  
As illustrated:
  
- You configure Azure Information Protection policies and labels in the Microsoft Azure portal. Configuring a sub-label of a scoped Azure Information Protection policy is recommended.
    
- Azure Information Protection labels show up as an **Information protection** bar in Office applications.
    
### Adding permissions for external users

There are two ways you can grant external users access to files protected with Azure Information Protection. In both these cases, external users must have an Azure AD account. If external users aren't members of an organization that uses Azure AD, they can obtain an Azure AD account as an individual by using this sign-up page: [https://aka.ms/aip-signup](https://aka.ms/aip-signup).
  
- Add external users to an Azure AD group that is used to configure protection for a label
    
     You'll need to first add the account as a B2B user in your directory. It can take a couple of hours for [group membership caching by Azure Rights Management](https://docs.microsoft.com/information-protection/plan-design/prepare#group-membership-caching-by-azure-rights-management). With this method, permissions are granted to all existing files protected with the label (even files protected before a user is added to the Azure AD group).
    
- Add external users directly to the label protection
    
     You can add all users from an organization (e.g. Fabrikam.com), an Azure AD group (such as a finance group within an organization), or an individual user. For example, you can add an external team of regulators to the protection for a label. With this method, permissions are granted only to files protected with the label after the external entity is added to the protection.
    
### Deploying and using Azure Information Protection

For the steps to configure Azure Information Protection in this solution, see [Protect SharePoint Online files with Azure Information Protection](protect-sharepoint-online-files-with-azure-information-protection.md).
  
## See Also

[Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[Cloud adoption and hybrid solutions](https://docs.microsoft.com/office365/enterprise/cloud-adoption-and-hybrid-solutions)




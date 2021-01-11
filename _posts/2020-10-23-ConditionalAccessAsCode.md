---
layout: post
tags: [azure,iac,conditionalaccess]
title: Conditional Access (As Code)
excerpt_separator: <!--more-->
---

I have long been an advocate of Conditional Access used in conjunction with Azure Active Directory. It is a fantastic tool in your armoury for securing user access to Office 365 and other services powered by Azure AD.

Earlier this year Microsoft extended the API capabilities which allow us to interact with the Conditional Access service as admins. Now rather than reinventing the wheel here, I just want to quickly share some great examples of this capability "Condtional Access (as code)" which I think can really help!

<a href="https://github.com/Azure-Samples/azure-ad-conditional-access-apis/tree/main/05-manage/01-backup-restore" target="_blank">Backup and restore Conditional Access policies with approval workflows</a> 

<a href="https://github.com/Azure-Samples/azure-ad-conditional-access-apis/blob/main/04-monitor/readme.md" target="_blank">Alert on Conditional Access Policy changes</a>

<a href="https://github.com/Azure-Samples/azure-ad-conditional-access-apis/blob/main/02-test/readme.md" target="_blank">Safe rollout of policies from pre-production to production with approval workflow</a>




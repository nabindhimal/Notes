
## What is Active Directory?

Active Directory (AD) is a directory service for Windows network environments used by an estimated 95% of all Fortune 500 companies. Its structure facilitates centralized management of an organization's resources which may include users, computers, groups, network devices, file shares, group policies, devices, and trusts.

At the highest level, AD provides authentication and authorization functions within a Windows domain environment. While it has been a target of hackers since its inception, attacks and research continue to evolve.

_Recommended read: [Active directory pentesting](https://www.hackthebox.com/blog/active-directory-penetration-testing-cheatsheet-and-guide) and cheatsheet_

## Why is Active Directory important for cybersecurity?

AD remains a key area of interest for offensive and defensive security practitioners because when an Active Directory environment is compromised, this typically results in almost complete control over the network. An initial installation of AD is arguably "not secure by default," and it can be easily misconfigured. 

Weaknesses in AD, including common and obscure misconfigurations, recent vulnerabilities, and built-in functionality that attackers can abuse, can be leveraged to move laterally and vertically within a network environment and gain unauthorized access and persistence. AD is essentially a large database where many components can be queried by any authenticated user in the domain, regardless of their privilege level.

💡Note: If you're interested in learning how to defend active directory, check out our guide on [Active Directory hardening](https://www.hackthebox.com/blog/active-directory-hardening-pentester-vs-soc), in which a SOC analyst defends AD from our Head of Security's attempts to perform a Golden Ticket attack.


## Short History of Active Directory

Active Directory has been around for a couple of decades, and Microsoft's commitment to backward compatibility is commendable, but, as a result, some configurations are insecure by default. A basic AD user account with no added privileges can enumerate most information within the domain (including misconfigurations and flaws that could lead to unintended access) and even perform many different attacks. Due to this, organizations must focus on defense-in-depth and strategic planning, emphasizing security, AD hardening, hygiene, network segmentation, and limiting rights and privileges wherever possible.

While certain insecure practices have been eliminated as AD has evolved over the years (like allowing anonymous access to query any information in the domain without an authenticated user account and allowing admins to store passwords in Group Policy Preferences files), some "legacy" misconfigurations can still be seen in modern AD environments due to how AD upgrades can be performed. Domain Users being able to read this information isn't a vulnerability in itself, but since all users do have read access, if the domain is not properly hardened, any user, regardless of privilege level, can relatively easily sniff out misconfigurations with tools like BloodHound

Active Directory, by design, makes information easy to find and use for administrators and users alike. AD is highly scalable, supports millions of objects per domain, and allows the creation of additional domains as an organization grows, making it often the go-to choice for everything from small to mid-sized and large enterprises.




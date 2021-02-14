# Powershell CloudFlare Access Rule
This is a powershell script to simply create/delete an Access Rule for Cloudflare API v4 (so to BAN(BLOCK) or UNBAN(UNBLOCK) an IP).

# Introduction
The script is based on original bash script that can be located [here](https://gist.github.com/pjv/926ece8549cd45bac4821945f6ad253c).
I converted it for powershell and putted everything in one script for ban and unban.

For different kind of Cloudflare API perimission and target I create two script:

`Script_CloudFlare_API_Global_Access_Rule.ps1`
it creates/delete rules for a given IP address accross all of your domains in CloudFlare  
You need a Cloudflare Global API key

`Script_CloudFlare_API_Zone_Access_Rule.ps1` 
it creates/delete rules for a given IP address only for the domain contoso.com  
You need a Cloudflare a Zone ID of your domain and a Zone API key (Mininum Edit Permissions needed: Zone.Firewall Services)

# Parameter to set inside
Parameter to set inside both the script:  
`$USER` is the Cloudflare account email  
`$TOKEN` is the Cloudflare API token. It can be Global API token or API token only for zone

Parameter to set inside needed only for script `Script_CloudFlare_API_Zone_Access_Rule.ps1`:  
`$ZONEID` is Zone ID, that you can find in the Cloudflare Dashboard of the domain

# Parameter to pass on execution
To ban an IP:  
`c:>.\Script_CloudFlare_API_Global_Access_Rule BLOCK IPADDRESS`   
Before to call a ban it check if already exist an Access Rule with that IP, if not it ban the passed IP (aka create anAccess Rule)

To unban an IP:  
`c:>.\Script_CloudFlare_API_Global_Access_Rule UNBLOCK IPADDRESS`  
Before to call an unban it check if exist an Access Rule with that IP, if yes it unban passed IP (aka delete an Access Rule)

# Some Tips
- Example of ways to run the script:  
`.\Script_CloudFlare_API_Zone_Access_Rule.ps1 BLOCK IpToBan`  
`PathToScript\Script_CloudFlare_API_Zone_Access_Rule.ps1 BLOCK IpToBan`  
or  
`C:\Windows\system32\WindowsPowerShell\v1.0\powershell.exe -file PathToScript\Script_CloudFlare_API_Zone_Access_Rule.ps1 BLOCK IpToBan`

- Obviusly before to start you need to set the execution policies to Unrestricted.  
To do that you must start as Administrator Powershell and execute `Set-ExecutionPolicy Unrestricted` and digit `Y`  
To set it to windows defaul you must execut `Set-ExecutionPolicy Restricted` and digit `Y`  
[Set-ExecutionPolicy Command](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/set-executionpolicy?view=powershell-7.1)

# Helpfull link and credit
[Cloudflare API v4 guide](https://api.cloudflare.com/#user-level-firewall-access-rule-properties) 
[Cloudflare Creating API tokens](https://developers.cloudflare.com/api/tokens/create)
[Power Shell Get Date Time on Same line](https://stackoverflow.com/questions/20246889/get-date-and-time-on-the-same-line)
[Cloudflare Powershell invoke webrequest info exemple](https://community.cloudflare.com/t/invoke-webrequest-cloudflare-api-error-400/1842/2)
Thanks to:  
[GithubGist pjv/cf_ban scripts](https://gist.github.com/pjv/926ece8549cd45bac4821945f6ad253c)  
[Github poshsecurity/PowerShell-CloudFlare-Tor-Whitelist repository](https://github.com/poshsecurity/PowerShell-CloudFlare-Tor-Whitelist)  
[Github zloeber/PSCloudflare repository](https://github.com/zloeber/PSCloudflare)  

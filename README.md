# Powershell CloudFlare Access Rule
This is a powershell script to simply create a Access Rule for Cloudflare API v4 to BAN or UNBAN an IP.

# Introduction
The script is based on original bash script that can be located [here](https://gist.github.com/pjv/926ece8549cd45bac4821945f6ad253c)

I converted it for powershell and putted everything in one script.
I create two script:

`Script_CloudFlare_API_Global_Access_Rule.ps1`
it creates/delete rules for a given IP address accross all of your domains in CloudFlare
You need a Cloudflare Global API key

`Script_CloudFlare_API_Zone_Access_Rule.ps1` 
it creates/delete rules for a given IP address only for the domain contoso.com
You need a Cloudflare Zone API key

# Parameter to set inside
Paremeter to set inside both the script

`$USER` is the Cloudflare account email

`$TOKEN` is the Cloudflare API token. It can be Global API token or API token only for zone (Mininum Edit Permissions needed: Zone.Firewall Services)

Paremeter to set inside needed only for script `Script_CloudFlare_API_Zone_Access_Rule.ps1`

`$ZONEID` is Zone ID, that you can find in the Cloudflare Dashboard of the domain

# Parameter to pass on execution
To ban an IP

`c:>.\Script_CloudFlare_API_Global_Access_Rule BAN IPADDRESS`
Before to call a ban it check if already exist an Access Rule with that IP, if not it ban the passed IP (aka Create Access Rule)

To unban an IP

`c:>.\Script_CloudFlare_API_Global_Access_Rule UNBAN IPADDRESS`
Before to call an unban it check if exist an Access Rule with that IP, if yes it unban passed IP (aka Delete Access Rule)

- [Setting Up pfSense as a Home Router/Firewall](#setting-up-pfsense-as-a-home-routerfirewall)
  - [Initial Setup](#initial-setup)
  - [Basic Firewall Setup](#basic-firewall-setup)
  - [DNS Blocking](#dns-blocking)
- [Backup Settings](#backup-settings)
- [Extras](#extras)

# Setting Up pfSense as a Home Router/Firewall
Assumes you are using a Netgate SG-1100

## Initial Setup
- Plug in power and cable between PC and LAN interface
- Wait ~5min
- Navigate to 192.168.1.1
- Log in with admin:pfsense
- Run through the setup wizard with all defaults
- Primary DNS server suggestion - [OpenDNS](https://support.opendns.com/hc/en-us/articles/228006047-Generalized-Router-Configuration-Instructions)

## Basic Firewall Setup
The pfSense firewall blocks WAN traffic by default - any traffic that doesn't match any rules is dropped silently.

### Default-deny Outbound
This is basically hard-mode. You will have to create Pass rules above this rule to get anything working. We'll put in Pass rules for basic internet over TCP 80/443

- Navigate to Firewall > Rules > LAN
- Add these rules
  - Pass tcp any 443
  - Pass tcp any 80
  - Pass any LAN net LAN net
  - Block IPv4+IPv6 protocol:any LAN Net any (enable logging)
- Click Apply Changes
- Review any blocks via Status > System Logs > Firewall


## DNS Blocking

### Firewall DNS Setup
- Navigate to Firewall > Rules > LAN
- Traffic is parsed through firewall rules top-to-bottom. We will make two rules here. One to allow DNS to the pfSense system, and one UNDER it to block all DNS.
- Add a rule:
  - Action: Pass
  - Protocol: UDP
  - Source: Any
  - Destination LAN Net / DNS (53)
  - Description: Allow DNS to pfSense
- Add another rule:
  - Action: Block
  - Protocol: UDP
  - Source: Any
  - Destination Any / DNS (53)
  - Description: Block DNS traffic

### pfBlocker
- Navigate to System > Package Manager > Available Packages
- Search for pfBlockerNG and install the non-development package
- Firewall > pfBlockerNG
- Check Enable pfBlockerNG and click Save at the bottom
- Firewall > pfBlockerNG > DNSBL
- Check Enable DNSBL and click Save at the bottom

#### DNSBL EasyList
- Navigate to Firewall > pfBlockerNG > DNSBL EasyList
- In DNS GROUP Name type "EasyList"
- In EasyList Feeds, click Add and set up the two lists
  - ON | Easylist w/o Elements | EasyList
  - ON | EasyPrivacy | EasyPrivacy
- Select all entries in Categories
- Change List Action to Unbound
- Change Update Frequency to Once a day

#### DNSBL Feeds
- Navigate to Firewall > pfBlockerNG > DNSBL Feeds
- Set DNS GROUP Name to StevenBlack List
- Set Description to https://github.com/StevenBlack/hosts
- Click Add and set up the two lists
    - Auto | ON | https://raw.githubusercontent.com/StevenBlack/hosts/master/alternates/fakenews-gambling-porn-social/hosts | porn
    - Auto | ON | https://raw.githubusercontent.com/StevenBlack/hosts/master/hosts | adware_malware
- Set List Action to Unbound
- Set Update Frequency to Once a day
- Click Save

#### Update the DNSBL Lists
- Navigate to Firewall > pfBlockerNG > Update
- Click Run

#### DNSBL Whitelisting
- Navigate to Firewall > pfBlockerNG > DNSBL
- Scroll to the bottom and expand Custom Domain Whitelist
- Add entries - one per line
- Navigate to Firewall > pfBlockerNG > Update
- Select 'Force' option Reload
- Click Run

#### Troubleshooting & Log Review
- Navigate to Firewall > pfBlockerNG > Logs
- Select Log/File selection > dnsbl.log
- Review Rejects in the log file

# Backup Settings
- Navigate to Diagnostics > Back and Restore
- Click Download Configuration as XML


# Extras
- Use your DD-WRT router as a switch
  - https://wiki.dd-wrt.com/wiki/index.php/Switch



